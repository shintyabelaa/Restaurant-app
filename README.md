# Restaurant-app

//How to fetch api from DATA.JSON


import 'regenerator-runtime'; /* for async await transpile */<br>
import '../styles/style.css';<br>
import '../styles/responsive.css';<br>
import App from './views/app';<br><br>

fetch('DATA.json')<br>
   .then((response) => {<br>
    console.log('Response:', response);<br>
    return response.json();<br>
  })<br>
  // response.json())<br>
  .then((data) => {<br>
    console.log('Data:', data);<br>
    const restaurantsList = document.getElementById('restaurants-list');<br>

    data.restaurants.forEach((restaurant) => {
      const restaurantItem = document.createElement('div');
      restaurantItem.classList.add('restaurant-item');

      const restaurantPlace = document.createElement('h1');
      restaurantPlace.innerText = restaurant.city;
      restaurantItem.appendChild(restaurantPlace);

      const restaurantImage = document.createElement('img');
      restaurantImage.setAttribute('src', restaurant.pictureId);
      restaurantImage.setAttribute('alt', restaurant.name);
      restaurantItem.appendChild(restaurantImage);

      const restaurantRatings = document.createElement('h2');
      restaurantRatings.innerText = `Rating: ${restaurant.rating}`;
      restaurantItem.appendChild(restaurantRatings);

      const restaurantName = document.createElement('h3');
      restaurantName.innerText = restaurant.name;
      restaurantItem.appendChild(restaurantName);

      const restaurantDescription = document.createElement('p');
      restaurantDescription.innerText = restaurant.description;
      restaurantItem.appendChild(restaurantDescription);

      restaurantsList.appendChild(restaurantItem);
    });
  })
  .catch((error) => console.error(error));

