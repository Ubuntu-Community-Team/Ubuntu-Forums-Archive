---
title: "Weather Report 2.30.0 stuck"
date: 2010-12-19
forum: General Help
---

### Post by cosmolee on 2010-12-19
Ubuntu 10.04, Weather Report 2.30.0 (gnome-applet)

I'm using the gnome-applet for weather reports.  In the Details section, it updates the "Current Conditions" tab with current conditions properly, but in the "Forecast" tab, my report for New York City has been stuck on the same forecast for weeks now.  It never changes.  

I've tried clicking the "update" button, but the same forecast just gets refreshed.  I've also tried changing the city, then cycling back to NYC, but the same forecast persists.  I've also tried changing sub-locations for NYC, but I still get the same forecast.

I have another instance of the applet running for another city, and it updates the forecast properly.  The problem only exists for New York City.

Ideas?

---

### Post by mgcleveland on 2010-12-19
I have this same issue on both of my Ubuntu machines.  They are both running 10.04 with weather applet 2.30.0.

Each machine has been reporting a stale forecast for months now.  I've tried updating and changing locations to no avail.

---

### Post by cosmolee on 2010-12-21
It appears to me that the problem may not have to do with the weather applet, but the source of the forecast.  

I just installed the weather applet on a different machine and set the location to NYC.  I got the identical "stuck" forecast that's been on my other machine for weeks.  Though today is Monday, it shows a forecast for a certain Friday, and it shows the forecast for the next couple of days, starting with Saturday, Sunday, etc.

Perhaps the source of the weather forecast is "stuck"?

:confused:

---

### Post by RobNY on 2011-01-02
I'm seeing this problem, too.  I'm also pointed to New York.

---

### Post by ray field on 2011-01-05
me too. if there isn't a machine to kick, guess I'll just have to move to New Jersey.

---

### Post by novaraz on 2011-01-05
I've been having the same problem for a few weeks as well.  Mine's stuck to a particular report; if I set it to Newark Airport, It gives me the forecast for Mon, Jan 31 / 08:51.  Similarly with other locations, just different date and time.  No location refreshes.

---

### Post by cliffliang on 2011-01-24
I fixed this by editing
/usr/share/libgweather/Locations.xml

and updated the NYC codes based on information from:
[https://bugzilla.gnome.org/show_bug.cgi?id=637597](https://bugzilla.gnome.org/show_bug.cgi?id=637597)

---

### Post by cosmolee on 2011-01-24
Thanks, that fixed it!  

Although, it's hard to believe that for a large metropolitan area like NYC, these aren't fixes being made by the developers.  It's not like it's some obscure town that nobody lives in.

And I did send an email to each developer listed in the "About" for the app.  I got no reply from anybody...

---

### Post by spottoid on 2011-01-27
cliffliang,  Thank you.  That worked for me too, but I'm located in New Jersey and needed a different zone number for Teterboro (KTEB).  I ended up using NJZ104.  Also, for anyone changing zone ID's be careful that your zone isn't listed twice in the Locations.xml file like Teterboro's is.  I had to change the ID in both listings before the forecast worked.

---

### Post by ray field on 2012-01-03
hi Cosmo (and/or everybody else) -- 

dang weather applet seems to be broke again for the new year, in NYC anyway -- NEITHER the JFK nor the LGA forecasts are updating.  does anyone know if they changed weather stations, or things are broken?  or am I the only one still on Lucid/gnome 2?

---

### Post by ray field on 2012-01-03
okay, I checked the address given at the Bugzilla link, and LGA (as well as JFK as far as I can tell) are given as NYZ176, so I made the change in /usr/share/libgweather/Locations.xml.

---

### Post by cosmolee on 2012-01-03
Hey, Ray!  I'm using Ubuntu 10.10, WeatherReport 2.30.  LGA is working fine for me at the moment.

---

### Post by cosmolee on 2012-01-03
I've got Central Park, La Guardia airport and JFK airport all as NZ076.

---

### Post by cosmolee on 2012-01-12
Dammit, now NYZ076 is broke!  But, NYZ176 seems to be working though... :P

---

### Post by sullam on 2013-03-21
> **spottoid said:**
> cliffliang,  Thank you.  That worked for me too, but I'm located in New Jersey and needed a different zone number for Teterboro (KTEB).  I ended up using NJZ104.  Also, for anyone changing zone ID's be careful that your zone isn't listed twice in the Locations.xml file like Teterboro's is.  I had to change the ID in both listings before the forecast worked.

I just wanted to let you know that as of 03/21/13 this fix still works. I fixed my problem on 10.04.

---

### Post by oldos2er on 2013-03-21
Old thread closed, please start a new thread.

---

