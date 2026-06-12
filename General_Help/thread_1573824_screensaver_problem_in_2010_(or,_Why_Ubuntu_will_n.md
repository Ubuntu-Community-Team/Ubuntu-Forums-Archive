---
title: "screensaver problem in 2010 (or, Why Ubuntu will never be ready for mainstream)"
date: 2010-09-13
forum: General Help
---

### Post by stim on 2010-09-13
I  use ubuntu at work, and have my screensaver set to come on after 1 minute of inactivity, and lock the screen. Frequently, while I am talking to someone, the screen will start to go blank, so I'll touch the mouse or touchpad to keep it from locking me out (not a big deal, and completely expected with a one-minute lock time)

BUT

When I leave for lunch, or to go to the bathroom , or do anything that involves me leaving my desk,  where I would actually want my computer to lock, I come back and its not locked, not in the screensaver, nothing. Just sitting at my desktop, wide open.  

SUMMARY:
When I am at my desk, it locks every minute. When I leave my desk, it never locks. 



I have taken to manually locking the screen when I leave, and not depending on ubuntu to do something as simple as locking the screen after a set time.


As far as I know this works on windows and my other distributions just fine (gentoo, debian).  So do I sit and try to debug exactly why a SCREENSAVER doesn't work as expected, or do I just move on, and chalk it up to "linux will never be for the masses"?


I'm pretty sure I have better uses for my time than to debug a screensaver.


Ubuntu, I recommend you to everyone I know, but this is why you will never be ready for mainstream.

---

### Post by perspectoff on 2010-09-13
I don't have that problem. My screensaver works properly in every version, and locks (and unlocks) properly. However, I only use the screen blanker, which is the most basic one. 

For many years, custom screensavers were one of the biggest portals for trojans and viruses, on every OS. If security is really that important to you, stick to the basics.

But, I don't really understand what is happening to you. It works when you are talking to someone but it doesn't work when you go to the bathroom?

Sounds like you have upset it in some way. Perhaps you need to bring your computer some flowers, or chocolate, or whisper sweet nothings to it...

---

### Post by stim on 2010-09-13
Its not a custom screen saver, its a blank screen just like you..... I thought that might have been part of the problem so reverted to simple blank screen.

---

### Post by realzippy on 2010-09-13
Maybe some power saving issue?
Suggest to watch your computer without doing anything until you see what is going on.

---

### Post by stim on 2010-09-13
I had the same thought zippy, the offending computer is indeed a laptop, but I have all sleep, suspend, hibernate turned off.   If you have any other ideas about what power saving features might be causing this , i'd love to hear them

Also , as far as "watching it to see what it does" , thats hard to do. When I watch it, or am at my desk through the course of the day,  it works fine. Only when I leave for lunch or other extended time, does it not work.

---

### Post by realzippy on 2010-09-13
...disabled power manager in Startup Applications?

,,,somebody uses your computer and leaves the room 59 seconds before you arrive   ;-) ?

---

### Post by Jazzy_Jeff on 2010-09-13
> **stim said:**
> I  use ubuntu at work, and have my screensaver set to come on after 1 minute of inactivity, and lock the screen. Frequently, while I am talking to someone, the screen will start to go blank, so I'll touch the mouse or touchpad to keep it from locking me out (not a big deal, and completely expected with a one-minute lock time)

BUT

When I leave for lunch, or to go to the bathroom , or do anything that involves me leaving my desk,  where I would actually want my computer to lock, I come back and its not locked, not in the screensaver, nothing. Just sitting at my desktop, wide open.  

SUMMARY:
When I am at my desk, it locks every minute. When I leave my desk, it never locks. And if security is that important to you, you should never leave the desk with the computer open in the first place. How hard is it to put a lock screen icon on your panel and click it when you are leaving your computer.



I have taken to manually locking the screen when I leave, and not depending on ubuntu to do something as simple as locking the screen after a set time.


As far as I know this works on windows and my other distributions just fine (gentoo, debian).  So do I sit and try to debug exactly why a SCREENSAVER doesn't work as expected, or do I just move on, and chalk it up to "linux will never be for the masses"?


I'm pretty sure I have better uses for my time than to debug a screensaver.


Ubuntu, I recommend you to everyone I know, but this is why you will never be ready for mainstream.

It works every time on my computer so I don't know what the problem is. Maybe it knows you don't like it ):P.

---

### Post by Jazzy_Jeff on 2010-09-13
If security is that important to you, why would you leave your desk without the computer being locked in the first place? How hard is it to put a lock screen icon on your panel and click it before you leave your desk? I have also had instances using Windows in the past where the screensaver did not kick in because some program running in the background was not working properly and so the screensaver never activated.

---

### Post by stim on 2010-09-13
As stated in the original post, I am now locking it manually. However, the point of my post was that this should work. First time. No debugging, no troubleshooting.  

If I was compiling a kernel module or driver, patching code, optimizing code, or doing something else technical,  problems can be expected.

If I want my screen to blank out after 1 minute of inactivity, that should work.

---

### Post by Jazzy_Jeff on 2010-09-13
> **stim said:**
> As stated in the original post, I am now locking it manually. However, the point of my post was that this should work. First time. No debugging, no troubleshooting.  

If I was compiling a kernel module or driver, patching code, optimizing code, or doing something else technical,  problems can be expected.

If I want my screen to blank out after 1 minute of inactivity, that should work.

Obviously this does not happen to a lot of people or there would be more complaints. I have 3 systems running and they all lock once the screensaver kicks in. I don't know what is causing your problem. Just because 1 computer is having this problem does not mean it is not ready for mainstream use.

---

### Post by BigCityCat on 2010-09-13
This idea runs on the assumption that Ubuntu would become "mainstream" overnight. More than likely becoming "mainstream" would happen over a period of time. In which case these minor inconveniences that us current users face and learn how to fix on our own. Would be fixed by the fact that the resources received by being "mainstream" or approaching "mainstream" would enable that eventuality.

---

### Post by Jazzy_Jeff on 2010-09-13
If becoming mainstream meant that everything just worked Windows would have never made it then. I cannot remember a version of Windows where I did not have problems of some kind. It happens with all operating systems.

---

### Post by snkiz on 2010-09-13
You say it locks when you sit and watch it, for how long? Do you watch it for the same amount of time you'd be gone for lunch? It could be the screensaver is fine and something else is causing it to unlock after a period of time. Or possibly any number of programs designed to inhibit screensaver/power-saving functions.

You mentioned that you have shut off power saving capabilities, could it be that they are still being started even though they don't run? or your machine is doing strange things to the run level because of hardware options? You did say it  was a laptop, not using power-saving is an unusual use-case for a mobile computer.

Any somewhat informed Linux user knows mainstream adoption is in the hands of OEM's and manufactures. If they choose to shut us out no amount of advertising or development will save us.

---

### Post by nbr on 2011-02-11
I was having the same problem (screensaver would not kick in, but sometimes would) and I found the culprit:

Totem

When Totem is running, it prevents the screensaver to kick in, because if you're watching a movie, that's how it should behave.

To prevent this, there is an option that should be used in Totem:
Edit -> Preferences -> Display -> Allow the screensaver to activate even when audio-only is playing" (the even doesn't make sense to me, but anyway)

With this option activated, screensaver does kick in even if audio is playing (but not a movie, no matter in which Desktop area).

Sometimes I also hate Ubuntu when things stop working, but this time, it's a feature, not a bug...

---

