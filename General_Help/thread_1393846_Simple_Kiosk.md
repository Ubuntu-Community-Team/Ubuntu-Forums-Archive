---
title: "Simple Kiosk"
date: 2010-01-29
forum: General Help
---

### Post by rthawkcom on 2010-01-29
Trying to build a simple internal use kiosk using Lucid Lynx Server.  Security is NOT a concern since only 1 person will use it.  I want to boot up, run X and run firefox. No GUI.  That's it!  But I can't figure out where to do this.

Here is what I am doing so far:

sudo apt-get install hal
sudo apt-get install xorg
sudo apt-get install alsa-utils  *required for sound
sudo apt-get install firefox

sudo chmod +s /sbin/shutdown   **allow anyone to shut down
sudo dpkg-reconfigure x11-common  **allow anyone to run X

sudo vi /etc/rc.local
    - setterm -powersave off -blank 0  **turn screen saver off
    - startx 2>&1

sudo vi /etc/X11/xinit/xinitrc ** have X session start firefox
    -/usr/bin/firefox -width 1280 -height 1024 

My problem is getting Lucid to startx so that x can kick off firefox.  If I ALT+F1 in and run it, it works great, but how can I have it automatically kick off without having to open up a terminal?

---

### Post by texaswriter on 2010-01-31
Why don't you just use those like same options with the desktop version. If you are worried about all the other things installed, look for an alternate install disk [usually light] or a disk that specifically says minimal install. I think Ubuntu has such disk.

---

### Post by rthawkcom on 2010-01-31
I tried that already.  It did work, but over time Firefox would slow down a lot.  I ran Top and noticed that it wasn't playing nice with the desktop, so my only option is to remove the desktop out of the picture.  There was also another problem with the desktop not allowing the monitor to go into full 1280x1024 resolution.  The server edition I am running now doesn't have this limitation, nor is it causing any problems with firefox, so, I firmly believe the server edition is the way to go on this.

Thanks for your input!

---

### Post by texaswriter on 2010-01-31
Hrrm, could you describe in as much detail as you can how the desktop would cause problems [I'm assuming you mean GNOME] and exactly how you found this out. 

That might help some, also if others can see it. 

I've used Firefox for months in desktop in Debian and Ubuntu and haven't noticed anything like this. 

If you are worried about performance, lol, try wine+firefox

[http://www.tuxradar.com/content/browser-benchmarks-2-even-wine-beats-linux-firefox](http://www.tuxradar.com/content/browser-benchmarks-2-even-wine-beats-linux-firefox)

Otherwise, I might recommend rolling back to a different version of Firefox [what version are you running]... or, additionally, 
> 
**Just shows how much Mozilla**

Anonymous Penguin (not verified) - February 12, 2009 @ 6:48pm
Just shows how much Mozilla are bothering with optimization of the Linux build, I guess.
 
 **It's the compiler, stupid.**

Anonymous Penguin (not verified) - February 12, 2009 @ 10:28pm
Recompile Firefox with the Intel ICC compiler and rerun the test.
 
 **Re: It's the compiler, stupid.**

Anonymous Penguin (not verified) - February 13, 2009 @ 9:06am
NO! The whole *POINT* of this is that people *DON'T* recompile Firefox - the just use the one from their distro. If Linux performance is dragging behind because we use GCC, then this problem is much MUCH larger than just Firefox. 

---

### Post by rthawkcom on 2010-01-31
This isn't just a simple web surfing configuration.  The program I wrote uses the web browser as a front end.  It runs  XHTML 1.0 strict and makes heavy use of AJAX with threads firing every 5 seconds.  I can only use Firefox 3.6 due to all the bugs I found in 3.5.7.  (Yes, Firefox is being abused badly here, but its the only browser I found that works correctly.)  The desktop is getting in the way and definitely must go, not even to mention the display problem.

I feel we are getting side tracked here.  I'm not really interested in repairing what I have now.  I just want to get the new server edition working as is.  Lucid Lynx is slated for LTS, so this is another important issue.

I am confident that what I am asking is simple, I just don't know how to do it.  I only need to know how to modify Lucid such that it can boot up and run the "startx" command without me having to do ALT+F1 first.  I've already done everything else to get it running, including it to log in automatically.

---

### Post by amac777 on 2010-01-31
Does adding "startx" to the bottom of the .bashrc file in your home directory work?

---

### Post by rthawkcom on 2010-01-31
It booted up and hung.  When I hit F2 it went into Firefox just fine.  When I rebooted again, nothing works.  I must have messed something else up.

I'm going to reinstall fresh and try starting it that way.  I'll post back what I find.

---

### Post by rthawkcom on 2010-02-01
Interesting.  I can't bring up a terminal now.  When I hit ALT+F1 it just streams out:

^@^@^@^@^@^@^@^@^@^@^@^@^^@

all over the screen.  CTRL+ALT+DEL still works, but it is not launching a terminal.  I thought it was something I did. So I reinstalled, but the same thing happened.  In order to verify the computer was ok, I ghosted on a windows image and booted up just fine.   Yet when I re-installed Lucid, same thing.  I'm wondering if they just recently changed something in one of the files it downloads and broke something?

I tried to do ALT+PrintScn+K and then it throws out:

Kernal Panic - not syncing: Attempted to kill init!
*ERROR* Panic occurred, switching back to text console

Then the whole thing locks up.

---

