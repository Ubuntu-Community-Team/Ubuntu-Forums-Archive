---
title: "KUBUNTU SLOW!!! - Disabling running services, to free more RAM?"
date: 2006-06-04
forum: General Help
---

### Post by daller on 2006-06-04
Hi There,

I'm trying to get kubuntu running smoothly on an Intel P4 machine.

It's specs:

1700 Mhz
128 MB RAM
40 GB HDD

My problem is that KDE is really SLOW!!! (And very slow boot!)

It may be the amount of RAM???

It runs alot of things I don't use:

CUPS - I don't print from that pc.
Bluetooth - I don't use bluetooth on that pc.

How do I disable those? - And what else?

The goal is a quick boot, and a decent speed in KDE!

---

### Post by meng on 2006-06-04
Is this the first time you've run KDE on your machine? I wonder if it's going to be slow anyway given your specs. Perhaps you'd be better off with a lightweight window manager rather than a heavy desktop environment.

But, you could try installing and running sysv-rc-conf to specify which services start at which runlevels. For example, disable bluez-utils and cupsys.

---

### Post by Alex_Perry on 2006-06-04
Here's a few tips off the top of my head. By the way, I'm running Kubuntu Dapper on a Celeron 500mhz, 300mb RAM and a TNT2 with no problems.

- Disable startup services with sysv-rc-conf (there's help using it on the forum)
- Prelink, then add 'KDE_IS_PRELINKED=1' to /etc/environment
- Also, add 'KDE_NO_IPV6=1' to /etc/environment
- Configure hdparm for your drive(s)
- add 'RENDER' to xorg.conf
- Use plastik/lipstik for style/windec (They seem faster than others such as QTcurve)
- If using ext3, enable dir_index, 'sudo tune2fs -O dir_index /dev/hda#'
- disable GUI effects, under 'Settings >> Appearance >> Style'
- Disable Arts, under 'Settings >> Sound and Multimedia >> Sound System'
- compile a kernel with Con Kolivas' (sp?) patch.

For more reading...
[http://wiki.kde.org/tiki-index.php?page=Performance%20Tips]("http://wiki.kde.org/tiki-index.php?page=Performance%20Tips")
[https://wiki.ubuntu.com/KubuntuOptimization]("https://wiki.ubuntu.com/KubuntuOptimization")
[http://wiki.debian.org/LinuxSpeedup]("http://wiki.debian.org/LinuxSpeedup")

---

### Post by taurus on 2006-06-04
You only have 128MB of RAM and you want to run KDE and expect it to be fast!!!  Try fluxbox...

---

### Post by oobuntoo on 2006-06-04
What kind of graphic card you have? I'm using nvidia card and it was slow until I installed and use "nvidia" driver.

---

### Post by eqisow on 2006-06-04
The suggestions so far are good, and I don't really have anything else to add.

However, if things are still too slow after these tweaks, you could always try Xubuntu. (which runs XFCE)

---

### Post by risbac on 2006-06-04
For this kind of processor, you don't have enough RAM I think. If it's not a laptop, go for 256 more Mo, you won't regret. If it's a laptop and you find the Ram too expensive, then KDE is clearly not the best solution, Xubuntu would be a better choice.

---

### Post by daller on 2006-06-04
[QUOTE=oobuntoo]What kind of graphic card you have? I'm using nvidia card and it was slow until I installed and use "nvidia" driver.[/QUOTE]

I'm not using any 3D-effects...

Will installing the proprietary drivers help ME?

---

### Post by daller on 2006-06-04
[QUOTE=eqisow]The suggestions so far are good, and I don't really have anything else to add.

However, if things are still too slow after these tweaks, you could always try Xubuntu. (which runs XFCE)[/QUOTE]

No offense, but does XFCE have nice styles?

It's for a SHOWROOM-machine, and has to look nice...

I've had a guy write me an application in Kdevelop designer / vim

Can I make it look the same on XFCE?

...Running Kubuntu seems like an overkill to me too! - But I need the themes/styles/"whatever-all-that-eyecandy's-called" to make the app look nice!

BTW: The ordinary users NEVER see the underlying desktop environment!

EDIT: Can I install XFCE on my Kubuntu-system without messing it up? - And load it through kdm?

---

### Post by shamrock_uk on 2006-06-04
[QUOTE=daller]I'm not using any 3D-effects...

Will installing the proprietary drivers help ME?[/QUOTE]

Yeah, it'll often help with things like video playback and even 2d window drawing speed.

---

### Post by eqisow on 2006-06-04
Yes, Qt (KDE apps use Qt) will look the same under XFCE. You should still be able to install themes via the theme manager if you simply install XFCE on the existing Kubuntu install. (Which works just fine, btw)

Also, the propriatary drivers aren't just for 3D. They are faster at 2D rendering as well. See the wiki on [installing nVidia drivers]("https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia") for more info.

Edit: I would just install xfce4 and not the entire xubuntu-desktop package, since you are keeping Kubuntu.

Edit again: Actually, fluxbox would probably be even faster. XFCE is nicer, imo, but if users will never see the desktop, it doesn't matter.

---

### Post by Denta on 2006-06-04
The problem lays guaranteed in your lack of RAM, add a stick of 128 or 256 and things will fly.

---

### Post by shamrock_uk on 2006-06-04
Make sure you're not running a generic i386 kernel either - check you're running one appropriate to a P4 as the jump from i386 makes a significant difference in general speed.

---

### Post by daller on 2006-06-04
[QUOTE=shamrock_uk]Make sure you're not running a generic i386 kernel either - check you're running one appropriate to a P4 as the jump from i386 makes a significant difference in general speed.[/QUOTE]

Seems like a nice "solution"!

And what would that be? linux-686?

---

### Post by daller on 2006-06-04
[QUOTE=eqisow]Yes, Qt (KDE apps use Qt) will look the same under XFCE. You should still be able to install themes via the theme manager if you simply install XFCE on the existing Kubuntu install. (Which works just fine, btw)

Also, the propriatary drivers aren't just for 3D. They are faster at 2D rendering as well. See the wiki on [installing nVidia drivers]("https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia") for more info.

Edit: I would just install xfce4 and not the entire xubuntu-desktop package, since you are keeping Kubuntu.

Edit again: Actually, fluxbox would probably be even faster. XFCE is nicer, imo, but if users will never see the desktop, it doesn't matter.[/QUOTE]

It's not nvidia! - Think it's intel... Something onboard!

Will installing "xfce4" add an entry in kdm? - So that starting xfce is easy?

---

### Post by eqisow on 2006-06-04
> And what would that be? linux-686?

Yes

> Will installing "xfce4" add an entry in kdm? - So that starting xfce is easy?

Yes, and so will fluxbox, for that matter.

---

### Post by eqisow on 2006-06-04
For Intel drivers:

Run the following command:
```

cat /etc/X11/xorg.conf | grep i810
```

It should return something along the lines of **Driver "i810"**.

If it does, you have the right drivers already. If it doesn't return anything, then run the following:

```
sudo dpkg-reconfigure xserver-xorg
```

Choose the "Automatically detect your video card" option, and make sure it chooses i810 when it ask you to select a driver. Then accept the defaults for the remaining questions, excluding the part where it asks you about video modules to load. Make sure "dri", "glx" and "GLCore" are enabled. Then continue on through, and once it finishes, hit <Ctrl +Alt + Backspace> to restart the X server. If it doesn't restart, type

```
startx
```

*Note: You have to use the Spacebar to select options when doing **dpkg-reconfigure xserver-xorg**, Enter confirms these choices.*

---

### Post by coolclassic on 2006-06-04
To make any big difference in the speed of your computer is to install more ram I would recommend increasing it to 512mb as this will be enough to stop using swap.

My system is Identical to yours appart from the ram and it flies along nicely using  3d games ect.

---

### Post by daller on 2006-06-04
[QUOTE=coolclassic]To make any big difference in the speed of your computer is to install more ram I would recommend increasing it to 512mb as this will be enough to stop using swap.

My system is Identical to yours appart from the ram and it flies along nicely using  3d games ect.[/QUOTE]

If xfce or fluxbox doesn't solve my speed-issue, I will probably buy a 512MB RAM module! - But IMO, it's a waste of money, if xfce solved it anyway!

---

### Post by s3ppel on 2006-06-04
I strongly suggest to go with more RAM, 512 MB is cheap and  will defenitely solve all your speed issues.  128 MB just doesnt cut it any longer for full-featured desktop envoironments with multiple applications running - to much swapping to the swap space occurs and slows the system down. XFCE or Fluxbox can help a little, but i suppose even with such a light window manager u will still be bottlenecked by your RAM once you open multiple programms. It doesn't need to be the fastest RAM though, it should just match your FSB / memory channel speed, but doesn't need any fancy CAS / RAS Latencys.

---

### Post by eqisow on 2006-06-04
All the poor guy wants to do is run ONE app for a showroom machine. Nothing else.  It's not for his personal use and nobody will be running anything else or even looking at the desktop. Stop telling him to go spend money that he may not have to spend.

---

### Post by moopere on 2006-06-05
[QUOTE=shamrock_uk]Make sure you're not running a generic i386 kernel either - check you're running one appropriate to a P4 as the jump from i386 makes a significant difference in general speed.[/QUOTE]

Got any numbers to back up this assertion?

I did some bench's several months ago (posted here in the forums) using the kolivas interactivity benchmark - I certainly couldn't see any difference from staring at the numbers between an i386 and an i686 kernel except when using an smp kernel on an smp machine.

Now that dapper has 686 smp default kernels (no UP kernels any more except for the i386 type) if the OP has a HT or Dual Core I'd expect to see a difference, though I should point out that I doubt it would be a 'significant' difference.

There are good reasons to use a 686 compiled kernel (or the AMD equiv), but as far as I could see via benchmarks, outright interactivity speed isn't one of them (tight loop number crunching might be one, easy access to >1GB RAM is another).

Sorry, just had to add my 2c worth as changing away from an i386 kernel is probably the most often cited 'fix' for speed problems, yet I've yet to see anyone come back to the forums with actual numbers after a kernel change proving the speed improvment (as opposed to empirical...oh yeah, it feels faster now)

Cheers,
Craig

---

### Post by aysiu on 2006-06-05
I'm with Craig on this one.

To the OP, you may want to try ```
sudo aptitude update
sudo aptitude install kpersonalizer
kpersonalizer
``` and choose fewer effects (keep the background image, though).

You may also want to try ```
sudo aptitude update
sudo aptitude install gksu bum
gksudo bum
``` and disable all the services you don't want (Bluetooth, etc.).

Honestly, though, no matter what you do to make KDE faster on 128 MB of RAM, it's going to be slow if you have more than two applications running at the same time. Even XFCE will be slow if you have four or more applications running simultaneously on 128 MB or RAM.

If you want to impress people (you said it's a showroom?), then you need to upgrade your RAM. That's the only real solution.

---

### Post by coolclassic on 2006-06-05
[QUOTE=daller]

 - But I need the themes/styles/"whatever-all-that-eyecandy's-called" to make the app look nice!

[/QUOTE]

[QUOTE=eqisow]
  All the poor guy wants to do is run ONE app for a showroom machine. Nothing else. It's not for his personal use and nobody will be running anything else or even looking at the desktop. Stop telling him to go spend money that he may not have to spend.
[/QUOTE]

Daller kneeds the ram to run the eyecandy.

---

### Post by onesojourner on 2006-06-05
I would double your ram. you could prob do it for 10 bucks if you get a used stick from a local computer store. 128 is super low.

---

### Post by daller on 2006-06-05
Thank you all for your replies!!!

I'll probably go for xfce (over fluxbox because xubuntu offers a easy installation, etc...), and if that doesn't help, I'll buy a stick of 128MB RAM!

About xfce4, I installed that (on top of kubuntu), and when logging in, it looks really ugly (green vertical stripes), and the panels are gone!
...Any suggestions on that issue? - Should I install xubuntu-desktop, or would that populate the menu in kde?

---

### Post by daller on 2006-06-05
[QUOTE=coolclassic]Daller kneeds the ram to run the eyecandy.[/QUOTE]

The standard theme/style in xubuntu is more than nice enough for me!

---

### Post by daller on 2006-06-06
The theme/style in xubuntu is REALLY nice!

Problem is, the app doesn't use that theme/style!

Since it's qt? - Made in Kdevelop designer?

What can I do to fix it?

---

### Post by daller on 2006-06-06
Guess it a gtk/qt crossover problem...

Installing "gtk2-engines-gtk-qt" solved that!

Xfce runs damn fast on this machine! :D

I WOULD like the app to use xfce's style/theme, though - I looks better than KDE's, IMHO :D

---

### Post by drtvasudevan on 2006-06-09
[QUOTE=daller]

EDIT: Can I install XFCE on my Kubuntu-system without messing it up? - And load it through kdm?[/QUOTE]
sure you can. see this thread
[http://ubuntuforums.org/showthread.php?t=188679&highlight=aptitude](http://ubuntuforums.org/showthread.php?t=188679&highlight=aptitude)

tv

---

### Post by unf on 2006-06-09
If kde is compiled with "kdeenablefinal" it will use all the memory that is avaible I have 1024mb and it is using 950mb (in gentoo so its only a guessing).

---

