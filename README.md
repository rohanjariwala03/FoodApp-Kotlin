# FoodApp-Kotlin

A small food ordering app for Android, written in Kotlin while I was learning the platform. There is no backend. The restaurants and menus come from a JSON file bundled in the app, and placing an order just shows a confirmation screen.

## What it does

- Lists four sample restaurants (name, address, logo and today's opening hours) loaded from `app/src/main/res/raw/restaurent.json`.
- Shows a restaurant's menu in a two-column grid. You can add items to the cart and change the quantity (up to 10 per item).
- The order screen lists the cart items with a subtotal. A delivery switch shows the address fields and adds the restaurant's delivery charge to the total.
- Validates that the name, card number, expiry and CVV fields are filled in (plus address, city and zip when delivery is on), then shows an order confirmation screen. No payment is processed.

## Stack

- Kotlin 1.6.0, Android Gradle Plugin 7.0.3, Gradle 7.0.2
- compileSdk / targetSdk 32, minSdk 21
- RecyclerView, Material Components
- Gson to parse the bundled JSON
- Glide to load food and restaurant images from their URLs
- Kotlin Android Extensions (synthetic view binding), which has since been deprecated

## Getting started

Open the project in Android Studio and let Gradle sync, or build from the command line:

```
./gradlew assembleDebug
```

Use a JDK that matches AGP 7.0 (JDK 11).

## Status

This was left unfinished. As committed, the Kotlin sources declare the package `com.demo.foodorderanddeliveryappkotlin` while the manifest and resources use `com.example.foodappkotlin`. Some files import `R` from the wrong package, and only `MainActivity` is registered in `AndroidManifest.xml`. The manifest also has no `INTERNET` permission, so Glide can't load the remote images. These need fixing before the app will build and run.

## Project structure

```
app/src/main/java/com/example/foodappkotlin/
  SplashActivity.kt           2 second splash screen
  MainActivity.kt             restaurant list
  RestaurantMenuActivity.kt   menu grid and cart
  PlaceYourOrderActivity.kt   order form and totals
  SuccessOrderActivity.kt     confirmation screen
  adapter/                    RecyclerView adapters
  models/RestaurantModel.kt   Parcelable data classes
app/src/main/res/raw/restaurent.json   sample data
```
