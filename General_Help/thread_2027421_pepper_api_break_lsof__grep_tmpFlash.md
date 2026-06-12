---
title: "pepper api break lsof | grep /tmp/Flash*"
date: 2012-07-16
forum: General Help
---

### Post by Primefalcon on 2012-07-16
currently with firefox as well as older version of chrome

you could open a flash video file in vlc or totem by smply doing

```
lsof | grep -E /tmp/Flash*
```

which would output something like....
```
plugin-co 18796       <username>   20w      REG        8,1  9866048  132877 /tmp/FlashXXGrh9Wn (deleted)
```

to open said video in vlc all you then had to do was type in the following
```
vlc /proc/18796/fd/20
```

however this is not working with the newer version of flash in chrome (pepper), and I am wondering if anyone else has any method to locate the cached file to watch/save (reason I do it is flash can be laggy but plays smoothly in a desktop client even at very high quality).

and while the method still works in firefox, they'll either have to go pepper or drop flash eventually, and it'd be nice to have a solution before that happens.. and this method will allow me to watch flash in better quality and with less (its's non-existant) lag/jitter even better than windows....

---

### Post by drmrgd on 2012-07-16
I noticed this too, and have switched to Firefox for this kind of thing.  I didn't quite know the reason, though.  Now I see what the difference is.  Sorry I don't have a solution - hopefully this is something that can be worked out easily.

---

### Post by Primefalcon on 2012-07-16
> **drmrgd said:**
> I noticed this too, and have switched to Firefox for this kind of thing.  I didn't quite know the reason, though.  Now I see what the difference is.  Sorry I don't have a solution - hopefully this is something that can be worked out easily.
hopefully, I'll try t keep this post active until either myself or someone else comes up with a solution...

I am figuring it's still a matter of adjusting grep for search parameter's but we'll see

---

### Post by matt_symes on 2012-07-16
Hi 

There is a way to do it PrimeFalcon. 

I'm just trying to find out if posting the solution would break the forums guidelines.

Kind regards

---

### Post by Primefalcon on 2012-07-16
> **matt_symes said:**
> Hi 

There is a way to do it PrimeFalcon. 

I'm just trying to find out if posting the solution would break the forums guidelines.

Kind regards
there are plenty of sites will allow their flash content to be viewed, only a very few don't and we could have a disclaimer that you must abide by individual rules, for example I have put flash content on some of my sites before I wouldn't care if you did this to enhance viewing experience.

itsnot exactly like yor copying the file or anything, just using a different viewer/browser to view the content

---

### Post by drmrgd on 2012-07-16
I was a little concerned about Forum rules too.  Maybe a PM with the solution.....:D

I tried myself a host of grep queries, but just couldn't nail it down.  Part of the problem is that I don't yet understand Pepper (just haven't read up on it yet).

---

### Post by Primefalcon on 2012-07-16
One idea I have which I'll try later unless someone else wants to...

is to output a copy of the output of lsof to a file, close the flash player and then output to a different file and maybe use something like diff to compare them

---

### Post by Primefalcon on 2012-07-16
either that or read through the pepper docs wherever they're located

---

### Post by Primefalcon on 2012-07-17
just keeping this active

---

### Post by Primefalcon on 2012-07-19
starting to feel this post is probably a lost cause tbh, so this will be my last bump unless a solution is found or something

---

### Post by sughoshk on 2012-07-24
This not the exact solution you asked for but its close. You can force chrome to use libflashplayer by default:

Navigate to [COLOR="Red"]chrome://plugins[/COLOR]

You should see:

[COLOR="Red"]Flash (2 files) - Version: 11.2 r202
Shockwave Flash 11.2 r202[/COLOR]

Hit details on the right for an expanded view.

Disable pepper's flash player. Mine was at [COLOR="red"]/opt/google/chrome/PepperFlash/libpepflashplayer.so[/COLOR]

Do confirm if this works for you.

---

### Post by Syock on 2012-08-01
```
sudo lsof | grep Shockwave
```
I don't know if there's a better way.

---

### Post by kurt18947 on 2012-08-01
I'm probably missing the obvious but why not use one of the flash downloaders in Firefox's add-ons?

---

### Post by vasa1 on 2012-08-01
> **matt_symes said:**
> Hi 

There is a way to do it PrimeFalcon. 

I'm just trying to find out if posting the solution would break the forums guidelines.

Kind regards
That seems primarily related to YouTube and other sites that have copyrighted material? At least that's what I gather from [here]("http://ubuntuforums.org/showthread.php?t=1850955"): "We do not support circumventing TOS, EULA, etc here. Such threads will be closed and offending users will be penalised with infractions and warnings."

Now whether the disclaimer that what is being discussed is an alternate way of viewing content, copyrighted or not, will suffice is a call someone has to make :)

---

### Post by drmrgd on 2012-08-01
> **kurt18947 said:**
> I'm probably missing the obvious but why not use one of the flash downloaders in Firefox's add-ons?

I think the goal is / was to remain using Google-Chrome as this function seems to only be borked in that browser with the switch over to Pepper Flash.  Everything still works as normal in Firefox.

I've preoccupied with too many other things and haven't returned to this.  Although I did recently learn that one can monitor lsof output using htop, which may be helpful here.  Just run htop as sudo and then press 'l' (lower-case "L") to see a sorted list of open files.

---

### Post by kurt18947 on 2012-08-02
> **drmrgd said:**
> I think the goal is / was to remain using Google-Chrome as this function seems to only be borked in that browser with the switch over to Pepper Flash.  Everything still works as normal in Firefox.

I've preoccupied with too many other things and haven't returned to this.  Although I did recently learn that one can monitor lsof output using htop, which may be helpful here.  Just run htop as sudo and then press 'l' (lower-case "L") to see a sorted list of open files.

Doh, you're correct, sorry.  I don't really care for Chrome/Chromium so haven't used it much.  As long as web sites don't require flash versions newer than 11.2.xxxx I'm going to continue with ol' foxy.  I'll worry about security issues if/when Adobe drops patches in 5 years.

---

