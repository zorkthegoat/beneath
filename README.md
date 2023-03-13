{% for product in collections.frontpage.products limit:3 %}
  <div class="product">
    <a href="{{ product.url }}" title="{{ product.title }}">
      <img src="{{ product.featured_image.src | img_url: 'large' }}" alt="{{ product.title }}" class="product__image">
      <h2 class="product__title">{{ product.title }}</h2>
    </a>
    <p class="product__price">{{ product.price | money }}</p>
    <form action="/cart/add" method="post" enctype="multipart/form-data">
      <input type="hidden" name="id" value="{{ product.variants.first.id }}">
      <button type="submit" class="btn btn--primary product__add-to-cart">{{ 'Add to cart' | t }}</button>
    </form>
  </div>
{% endfor %}
