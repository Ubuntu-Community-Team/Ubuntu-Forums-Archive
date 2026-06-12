---
title: "Ubuntu logs me off when idle?"
date: 2012-01-27
forum: General Help
---

### Post by Coolmariorocks on 2012-01-27
Ok so on my desktop computer Ubuntu 10.10 logs me off when it goes idle.. I don't want this to happen i want it just like make the screen go blank or show the screensaver instead. any ideas on how i can get ubuntu

---

### Post by 2F4U on 2012-01-28
Is the desktop crashing? You may look into .xsession-errors in your home folder to verify if the desktop crashes.

---

### Post by lisati on 2012-01-28
Sure it's not just locking the screen?

---

### Post by Coolmariorocks on 2012-01-28
> **2F4U said:**
> Is the desktop crashing? You may look into .xsession-errors in your home folder to verify if the desktop crashes.
No the desktop isn't crashing..

When i am not on the computer for like 5 minutes it logs me off. (is that the screen locking?)  if it is screen locking how do i turn it off?

---

### Post by Frogs Hair on 2012-01-28
Locate screen in the system settings and change the time .

---

### Post by Coolmariorocks on 2012-01-28
I set it to 2 hours... I had lock screen unchecked in Screensaver on ubuntu 10.10  but it doesn't load the screensaver when idle..   also i haven't installed updates yet.. We are waiting for a while to install updates

---

### Post by 2F4U on 2012-01-29
The computer may be going to suspend (thats a form of a sleep state where the processor shuts down most of its activity to save power). You can check your power management settings.

---

### Post by Coolmariorocks on 2012-01-29
> **2F4U said:**
> The computer may be going to suspend (thats a form of a sleep state where the processor shuts down most of its activity to save power). You can check your power management settings.
 How would sleep have something to do with my computer logging me out?:confused:

---

### Post by Roving Sign on 2012-01-29
> **Coolmariorocks said:**
> How would sleep have something to do with my computer logging me out?:confused:

You're not being logged out.

Your screen is being locked - and you have to enter your password to unlock.

In the Settings - look for "Screen" - you can turn it off there - or change the time before lock.

---

### Post by Coolmariorocks on 2012-01-29
> **Roving Sign said:**
> You're not being logged out.
 
Your screen is being locked - and you have to enter your password to unlock.
 
In the Settings - look for "Screen" - you can turn it off there - or change the time before lock.
 I am confused. I'm all new to ubuntu  where is Settings? where is screen?:confused::confused:

---

### Post by Roving Sign on 2012-01-30
> **Coolmariorocks said:**
> I am confused. I'm all new to ubuntu  where is Settings? where is screen?:confused::confused:

Well - Im still running 11.10 but just switched to the Cinnamon desktop the other day - so this is from memory...

Click the Gear icon on the left sidebar.

A panel with various icons will appear - look for "Screen"

Click that one - you should see the dialogs for turning the lock off or adjusting the time until lock.

---

### Post by Peder_Erickson on 2012-01-30
Uh... they're using 10.10, not 11.10, so they are looking for 'Screensaver', not 'Screen'

Go to System->Prefrences->Screensavers and check if the 'Lock Screen' checkbox is checked. :)

On another note just to check if we're getting everything right, is it showing the login screen, or a screen with a black background?  the black background one means that the screen is being locked, just as everybody else says is happening, if it's showing the purple wallpaper and you have to select your name, then you may be getting logged out.

Screensaver is in all ubuntu versions before 11.10, for some reason it  got re-named 'Screen' in 11.10, and the GNOME project removed all of the  screensavers except the blank screen one.

---

### Post by Coolmariorocks on 2012-01-30
> **Peder_Erickson said:**
> Uh... they're using 10.10, not 11.10, so they are looking for 'Screensaver', not 'Screen'
 
Go to System->Prefrences->Screensavers and check if the 'Lock Screen' checkbox is checked. :)
 
On another note just to check if we're getting everything right, is it showing the login screen, or a screen with a black background? the black background one means that the screen is being locked, just as everybody else says is happening, if it's showing the purple wallpaper and you have to select your name, then you may be getting logged out.
 
Screensaver is in all ubuntu versions before 11.10, for some reason it got re-named 'Screen' in 11.10, and the GNOME project removed all of the screensavers except the blank screen one.
I had lock unchecked and had display screensaver when idle.. checked but it went into idle..

---

### Post by Coolmariorocks on 2012-02-01
I think I found the problem. It was because I didn't have xscreensaver installed.. Marking topic was Resolved :D:popcorn:

---

