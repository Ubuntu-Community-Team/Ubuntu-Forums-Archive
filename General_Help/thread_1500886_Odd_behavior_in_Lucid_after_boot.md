---
title: "Odd behavior in Lucid after boot"
date: 2010-06-03
forum: General Help
---

### Post by cscj01 on 2010-06-03
I upgraded to Lucid from Karmic a few weeks ago.  The upgrade went fine.  Then I decided to move my exit, maximize, and minimize buttons to the right side.  I used Ubuntu Tweak to do this.  Since that time I have very odd behavior after I boot Lucid.

The booted system comes up with an X for a cursor.  There are no exit, maximize, and minimize buttons on my window bar.  Finally, I can open a terminal, but cannot type anything in it.

Sometimes I can get things back to normal by using Ubuntu Tweak to move the buttons to the left or right (depending on where they were before the boot).  Sometimes I have to open System>Preferences>Appearance> and change Visual Effects from None to Normal or vice versa.

I have tried metacity --replace (after getting the terminal window to allow me to type in data), but after I reboot, things are back the way they were.

Does anyone have a suggestion as to what I can look for to resolve this?  I have an Nvidia GeForce 7300 LE on board graphics card, and I am using the Nvidia current version driver.  When things are working correctly, System Monitor shows a compiz process running but not a metacity process.  Is this correct?

---

### Post by cscj01 on 2010-06-04
I have just found that whenever I have to boot Lucid, the "Visual Effects" setting in System > Preferences > Appearance is reset to "None".  Now, if I set that to "Normal" my bars and icons return.  Additionally, I can type data into a terminal session.

Why would the Visual Effects setting be changed by booting Lucid?  Is there a configuration file I can check for this behavior?

---

### Post by JOZeldenrust on 2010-06-04
> **cscj01 said:**
> I have just found that whenever I have to boot Lucid, the "Visual Effects" setting in System > Preferences > Appearance is reset to "None".  Now, if I set that to "Normal" my bars and icons return.  Additionally, I can type data into a terminal session.

Why would the Visual Effects setting be changed by booting Lucid?  Is there a configuration file I can check for this behavior?

I have the same problem. See:

[http://ubuntuforums.org/showthread.php?t=1501308](http://ubuntuforums.org/showthread.php?t=1501308)

(not a solution, just a more detailed description of what goes wrong)

---

### Post by Bobulous on 2010-06-08
Can you take a look at my post about this:

[http://ubuntuforums.org/showthread.php?t=1503160](http://ubuntuforums.org/showthread.php?t=1503160)

I'm trying to work out whether the steps I tried work for other people, or if it's just a coincidence that Metacity now runs automatically for me.

---

### Post by cscj01 on 2010-06-08
>  Can you take a look at my post about this:

[http://ubuntuforums.org/showthread.php?t=1503160](http://ubuntuforums.org/showthread.php?t=1503160)

I'm trying to work out whether the steps I tried work for other people, or if it's just a coincidence that Metacity now runs automatically for me.

I have run ```
rm ~/.config/gnome-session/saved-session/*
``` to see if that alone will fix the problem.  I'll let you know when I reboot.

---

### Post by cscj01 on 2010-06-08
Well, it certainly works on the first reboot.  We'll see if the problem reappears.  Thanks for your reference.

Edited: 09 Jun 2010

I have rebooted a number of times and things seem to be correct.  I believe step 3 was all that was required.

---

### Post by Bobulous on 2010-06-10
Looks like Bernhardt is a genius. Hopefully the Ubuntu development are aware of this oversight, so it doesn't happen again.

Now I just need to figure out how to get gamma to remain stable under the open source graphics driver.

---

### Post by JOZeldenrust on 2010-06-12
> **cscj01 said:**
> I have run ```
rm ~/.config/gnome-session/saved-session/*
``` to see if that alone will fix the problem.  I'll let you know when I reboot.

What he said...

---

### Post by JOZeldenrust on 2010-06-12
> **JOZeldenrust said:**
> What he said...

I have since rebooted. The problem seems to be fixed. Thanks guys!

---

