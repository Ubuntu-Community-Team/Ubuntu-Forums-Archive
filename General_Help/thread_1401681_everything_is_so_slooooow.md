---
title: "everything is so slooooow"
date: 2010-02-08
forum: General Help
---

### Post by pinnacle2009 on 2010-02-08
I had this problem fixed the first time I had Ubuntu, but cannot remember how I did it. Something about changing some values in the internet browser.

And another question, the only thing I really do with this desktop is play games. Mostly browser games. I was wondering what I could upgrade to help them run smoother and with less lag.

I have a Dell Inspiron 531. Everything is stock. It has 2gigs of ram. If there is anything else that needs answering before my question can be answered, ask away. I just don't have time to look for specifics; I wanted to get this posted before I went in to class.

---

### Post by Cabs21 on 2010-02-08
1: did you update your drivers to support your graphics card?
2: what browser are you using to play games?
3: did you install some version of flash?
4: 64-bit OS or 32-Bit? (guessing 32-bit)
5: What kind of internet connection are you using and how strong is the signal?

---

### Post by pinnacle2009 on 2010-02-08
> **Cabs21 said:**
> 1: did you update your drivers to support your graphics card?
2: what browser are you using to play games?
3: did you install some version of flash?
4: 64-bit OS or 32-Bit? (guessing 32-bit)
5: What kind of internet connection are you using and how strong is the signal?

1. I did a system update, but I didn't do that specifically. How would I go about that?

2. Chrome

3. I thought I did, but after looking, I only installed Java. I'll get on that after class.

4. 32-bit

5. Wireless, connection is generally 65%+. We have Windstream if that matters at all.

---

### Post by Cabs21 on 2010-02-08
Drivers are in SYSTEM>ADMINISTRATION>HARDWARE DRIVERS

you need to be connected to the internet to update these.  Also without flash properly installed your browser may crash and or lag like crazy.  So follow the instructions closely for flash 32-bit.  32-bit flash is not to bad so dont worry, 64-bit is the real pain in the *** if you screw up.

---

### Post by Alex Libman on 2010-02-08
[LIST]
[*]Use a utility like [EnvyNG]("http://en.wikipedia.org/wiki/Envy_%28software%29") (which also comes with a Qt GUI) to see if it recommends a different video card driver.  If the changes recommended by envyng don't work, you can run it in console mode to undo.  (Newer versions of Ubuntu might have something better, I'm not sure.)
[/LIST]

[LIST]
[*]After installing the recommended video card driver and rebooting, run `glxgears` from shell with no other major programs running, maximize it, give it a few seconds, and post your FPS.  If your video card is old or poorly supported by Linux then you should probably disable compiz and any other fancy effects entirely.
[/LIST]

[LIST]
[*]Run `top`, press '>' several times to move the sorting column selection to CPU Time, and see what your computer spends the most of its CPU time on.  You can list your most CPU / memory hungry processes here, and there can be some additional steps you can take depending on what they are.
[/LIST]

[LIST]
[*]Also in `top`: if you see a lot of your swap space being used then [adding more]("http://ubuntuforums.org/showthread.php?t=1042946") might help.
[/LIST]

[LIST]
[*]Disable any [daemons]("http://en.wikipedia.org%3Cbr%20/%3E%0A/wiki/Daemon_%28computer_software%29") you don't need.  I personally prefer the `sysv-rc-conf` utility to uncheck all run levels.
[/LIST]

[LIST]
[*]Try disabling some or all of your Web browser add-ons to identify if any of them use too much CPU or RAM (possibly due to a bug, which is especially likely with Chrome as many of its add-ons are still in beta).
[/LIST]

[LIST]
[*]As a last resort, if your computer itself is too slow for the default Ubuntu desktop, switching to [Xubuntu]("http://en.wikipedia.org/wiki/Xubuntu") (which uses [Xfce]("http://en.wikipedia.org/wiki/Xfce") instead of Gnome) or even [Lubuntu]("http:.net//en.wikipedia.org/wiki/Lubuntu%22") (which uses [Openbox]("http://en.wikipedia.org/wiki/Openbox")) may be your best option.  You can still use any Gnome components that you especially miss (ex. gedit, nautilus, etc).  There are also [Linux distros that are optimized for slower computers]("http://en.wikipedia.org/wiki/Mini_Linux") in all their components, including the kernel.
[/LIST]

---

### Post by pinnacle2009 on 2010-02-08
> **Alex Libman said:**
> [LIST]
[*]Use a utility like [EnvyNG]("http://en.wikipedia.org/wiki/Envy_%28software%29") (which also comes with a Qt GUI) to see if it recommends a different video card driver.  If the changes recommended by envyng don't work, you can run it in console mode to undo.  (Newer versions of Ubuntu might have something better, I'm not sure.)
[/LIST]

[LIST]
[*]After installing the recommended video card driver and rebooting, run `glxgears` from shell with no other major programs running, maximize it, give it a few seconds, and post your FPS.  If your video card is old or poorly supported by Linux then you should probably disable compiz and any other fancy effects entirely.
[/LIST]

[LIST]
[*]Run `top`, press '>' several times to move the sorting column selection to CPU Time, and see what your computer spends the most of its CPU time on.  You can list your most CPU / memory hungry processes here, and there can be some additional steps you can take depending on what they are.
[/LIST]

[LIST]
[*]Also in `top`: if you see a lot of your swap space being used then [adding more]("http://ubuntuforums.org/showthread.php?t=1042946") might help.
[/LIST]

[LIST]
[*]Disable any [daemons]("http://en.wikipedia.org%3Cbr%20/%3E%0A/wiki/Daemon_%28computer_software%29") you don't need.  I personally prefer the `sysv-rc-conf` utility to uncheck all run levels.
[/LIST]

[LIST]
[*]Try disabling some or all of your Web browser add-ons to identify if any of them use too much CPU or RAM (possibly due to a bug, which is especially likely with Chrome as many of its add-ons are still in beta).
[/LIST]

[LIST]
[*]As a last resort, if your computer itself is too slow for the default Ubuntu desktop, switching to [Xubuntu]("http://en.wikipedia.org/wiki/Xubuntu") (which uses [Xfce]("http://en.wikipedia.org/wiki/Xfce") instead of Gnome) or even [Lubuntu]("http:.net//en.wikipedia.org/wiki/Lubuntu%22") (which uses [Openbox]("http://en.wikipedia.org/wiki/Openbox")) may be your best option.  You can still use any Gnome components that you especially miss (ex. gedit, nautilus, etc).  There are also [Linux distros that are optimized for slower computers]("http://en.wikipedia.org/wiki/Mini_Linux") in all their components, including the kernel.
[/LIST]

When maximized, glxgears showed an average of 440 frames per 5 secs.

I could not get sysv-rc-conf to work. I installed it, but it would not run.

5847620k was my swap space.

Nvidia installed through envyng

---

### Post by Alex Libman on 2010-02-09
Your hardware, video driver, and swap clearly aren't a problem then.

Could you describe in more detail what exactly is slow - just the Web browser or the rest of the OS as well?  Are only some Web-sites slow while the rest are normal?  If you try the abnormally slow pages in different browsers (Firefox, Chrome, Opera), are they all abnormally slow?

You run `sudo sysv-rc-conf` from shell, but you first need to know if you need to disable any of your daemons, which is why I asked you to look at your `top` output sorted by CPU Time.

Also, where do you get your Chrome / Chromium build?

---

### Post by pinnacle2009 on 2010-02-09
> **Alex Libman said:**
> Your hardware, video driver, and swap clearly aren't a problem then.

Could you describe in more detail what exactly is slow - just the Web browser or the rest of the OS as well?  Are only some Web-sites slow while the rest are normal?  If you try the abnormally slow pages in different browsers (Firefox, Chrome, Opera), are they all abnormally slow?

You run `sudo sysv-rc-conf` from shell, but you first need to know if you need to disable any of your daemons, which is why I asked you to look at your `top` output sorted by CPU Time.

Also, where do you get your Chrome / Chromium build?

How do I tell what the CPU usage is measuring? (What "daemon"?) I am still very new, so please bear with me. lol

In Firefox and Chrome, all the websites are pretty slow. I haven't tried any other browsers besides those, but I will give Opera a try and let you know how that goes.

I downloaded Chrome from the Google website.

And it seems to be just internet, although, I really don't use anything else, so I really couldn't say if its the whole OS or not. I will run a couple of different programs and find out this week.

---

### Post by wojox on 2010-02-09
If your using 9.10 see her: [http://wojox.homelinux.net/?p=4](http://wojox.homelinux.net/?p=4)

Firefox see here: [http://wojox.homelinux.net/?p=33](http://wojox.homelinux.net/?p=33)

---

