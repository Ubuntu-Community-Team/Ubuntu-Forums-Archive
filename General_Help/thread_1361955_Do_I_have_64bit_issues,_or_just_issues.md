---
title: "Do I have 64bit issues, or just issues?"
date: 2009-12-22
forum: General Help
---

### Post by Speedwagon on 2009-12-22
I keep having difficulty with things like flash, java, etc on my system.  I haven't really invested time into working on these issues, but they are irritating.  This is in 9.10.

An example of an issue: when trying to watch youtube videos, I sometimes have a hard time hitting a control.  It's like it's there, but not.  If I can manage to move the mouse around enough while clicking, I can eventually get it to work(most times).  But in general, it is just not working as good as it should.  I get the same kind of issues when listening to Pandora, even though the button might highlight, it won't do anything when I click(both Firefox and Opera do it).

Is there any advantage to going back to 32 bit anymore, for ease of use?

---

### Post by dyous87 on 2009-12-22
This seesm to be a 64 bit issue with the flash plugin, I had this issue too but there is a quick fix.

Open a terminal and type:

> gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer

The add the following line right before the last line:

> export GDK_NATIVE_WINDOWS=1

Save the file, restart all yor browsers, and now the flash plugin should allow you to click buttons with out issues.

Let me know if this works for you.

Regards,
David

---

### Post by oldos2er on 2009-12-22
> **Speedwagon said:**
> I keep having difficulty with things like flash, java, etc on my system.

 Are you using 64-bit java and flash?

---

### Post by mxc1090 on 2009-12-22
I had a lot of these issues too with 64-bit 9.10...I'm running 32-bit now and things work a little better, but I will be following this thread because I want to switch back to 64-bit.

---

### Post by dyous87 on 2009-12-22
Well I am using 64bit 9.10. The above fix got rid of the flash issue for me and I haven't had any java issues as of now.

David

---

### Post by dcstar on 2009-12-22
> **dyous87 said:**
> Well I am using 64bit 9.10. The above fix got rid of the flash issue for me and I haven't had any java issues as of now.

David

You may be using 64-bit but if you have that fix then you are using 32-bit flash.

There is a beta native 64-bit flash from Adobe that can be installed fairly easily, do a search do detailed instructions.

---

### Post by pricetech on 2009-12-22
I'm running 64 bit Hardy.  I installed 64 bit Java and the 64 bit Flash plugin.

No problems.

---

### Post by Speedwagon on 2009-12-25
> **oldos2er said:**
> Are you using 64-bit java and flash?

How does one get a 64 bit flash, when I can't seem to find such on Adobe's site?  And they say:
> Adobe Flash Player is not supported for playback in a 64-bit browser. However, you can run Flash Player in a 32-bit browser running on a 64-bit operating system.

I normally run Opera 64 bit.  I don't know how to check my current flash version, but I assume there is only a 32 bit version that is bandaided to work?

---

### Post by oldos2er on 2009-12-25
Here's a direct link for Flash: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz)

And here's info on installing it: [http://www.ubuntugeek.com/adobe-flash-player-10-for-64-bit-linux-released-and-ubuntu-installation-instructions.html](http://www.ubuntugeek.com/adobe-flash-player-10-for-64-bit-linux-released-and-ubuntu-installation-instructions.html)

For Java: [http://ubuntuforums.org/showthread.php?t=1019314](http://ubuntuforums.org/showthread.php?t=1019314)

---

### Post by Speedwagon on 2009-12-25
I'll give that a try, thanx!

---

### Post by MooPi on 2009-12-25
If your having problems try this, uninstall all previous flash plugins. Downloads this: [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz)
Extract to and copy to  ```
.mozilla/plugins/
```
Works like a charm for me every time.

---

### Post by gunksta on 2009-12-25
Just to be very clear - The flash installed via the repos is the 32-bit version and relies on the lib32 stuff. I have tried to run this on several computers and always gave up. The 64-bit native beta is much much better IMO.

---

### Post by Speedwagon on 2009-12-29
I tried the 64bit flash, and I didn't have much luck.  Either I did it wrong, or it doesn't work right.

Either way, I just got done re-installing Ubuntu 9.10 32-bit, added flash and Java, and it is working soooooo much better now than it ever did for me in 64 bit.  I choose less effort, more working for now.  I have so many other projects that require my attention, I don't want my computer to be one of them.  Thanx for the help everyone.

---

