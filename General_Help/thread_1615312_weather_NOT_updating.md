---
title: "weather NOT updating"
date: 2010-11-06
forum: General Help
---

### Post by guss606 on 2010-11-06
Hi guys,

Since I installed ubuntu 10.10 and the weather applet is on the exact same details, it is NOT updating what so ever :confused:. how can this be fixed please?

Please guys this is very important for me, Thanks.

---

### Post by kako13 on 2010-11-06
Have you tried by clicking the icon and right click -> update?

---

### Post by guss606 on 2010-11-07
:shock:

Yes man, i wrote that with capital letters that it is "**_[SIZE="4"]NOT[/SIZE]_**" updating.

any idea guys!?

---

### Post by guss606 on 2010-11-08
any idea guys?! Thanks

---

### Post by wojox on 2010-11-08
Try picking a different location for your applet and see if it works.

---

### Post by guss606 on 2010-11-08
> **wojox said:**
> Try picking a different location for your applet and see if it works.

Thank you, it worked for another location in same country. 

Is there a way to change the weather source?!

---

### Post by wojox on 2010-11-08
> **guss606 said:**
> Thank you, it worked for another location in same country. 

Is there a way to change the weather source?!

Not that I'm aware of. I'm in the U.S. and it pulls the info from the nearest airport that I pick. Try Googling around.

---

### Post by guss606 on 2010-11-08
Thanks anyway.

---

### Post by gmargo on 2010-11-08
What is the location that is not updating?

---

### Post by guss606 on 2010-11-09
> **gmargo said:**
> What is the location that is not updating?

The Hague, Netherlands

---

### Post by gmargo on 2010-11-10
I assume you are using the Gnome desktop. Are you using the weather applet (gweather) or the "locations" section of the calendar widget? Or both?

---

### Post by guss606 on 2010-11-10
> **gmargo said:**
> I assume you are using the Gnome desktop. Are you using the weather applet (gweather) or the "locations" section of the calendar widget? Or both?

Yes, I am on GNOME desktop and i use the locations of the calendar.

---

### Post by gmargo on 2010-11-10
The weather data entry for The Hague uses **[METAR]("http://en.wikipedia.org/wiki/Metar")** code EHVB which corresponds to the [**Valkenburg Naval Air Base.**]("http://en.wikipedia.org/wiki/Valkenburg_Naval_Air_Base")

It would appear that the weather station at Valkenburg has stopped reporting the weather through the METAR system.  The last weather update from EHVB is dated 2010/04/01.  And that is why the weather never seems to update - it's showing the most recent report.

Here's the URL that libgweather uses to get the EHVB information: [http://weather.noaa.gov/mgetmetar.php?cccc=EHVB](http://weather.noaa.gov/mgetmetar.php?cccc=EHVB)  You can see on that page that the observation date and time was "2010/04/01 07:55".


And after all that I finally think to look for bug reports, and here they are:  
[https://bugzilla.gnome.org/show_bug.cgi?id=617689](https://bugzilla.gnome.org/show_bug.cgi?id=617689)
[https://bugs.launchpad.net/ubuntu/+source/libgweather/+bug/559105](https://bugs.launchpad.net/ubuntu/+source/libgweather/+bug/559105)

---

### Post by guss606 on 2010-11-10
Thank you very much for this information, at least now i know the reason why.

Good thing thou, I am moving to another city next week which i tested its weather and it works :D

Thank you again.

---

