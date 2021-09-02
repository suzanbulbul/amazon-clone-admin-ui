<template>
  <main>
    <div class="container-fluid">
      <div class="row">
        <div class="col-sm-3"></div>
        <div class="col-sm-6">
          <div class="a-section">
            <div class="a-spacing-top-medium">
              <h2 style="text-align: center">Add a new product</h2>
              <form>
                <!-- Categry Dropdown -->
                <div class="a-spacing-top-medium">
                  <label>Category</label>
                  <select class="a-select-option">
                    <option
                      v-for="category in categories"
                      :value="category._id"
                      :key="category._id"
                    >
                      {{ category.type }}
                    </option>
                  </select>
                </div>
                <!-- Owner Dropdown -->
                <div class="a-spacing-top-medium">
                  <label>Owner</label>
                  <select class="a-select-option">
                    <option
                      v-for="owner in owners"
                      :value="owner._id"
                      :key="owner._id"
                    >
                      {{ owner.name }}
                    </option>
                  </select>
                </div>
                <!-- Title İnput -->
                <div class="a-spacing-top-medium">
                  <label style="margin-bottom: 0px">Title</label>
                  <input type="text" class="a-input-text" style="width: 100%" />
                </div>
                <!-- Price İnput -->
                <div class="a-spacing-top-medium">
                  <label style="margin-bottom: 0px">Price</label>
                  <input
                    type="number"
                    class="a-input-text"
                    style="width: 100%"
                  />
                </div>
                <!-- Description Textarea -->
                <div class="a-spacing-top-medium">
                  <label style="margin-bottom: 0px">Description</label>
                  <textarea
                    style="width: 100%"
                    placeholder="Provide details such a product description"
                  ></textarea>
                </div>
                <!-- Photo File -->
                <div class="a-spacing-top-medium">
                  <label style="margin-bottom: 0px">Add Photo</label>
                  <div class="a-row a-spacing-top-medium">
                    <label class="choosefile-button">
                      <i class="fal fa-plus"></i>
                      <input type="file" />
                      <p style="margin-top: -70px">name of the</p>
                    </label>
                  </div>
                </div>
                <hr />
                <!-- Button-->

                <div class="a-spacing-top-large">
                  <span class="a-button-register">
                    <span class="a-button-inner">
                      <span class="a-button-text">Add product</span>
                    </span>
                  </span>
                </div>
              </form>
            </div>
          </div>
        </div>
        <div class="col-sm-3"></div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  async asyncData({ $axios }) {
    try {
      let categories = $axios.$get("http://localhost:3000/api/categories");
      let owners = $axios.$get("http://localhost:3000/api/owners");

      const [catResponse, ownerResponse] = await Promise.all([categories, owners]);

      console.log("deneme", catResponse);

      return {
        categories: catResponse.categories,
        owners: ownerResponse.owners,
      };
    } catch (err) {
      console.log(err);
    }
  },
};
</script>

<style>
</style>