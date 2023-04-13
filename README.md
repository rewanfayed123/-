<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8">
    <title>تقييم المنتج</title>
    <style>
      /* ستايل لعلامات التصويت */
      .stars {
        display: inline-block;
        width: 20px;
        height: 20px;
        background-image: url("star.png"); /* تغيير الصورة إلى الصورة التي تريدها */
        background-size: contain;
        cursor: pointer;
      }

      /* ستايل للعلامات النجمية المحددة */
      .stars.active {
        background-image: url("star_active.png"); /* تغيير الصورة إلى الصورة التي تريدها */
      }

      /* ستايل لمربع النص لإظهار التقييم */
      .result {
        display: inline-block;
        margin-left: 10px;
        font-size: 20px;
        font-weight: bold;
      }
    </style>
  </head>
  <body>
    <h1>تقييم المنتج</h1>
    <p>قيّم هذا المنتج:</p>
    <div id="stars">
      <span class="stars" data-rating="1"></span>
      <span class="stars" data-rating="2"></span>
      <span class="stars" data-rating="3"></span>
      <span class="stars" data-rating="4"></span>
      <span class="stars" data-rating="5"></span>
      <div class="result"></div>
    </div>
    <script>
      const stars = document.querySelectorAll(".stars");
      const result = document.querySelector(".result");
      let rating = 0;

      for (let i = 0; i < stars.length; i++) {
        stars[i].addEventListener("click", function() {
          rating = this.dataset.rating;
          result.innerText = `(${rating} من 5)`;
          setRating();
        });

        stars[i].addEventListener("mouseover", function() {
          resetStars();
          setRating(this.dataset.rating);
        });

        stars[i].addEventListener("mouseout", function() {
          resetStars();
          if (rating !== 0) {
            setRating();
          }
        });
      }

      function setRating(active = null) {
        for (let i = 0; i < stars.length; i++) {
          if (i < active) {
            stars[i].classList.add("active");
          } else {
            stars[i].classList.remove("active");
          }
        }
      }

      function resetStars() {
        for (let i = 0; i < stars.length; i++) {
          stars[i].classList.remove("active");
        }
      }
    </script>
  </body>
</html>
