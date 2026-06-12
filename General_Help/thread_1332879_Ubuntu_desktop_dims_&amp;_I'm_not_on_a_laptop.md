---
title: "Ubuntu desktop dims &amp; I'm not on a laptop"
date: 2009-11-20
forum: General Help
---

### Post by KingYaba on 2009-11-20
The whole desktop will darken without warning. All open windows would darken. Programs ran like normal, just dimmed. It's not the monitor it's the OS or Gnome or something. This has happened a few times in the past week and it's rather annoying because the only way to get it back to normal is to run ```
sudo /etc/init.d/gdm restart
``` which logs me out and interferes with work . 

Some info about my computer,

AMD Phenom II X4
HD 4770
Gigabyte GA-MA770T-UD3P mobo
Ubuntu 9.10 with the latest updates

The only tinkering with the system I can think of is I disabled PulseAudio because it sucked. Crackle and pop and the sound cut out. I followed the directions in this thread, [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1313253](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1313253). Do you think this is related? I could use your guys' help. 

thanks

---

### Post by sgosnell on 2009-11-20
What do you have in the power settings?  Even on a desktop, it can be set to dim after an idle period, of whatever length you select.  Open System/Preferences/Power Management and see what is there.

---

### Post by KingYaba on 2009-11-21
Just so you know, this happened when I was actively using the computer. I don't know how to recreate the dimming.

Just happened again a minute ago. I'm just typing on the keyboard. Am I unknowingly hitting a key combo to do this? New windows, this time, are displaying properly but windows already open are dimmed. Once again, a screenshot.

---

### Post by sgosnell on 2009-11-21
If you have Compiz and/or Metacity active, windows which are not responding, for whatever reason, go gray.  They should return to normal brightness when they start responding again.  It may be that, or it may be something else I've never seen.

---

### Post by KingYaba on 2009-11-24
> **sgosnell said:**
> If you have Compiz and/or Metacity active, windows which are not responding, for whatever reason, go gray.  They should return to normal brightness when they start responding again.  It may be that, or it may be something else I've never seen.

I have Compiz enabled but the entire desktop (apps included) goes gray. They are responding and function as normal. Just everything is dim. Really dim. It's happening pretty frequently, too. 

Look at the screenshot in my last post. That's what I'm talking about.

By the way, I found out at least one trigger. When I have a Terminal window open and I hit the Backspace key a bunch of times or if I hold it down for several seconds, the display will dim. Display dims randomly as well but at least I have found a way to trigger it.

---

### Post by KingYaba on 2009-11-30
> **sgosnell said:**
>  or it may be something else I've never seen.

I'm bumping this thread because it's impossible to be productive and it's aggravating me. 

Now, when I turned off the visual effects it stopped this from happening. So hopefully this can narrow down the problem. When the effects were turned on, I looked through CCSM to find the problem. I couldn't find anything.

---

