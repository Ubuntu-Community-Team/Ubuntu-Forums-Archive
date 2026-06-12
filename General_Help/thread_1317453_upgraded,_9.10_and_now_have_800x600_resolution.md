---
title: "upgraded, 9.10 and now have 800x600 resolution"
date: 2009-11-06
forum: General Help
---

### Post by rhythmiccycle on 2009-11-06
I just upgraded to ubuntu 9.10

and now my screen resolution is at 800x600. I can't work with this. 

I went to display settings but 800x600 is the max.
How do i make it bigger?

if it can't go bigger, then how to I go back to 9.04?

---

### Post by Gosport on 2009-11-06
Try this thread: [http://ubuntuforums.org/showthread.php?t=1311772](http://ubuntuforums.org/showthread.php?t=1311772)

---

### Post by rhythmiccycle on 2009-11-06
thanks for the reply, I guess I'm going to have to do a bunch of research to make it work.

I don't want to deal with this. my monitor worked just fine with all the other versions of ubuntu. why did they make the new one stupid, I thought it was supposed to be better?

i read 

> 
The way to correct this is to get the monitor's technical specifications from the vendor and tell X how to use those specs via /etc/X11/xorg.conf.


If I have to go threw all this none sense to get it to work, I'd rather just go back to 9.04. How do I down grade?

---

### Post by rhythmiccycle on 2009-11-07
this is what I found:

ViewSonic VE175 17" LCD

with an optimum resolution of 1280x1024, brightness of 250 nits and contrast ratio of 550: 1

Synchronization Range - Vertical 	50 - 75 Hz 

Synchronization Range - Horizontal 	30 - 82 kHz 

Brightness    	300 cd/m² 

Color Depth     	24-bit (16.7M Colors)

---

### Post by rhythmiccycle on 2009-11-07
I tried to change xorg.conf, using the specs I found online, and now my monitor is out of range.

it says "out of range H:81.1 khz, V:64.9hz"

I don't understand why thats out of range, the specs I found must be wrong. 

now i'm trying to put it back from the command line

I "cd" into /ect/x11

then enter the command

```

sudo cat > xorg.conf

``` 
but then i get
"-bash: xorg.conf permission denied"

please help!!

all I have now is a command line!!

---

### Post by rhythmiccycle on 2009-11-07
I fix the last problem my self, using nano, not cat.

but now I'm right back where I started.

the specs where wrong I guess.

---

### Post by rhythmiccycle on 2009-11-07
I looked up the manual  and found this:

f:30-80kHz,f:50-75Hz

i changed it to those specs and still am getting out of range:

H:74.9khz
V:59.9hz

I can go back to defult,

BUT HOW DO I GET IT TO WORK AT the right resolution?

---

