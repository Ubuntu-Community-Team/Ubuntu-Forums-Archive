---
title: "Purging Ubuntu of Evolution"
date: 2009-12-29
forum: General Help
---

### Post by FeraTech on 2009-12-29
Is there any way to remove all the "Evolution" packages without breaking the desktop.

For the last two years I have tried to switch from Thunderbird to Evolution and every time it has been lacking in development and features available in Thunderbird.

Not to mention Thunderbird being a cross platform application making it much more accessible to regular users.

Evolution has several background tasks which run uselessly. I feel like the development of Evolution would be much more suited to be put elsewhere.

---

### Post by last1 on 2009-12-29
I've successfully removed evolution on machines before, but I have noticed it does break one minor thing.. You won't be able to run About Me, it won't even let you open it. That's where you add info for stuff like your contact info or whatever, ubuntu uses evolution to manage all that. I never use it for that, but it's also the only dialog you can use to change the picture that represents you, I think it's used to denote your user in the login screen. Again, not really important but something you should know. There's also a thing in there to change your user password, but you can do that in a few other ways. 

There might be something else that goes wrong if you remove it, but that's about all I've ever found. I usually just remove it anyway.

---

### Post by gsmanners on 2009-12-29
Removing Evolution technically breaks the Gnome desktop, in particular because gnome-panel depends on it (not to mention ubuntu-desktop). Your only option from where I'm sitting is to remove Gnome altogether to get a clean removal of Evolution.

---

### Post by last1 on 2009-12-29
> **gsmanners said:**
> Removing Evolution technically breaks the Gnome desktop, in particular because gnome-panel depends on it (not to mention ubuntu-desktop). Your only option from where I'm sitting is to remove Gnome altogether to get a clean removal of Evolution.

Does it? Man, that's lame. Eeebuntu does not build their packages so that gnome-panel has evolution as a dependency, I wonder why the main Ubuntu version does it that way?

---

### Post by snowpine on 2009-12-29
Pretend it isn't there... remove the icon from the panel and use Thunderbird (or whatever) instead. Evolution will take up a tiny amount of your hard drive, but you won't break Gnome.

---

### Post by Uncle Spellbinder on 2009-12-29
> **snowpine said:**
> Pretend it isn't there... remove the icon from the panel and use Thunderbird (or whatever) instead. Evolution will take up a tiny amount of your hard drive, but you won't break Gnome.

+1

I have SeaMonkey installed. Using it's mail side as default mail. I forgot Evolution was even in Ubuntu until I saw this thread.

---

### Post by fragos on 2009-12-29
You'll want to set the System-> Preferences-> Preferred Applications to insure your email package of choice is used for mailto:. The Clock applet in the upper right hand side uses Evolution for calendar display. You can safely remove it from the panel.

---

### Post by dcstar on 2009-12-30
> **snowpine said:**
> Pretend it isn't there... remove the icon from the panel and use Thunderbird (or whatever) instead. Evolution will take up a tiny amount of your hard drive, but you won't break Gnome.

Exactly, the amount of problems caused by people unnecessaryly removing Evolution is ridiculous - **just don't use it** if you don't like it.

---

### Post by FeraTech on 2009-12-30
The main packages I am reffering to are:

evolution-common
evolution-data-server-common

Also, parts of evolution are always running in the background unnecessarily.

---

### Post by Soul-Sing on 2009-12-30
When you remove evolution completely you remove (partly) the ubuntu-desktop. and your left with a broken system.
you could remove evolution but always let evolution-data-server(-common) untouched.

---

### Post by fragos on 2009-12-30
I performed the following three things to operationally replace Evolution with Gmail. The evolution code need not be removed to change mail readers.

You'll want to set the System-> Preferences-> Preferred Applications to insure your email package of choice is used for mailto:. I accomplished using Gmail instead of Evolution by setting Mail Reader to Custom and changing the command to:

gnome-open [https://mail.google.com/mail/?extsrc=mailto&url=%s](https://mail.google.com/mail/?extsrc=mailto&url=%s)

With that change Gmail also becomes my Contact list.

I also disabled "Evolution Alarm Notifier" in the Startup Applications Preferences since I'm also using Google Calendar.

The Clock applet in the upper right hand side uses Evolution for calendar display. You can safely remove it from the panel. I left it there and configured Evolution to sync with Google Calendar. My use of Evolution is limited to the display of this months calendar with days with appointment displayed in bold. Clicking a particular day displays the appointment for that day. I make use the Google Calendar to set events.

---

### Post by dcstar on 2009-12-31
> **FeraTech said:**
> The main packages I am reffering to are:

evolution-common
evolution-data-server-common

Also, parts of evolution are always running in the background unnecessarily.

Perhaps if you weren't still using 6.10 then this would change?

In a 9.10 system the only Evolution background process running uses no CPU and a measly 3.1 GiB if RAM - which will get moved to swap if necessary.

---

