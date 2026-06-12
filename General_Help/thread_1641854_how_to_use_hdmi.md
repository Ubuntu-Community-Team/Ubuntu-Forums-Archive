---
title: "how to use hdmi?"
date: 2010-12-09
forum: General Help
---

### Post by ibrahim.k on 2010-12-09
Hi
 
i want to connect my laptop to the lcd using hdmi
I have nvidia video card 9200 gs and the driver is installed
 
after connecting both together nothing happens!
do i have to change anything in the system or display settings?
I am using ubuntu 10.10
 
thnx

---

### Post by iosuna86 on 2010-12-09
Did you select the HDMI source in your TV? I have to switch my TV to HDMI everytime I connect it to my laptop. It does not do anything automatically.

I hope that helps solve your problem.

---

### Post by ibrahim.k on 2010-12-11
Yes, I changed the source in the lcd from av to HDMI but it didn't work! should it work automatically without changing anything in the system?

thnx in advance

---

### Post by iosuna86 on 2010-12-11
Hi again!

It's funny cause I am having the same problem too!!

I have been using the HDMI to watch some movies on my TV screen and now I have installed Ubuntu 10.10 on my gf's laptop and when I connect the HDMI there is a message on the TV screen saying "No signal". 

I decided to work it out by myself with almost no result. I went to System - Preferences - NVIDIA X Server Settings. I went to X Server Display Configuration and selected my TV as the model to display. I checked "Separate X screen" but nothing happens. I then checked "TwinView" but I cannot figure out how to make it work. I open a movie and the movie appears on the TV screen, but I cannot manage to change the volume, pause it, select full screen. I have one thing on my laptop's screen, and another one on the TV set.

It is pretty weird. 

I know I haven't solved you anything, but I will keep trying.

Cheers!

---

### Post by iosuna86 on 2010-12-11
I finally got it to work!!

I am pasting you my reply to a similar thread which solved my problem.

> I got it!!!

That was quick.

OK, here is what I did.

1. I connected the HDMI cable to my laptop with the TV already on (my  laptop was on too). 2. Went to NVIDIA X Server Settings, then to X  Server Display Configuration and on the Display Tab I chose my TV  (Samsung) as the "model", then configure it so that the TwinView mode  was switched on, then I changed the resolution to 1920x1080, position:  absolute and then I checked the box "Make this the primary display for  the X server" (I guess this is what I was missing in the first place).
3. Clicked on Apply and then my TV started to show what I was doing on my laptop. 

I hope that can solve your problem too.

Cheers!Hope that works for you too!


Edit: here is the link to the other thread:
[http://ubuntuforums.org/showthread.php?t=1639338](http://ubuntuforums.org/showthread.php?t=1639338)

---

### Post by ibrahim.k on 2010-12-12
Thank you very much iosuna86 it worked with me as well, but I am missing the screen boarders!! I can't see ubuntu panels for example, and there is no sound, I have changed the hardware settings in System --> Preferences --> Sound ---> hardware ---> hdmi output , but it didn't work,

Thnx again

---

### Post by iosuna86 on 2010-12-12
I am having trouble with that too. 

I'll let you know if I figure it out!

---

### Post by ibrahim.k on 2010-12-13
I think that it is a bug in Meerkat, I will test it on lucid soon.

---

### Post by iosuna86 on 2011-01-01
> **ibrahim.k said:**
> I think that it is a bug in Meerkat, I will test it on lucid soon.

I FINALLY got it all to work!!!

OK, so here is what you need to do.

Go to the terminal and type

```
alsamixer
```

Move with the arrow keys within the terminal and find "S/PDIF 1". To do so, move to the right 5 times and there, press "m" to unmute it (so that a green box with a double 0 appears, just like in the screenshot). It is muted by default. 

Now, the next time you select "HDMI Output" in Sound Preferences, you'll get audio thru the TV.

Hope that helps!

---

