---
title: "turning off redshift?"
date: 2010-06-15
forum: General Help
---

### Post by princeofnam on 2010-06-15
everytime i try to kill the process it just turns back on? i'm a tad confused. does anyone else run into the same issue?

---

### Post by stinkeye on 2010-06-15
Hit alt + F2 and run **gtk-redshift**
This will give you an icon in the Notification Area
to toggle redshift off and on.

---

### Post by princeofnam on 2010-06-15
thanks, although when i tried to do that i just got 

--
x@x:~$ gtk-redshift
No city selected as current city.
Initialization of gnome-clock failed.
Trying other provider...
Latitude and longitude must be set.


--

Odd considering that i already set my lat:log using redshift -l xx:xx

---

### Post by stinkeye on 2010-06-15
Right click on the date/time in the gnome panel -> preferences -> locations -> add ... then start typing area near you e.g. london and redshift will use this as your location.

or 

First find the longitude and latitude for your country/city @ [**_[COLOR="DarkRed"]http://www.getlatlon.com/[/COLOR]_**]("http://www.getlatlon.com/")
Next open up a terminal and enter the following command using the location found above as lat:lon like so: -
redshift -l 55.7:12.6 
So for Malmö, Sweden you would enter: -
redshift -l 55.6:13.0

---

### Post by bark50 on 2010-06-19
> **stinkeye said:**
> Right click on the date/time in the gnome panel -> preferences -> locations -> add ... then start typing area near you e.g. london and redshift will use this as your location.

or 

First find the longitude and latitude for your country/city @ [**_[COLOR="DarkRed"]http://www.getlatlon.com/[/COLOR]_**]("http://www.getlatlon.com/")
Next open up a terminal and enter the following command using the location found above as lat:lon like so: -
redshift -l 55.7:12.6 
So for Malmö, Sweden you would enter: -
redshift -l 55.6:13.0

Thanks, stinkeye.  Not only did that right-click process get redeye going for me, but as an added bonus, now my weather applet is working!  :guitar:

---

