# find location by phone number

#1
import phonenumbers
import folium
from phonenumbers import geocoder
from opencage.geocoder import OpenCageGeocode
from number import number
#2
yulNumber=phonenumbers.parse(number)
yourLocation=geocoder.description_for_number(yulNumber, "en")

#3
key='6aea1c32fb7e44a6a334157b973e1aac'
geocoder=OpenCageGeocode(key)
query=str(yourLocation)
results=geocoder.geocode(query)
lat=results[0]['geometry']['lat']
lng=results[0]['geometry']['lng']

#4
myMap=folium.Map(location=[lat,lng], zoom_start=9)
folium.Marker([lat,lng], popup=yourLocation).add_to ((myMap))
myMap.save("newlocation.html")
