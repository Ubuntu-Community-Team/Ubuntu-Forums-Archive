---
title: "Desktop Zoom"
date: 2012-03-31
forum: General Help
---

### Post by Quarkrad on 2012-03-31
Sorry to ask simple question but I'm running out of time.  I have two machines, 10.10 and 11.10 (ubuntu 2D) I'm configuring Desktop Zoom on (elderly in-laws).  I have configured the Compiz plug-in (Enhanced Desktop Zoom) on both machines and can get zoom in and out using the Ctrl and buttons 4 and 5. (I think this is a common set-up - using the mouse scroll wheel to zoom in and out).   My problem - on both machines is the pan function - I have set it to button 2 and also button 1 but it does not seem to work (or I'm not using it properly).  I am wondering if I do not understand Pan - my understanding is that if you zoom a screen (e.g. a web page) and cannot see part of the screen you can move the whole screen to the area you want by panning across.

---

### Post by philinux on 2012-03-31
> **Quarkrad said:**
> Sorry to ask simple question but I'm running out of time.  I have two machines, 10.10 and 11.10 (ubuntu 2D) I'm configuring Desktop Zoom on (elderly in-laws).  I have configured the Compiz plug-in (Enhanced Desktop Zoom) on both machines and can get zoom in and out using the Ctrl and buttons 4 and 5. (I think this is a common set-up - using the mouse scroll wheel to zoom in and out).   My problem - on both machines is the pan function - I have set it to button 2 and also button 1 but it does not seem to work (or I'm not using it properly).  I am wondering if I do not understand Pan - my understanding is that if you zoom a screen (e.g. a web page) and cannot see part of the screen you can move the whole screen to the area you want by panning across.

I have it set with Left win key and mouse scroll wheel. To pan I just move mouse left or right.

---

### Post by Quarkrad on 2012-03-31
That sounds just what I would like but I'm not sure how to set up as yours (Left win key).  Could I have a look at your compiz set up?

---

### Post by Quarkrad on 2012-03-31
OK - I can get this working on my own 10.10 machine (in-laws are remote, I config via remote access)and setting the Animation settings to Speed = 2.8680 and Timestep = 1.2000 I get a smooth zoom in and out.  Looks nice - pan also works.  I have a 11.10 machine set up in Virtualbox on my PC to simulate my mother-in-laws machine and transferred the same Compiz settings.  However, the zoom in an out is very jerky compared to my 10.10 native machine - could this be a virtualbox issue?  And the pan function does not work in 11.10 - despite same set up.  Could this be a Unity issue or should it work?

---

### Post by philinux on 2012-03-31
> **Quarkrad said:**
> That sounds just what I would like but I'm not sure how to set up as yours (Left win key).  Could I have a look at your compiz set up?

All I did is what this guy did here.

[http://www.youtube.com/watch?v=X1-T8UK2b_U](http://www.youtube.com/watch?v=X1-T8UK2b_U)

You can skip to half way through. Your VB will most likely be jerky as it's not using the graphics card.

---

### Post by Quarkrad on 2012-03-31
Thanks for the link.  I followed the instructions but I still have no pan function.  Just installed 12.04 as a new VB guest and I get the same result as 11.10 - I can zoom in and out but no pan function.  There are many settings in Enhanced Zoom (Compiz) - I guess you can leave most as they are but with youtube videos they never go into detail. I think (obviously not) I have followed the instructions but I can't get pan to work so I'm a bit stuck.

---

### Post by Quarkrad on 2012-04-01
bump - still can't pan on 11.10 (or 12.04)

---

### Post by stinkeye on 2012-04-02
Why do you need the pan function?
Don't the default settings pan with mouse movement?
In the mouse behaviour tab > zoom mode
sync mouse .....zoom area moves with mouse
pan area ...zoom area pans when mouse is moved to edges.

---

### Post by Quarkrad on 2012-04-04
Hmmm - just done fresh installs of 11.10 and 12.04 in Virtualbox 4.  Updated and upgraded both (sudo apt-get update && sudo apt-get upgrade) and installed ubuntu-restricted-extras.  I then install compiz settings manager via the software centre.  The default settings are the same in both (enhanced desktop is ticked - not zoom desktop and the defaults within enhanced desktop is the same). However, the actions are not the same (testing on a web page where this is needed).

12.04 - zooms in & out, but when zooming back out stops at original screen size
11.10 - zooms in & out, but when zooming back gets smaller and smaller 

12.04 - having zoomed in you can move the page up & down/side to side (pan) just by moving the mouse.

11.10 - moving the page/pan does not work.

Any help on this appreciated.  Mother-in-law has 11.10 and it took me many hours to get her (damn) Apple keyboard working (originally show was 10.10).  Easiest for me is to get this working on 11.10 - 12.04 (description above) works exactly how I would like it 'out of the box'.

---

### Post by stinkeye on 2012-04-04
It may be a virtual box thing.
I just logged in to my 11.10 install and set compiz back to defaults.
ie alt+F2
```
unity --reset
```
The enhanced zoom was enabled in defaults and all I did was bind
super+mouse4 and super+mouse5 to zoom in and zoom out.
In the mouse behaviour Tab both **sync mouse** and **pan area**
behaved as they should.

Works exactly the same for me, as in 12.04.

```
glen@Oneiric:~$ compiz --version
Compiz 0.9.6
```

---

### Post by Quarkrad on 2012-04-04
Thanks - I'm down at mother-in-laws tomorrow.  I will look/play at her machine rather than play on Virtualbox.

---

### Post by Quarkrad on 2012-04-05
Pan doesn't work on 11.10.  I'll look at 12.04 end of month.

---

