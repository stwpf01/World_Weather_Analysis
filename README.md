# World_Weather_Analysis

## Overview of Project

The purpose of this project was to expand upon the intitial PlanMyTrip app by adding a weather description to the weather data portion as well as selecting four cities to create a travel tour with a route between all of the cities. The code for this can be found in the [Weather_Database](https://github.com/stwpf01/World_Weather_Analysis/blob/main/Weather_Database/Weather_Database.ipynb) file, the [Vacation_Search](https://github.com/stwpf01/World_Weather_Analysis/blob/main/Vacation_Search/Vacation_Search.ipynb) file, and the [Vacation_Itinerary](https://github.com/stwpf01/World_Weather_Analysis/blob/main/Vacation_Itinerary/Vacation_Itinerary.ipynb) file. The results of these deliverables will be detailed below.

## Results

### Weather Database

The majority of this deliverable was refactored code with the exception of adding the weather description to the weather data. This was somewhat more tricky because the `[description]` dictionary was nested inside an array of the `[weather]` dictionary. So in order to retrieve the information, the array needed to be added to the line of code. Since it was the first and only array, `[0]` was the only extra bit of code that needed to be added. This is what it looks like compared to another line of code to retrieve the `[country]` dictionary:

`city_country = city_weather["sys"]["country"]`
`city_descr = city_weather["weather"][0]["description"]`

The weather description data was stored in the `Current Weather` column because `Weather Description` seemed rather cumbersome comparatively. This change was carried over to the next two deliverables. Further down in another cell `Max Temp` was renamed `Max Temp ($^\circ$F)` so that the column name would appear as `Max Temp (°F)` to clarify the temperature. This change, too, was carried over to the next two deliverables.

### Vacation Search

This deliverable was to allow customers to input a range in temperature to find a vacation spot within that range. A name of a hotel within that vacation spot would also appear in the search results. An example image showing the results on a map is below:

![WeatherPy_vacation_map](https://github.com/stwpf01/World_Weather_Analysis/blob/main/Vacation_Search/WeatherPy_vacation_map.png)


To ensure each result had a hotel within the specified limit from the latitude and the longitude of the cities, rows without anything in the `Hotel Name` column were removed. This was done by using this line of code:

`clean_hotel_df = hotel_df.loc[hotel_df["Hotel Name"] != ""]`

This created a new variable (`clean_hotel_df`) to equal the dataframe `hotel_df` and locate (`.loc`) the `Hotel Name` columns within the same dataframe where it did not equal (`!=`) a null variable (`""`). That way it would only retrieve rows that had a variable within the `Hotel Name` column. 

### Vacation Itinerary

This deliverable was to creat a route between four nearby cities to the main vacation spot. An example of how this would display is as follows:

![WeatherPy_travel_map](https://github.com/stwpf01/World_Weather_Analysis/blob/main/Vacation_Itinerary/WeatherPy_travel_map.png)


There is an option to decide how to travel between these four cities in the code:

`vacation_itinerary = gmaps.directions_layer(start, end, waypoints = [stop1, stop2, stop3], travel_mode="DRIVING")`

But when choosing another variable like `"BICYCLING"` for `travel_mode` the code would error, presumably because attemping to bicycle to and from these cities would be immensely impractical.

## Summary

With only minor adjustments each customer could fairly easily plan a pleasant vacation touring nearby cities. Having them choose a city based upon the range of temperature at time of input, however, does not seem like a viable option as weather can be fickle. Perhaps if it was designed around the cities upcoming week forecast it would provide a better snapshot of what to expect on the customers vacation.


