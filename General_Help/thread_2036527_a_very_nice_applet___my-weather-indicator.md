---
title: "a very nice applet  :: my-weather-indicator"
date: 2012-08-02
forum: General Help
---

### Post by shantiq on 2012-08-02
if you like a lot of data on your weather forecast you probably will enjoy this here:  i have just installed it instead of indicator-weather   and it shows much more

```
sudo add-apt-repository ppa:atareao/atareao
```


```
sudo apt-get update
```

```
 sudo apt-get install my-weather-indicator
```


then to applications/accessories   and set your prefs  [pick autostart in general options]



and you get this

[ATTACH]222129[/ATTACH]


leading to this


[ATTACH]222128[/ATTACH]

---

### Post by timgood on 2012-08-02
Works much better on Unity than on Gnome Shell :(

---

### Post by blueshead on 2012-08-02
It works fine.. Good thing too..my weather indicator has been broke for weeks and stuck at 79F. 79f in New Orleans in the summer.. lmao..

---

### Post by shantiq on 2012-08-02
> **blueshead said:**
> It works fine.. Good thing too..my weather indicator has been broke for weeks and stuck at 79F. 79f in New Orleans in the summer.. lmao..


ha funny blueshead    same reason i moved over


i had been on 15 C   night and day for 4 days before i smelt a rat
so looks like indicator-weather sometimes gets stuck

could see no way to unstick it:KS     but my- ...  is the same but deluxe info


here in england we dream of 79F

---

### Post by shantiq on 2012-08-31
after a while the google weather info went dead;    reading around i found this trick



```
sudo apt-get --reinstall install my-weather-indicator
```



basically updates it


google info still not available but now there is World Weather Online on the most recent version and that is even better than Google it seems...

---

### Post by rickm1945 on 2012-08-31
> **shantiq said:**
> after a while the google weather info went dead;    reading around i found this trick



```
sudo apt-get --reinstall install my-weather-indicator
```

basically updates it


google info still not available but now there is World Weather Online on the most recent version and that is even better than Google it seems...
Is this the one that sets by the system clock? I am running Unity with a Cinnamon Desktop.

---

### Post by shantiq on 2012-08-31
hi rick this is the way it looks here and what you get when click on forecast   .... not on unity myself

[ATTACH]223460[/ATTACH]

[ATTACH]223461[/ATTACH]


[**on unity**]("http://www.omgubuntu.co.uk/tag/myweatherindicator")

[IMG]http://cloudfront.omgubuntu.co.uk/wp-content/uploads/2011/10/screen-shot-2011-10-25-at-11.30.34.jpg[/IMG]

---

### Post by rickm1945 on 2012-08-31
> **shantiq said:**
> hi rick this is the way it looks here and what you get when click on forecast   .... not on unity myself

[ATTACH]223460[/ATTACH]

[ATTACH]223461[/ATTACH]


[**on unity**]("http://www.omgubuntu.co.uk/tag/myweatherindicator")

[IMG]http://cloudfront.omgubuntu.co.uk/wp-content/uploads/2011/10/screen-shot-2011-10-25-at-11.30.34.jpg[/IMG]
thanks, this is nice. I installed form Software Manager.

---

### Post by CK1 on 2012-09-04
My "my-weather-indicator" had also stopped working. I re-installed as recommended above, but it only started working after I deleted the directory ~/.config/my-weather-indicator in my home directory. Re-starting my-weather-indicator then gave me new options and it now works again.

---

### Post by Sam Mills on 2012-10-31
Thank you for this awesome weather applet!

---

### Post by seyfer on 2013-01-07
shantiq. Thank you! It's better than indicator-weather.

---

### Post by coldraven on 2013-01-07
I live on a remote island and for a weather app to be useful it has to have wind speed and direction. 
I had a "LCD" lookalike widget that used to work but it had one major flaw. It had an arrow showing where the wind was going, not the direction it came from.
(180 degrees opposite).

If you live near the sea then always remember that tides go to, winds come from.

So if my boat breaks down in a Westerly tide I will drift West.
If it breaks down with a Westerly wind I will drift East.
Got it? :)

---

### Post by shantiq on 2013-02-01
h,mmmmmmmmm   and now World Weather Online has gone on the blink and only Yahoo works which is not very good


anyone else finding that AND found a fix?

purged and reinstalled but still same

---

### Post by shantiq on 2013-02-02
there is now a launchpad [**bug report**]("https://bugs.launchpad.net/my-weather-indicator/+bug/1112765") if anyone has same and wants to contribute


in the meantime back to indicator-weather yikes :::]]]

---

### Post by shantiq on 2013-02-04
if anyone had a problem with worldweatheronline in the last few days


fix is;

go [**=>to **]("http://www.worldweatheronline.com") sign in they will issue you with API number

> gedit /usr/share/my-weather-indicator/worldweatheronlineapi.py

and change number on line 34


**more detailed**


install leafpad or mousepad they have line numbers

> sudo apt-get install leafpad

then go

> leafpad /usr/share/my-weather-indicator/worldweatheronlineapi.py

click options/line numbers now you have line numbers

go to line 34 and put your new personal API instead of other one

---

### Post by shantiq on 2013-02-14
there is now an update and you can enter your own [**API[click on free sign up]**]("http://www.worldweatheronline.com/") by going to preferences once installed

---

### Post by shantiq on 2013-03-23
if any you have moved to 13.04 and installed MWI you may find [at least i do with gnome-fallback] that the moon phase info /forecast/and sunrise sunset times have gone and all is left is this

If you are with unity and all is still there please comment would love to know one way or the other

[IMG]http://i53.fastpic.ru/big/2013/0323/00/a4086c342ad8ab4d0f42b6de5f468f00.png[/IMG]


so not happy with that had a stroke of luck and found
gkrellmoon [synaptic] which has in any case more info on moon phases than MWI


 [find it under Systems Tools[gnome] or dash[Unity] right click F1 for config and allow moonclock in plugins and untick all Builtins you do not wish to see]

Hover on moon on applet for word info

[IMG]http://i53.fastpic.ru/big/2013/0323/a9/b842ca7317f198b89d23638ac37c02a9.png[/IMG]

There is also gkrellweather which has a lot of info too

[IMG]http://i53.fastpic.ru/big/2013/0323/fa/aaf635355c323cf56b979b7df249b3fa.png[/IMG]


So using MWI and gkrell in combination all is good again on 13.04 apart from forecast but that can be got from indicator-weather as can sunrise-sunset

PLease comment if you found all is good anyway on MWI
It has not been my experience thus far

---

