---
title: "if I install 2.6.15 from kernel.org will I go to hell?"
date: 2006-02-28
forum: General Help
---

### Post by svref on 2006-02-28
Sorry 2.6.12, you're just not up-to-date enough for me.  I'm wondering what the recommended way to get 2.6.15 is?  I could bag the latest stable from kernel.org.  That wouldn't have the ubuntu patches in it, would that be Bad?  If Bad, how do I get the "working set" of patches for 2.6.15?

---

### Post by zachtib on 2006-02-28
id say just upgrade to dapper.  its pretty stable now, probably more stable than building your own kernel (i would assume)

---

### Post by RAOF on 2006-02-28
The wiki has a good guide to building a kernel the Ubuntu way: [https://wiki.ubuntu.com/KernelHowto](https://wiki.ubuntu.com/KernelHowto)

I'm not sure if the new kernel will work for your Breezy install.  I seem to remember devfs support being dropped, or something, so only udev works.  I can't remember if Breezy uses udev, though.  That might be something to look out for.

Finally, some generic disuasive "why do you want a new kernel" talk:

Unless the new kernel supports something that you need that the Ubuntu kernel doesn't, it's really not worth your while.  Security patches are backported to the current Ubuntu kernel.

If, however, you just want to mess around, I'd recommend upgrading to Dapper - you get the shiny new 2.6.15 kernel, Gnome 2.14, and a bunch of other stuff :)

---

### Post by patrickfromspain on 2006-03-01
about the ubuntu patches... I use a compiled 2.6.12 from kernel.org with no problems (at the moment.. jeje).

---

### Post by dcstar on 2006-03-01
[QUOTE=RAOF]
.......
If, however, you just want to mess around, I'd recommend upgrading to Dapper - you get the shiny new 2.6.15 kernel, Gnome 2.14, and a bunch of other stuff :)[/QUOTE]
For those of us too lazy to look at the main Ubuntu site (like me), just when is the "official" Dapper release date?

---

### Post by pinguinus on 2006-03-01
If I remember right, there are some major differencies in dependencies between 2.6.12 and 2.6.15 kernels, so installing 2.6.15 means the need of upgrading some quite central pieces of other software too. Correct me if I'm wrong, but Ubuntu 5.10 Breezy, based on 2.6.12, still uses hotplug while distros based on 2.6.15 kernels, like Ubuntu 6.04 Dapper, don't use Hotplug at all anymore because there the hotplug functionality is now integrated into the newer udev package. So the hotplug package will be automatically removed when installing a 2.6.15 kernel.

As an example of potential problems of installing a 2.6.15 kernel: 
When using Debian testing and installing 2.6.15, I remember a time when I couldn't boot my Debian correctly anymore, the boot process just stopped to a busybox commanline screen. The only way out of that (that I could find...) was that I had to dist-upgrade all the way to Debian unstable from Debian testing, so many other central software pieces had to be upgraded too. Now the problem has gone away, however, and Debian testing is now officially using the 2.6.15 kernels only.

---

### Post by engla on 2006-03-01
well.. I built and installed 2.6.15.1 from kernel.org on breezy, without any ubuntu patches. I haven't updated any other core packages (other than usual breezy updates), and haven't had any problems with my kernel 

-- apart from the compile not working until the second try -- but did your first kernel compile work?

Edit: And yeah, why did I do it?  I need it for my wireless card [but later on the driver didn't work all they way anyway], but I also get inotify, FUSE, and a much smaller kernel [I purged it of everything and more to cut the size.]. Overall I think 2.6.15 has lots to offer for me and for laptop/desktop users.

---

### Post by engla on 2006-03-01
[QUOTE=dcstar]For those of us too lazy to look at the main Ubuntu site (like me), just when is the "official" Dapper release date?[/QUOTE]
Dapper will be Ubuntu v6.04, right?

that's 04 2006 -- April 2006

See?;  Ubuntu releases are 6 months apart, breezy is 5.10 right.

---

### Post by Gustav on 2006-03-01
I even think it's the 20th of April for the final release

---

### Post by RAOF on 2006-03-01
[QUOTE=engla]...
Edit: And yeah, why did I do it?  I need it for my wireless card [but later on the driver didn't work all they way anyway], but I also get inotify, FUSE, and a much smaller kernel [I purged it of everything and more to cut the size.]. Overall I think 2.6.15 has lots to offer for me and for laptop/desktop users.[/QUOTE]
Just for the record, Breezy's default kernel has the inotify patches backported.  You don't need a new kernel to have inotify support.

---

### Post by dcstar on 2006-03-01
[QUOTE=engla]Dapper will be Ubuntu v6.04, right?

that's 04 2006 -- April 2006

See?;  Ubuntu releases are 6 months apart, breezy is 5.10 right.[/QUOTE]
So the "moral" of that is for people to wait just a few more weeks for an officially released and supported version of Ubuntu rather than potentially dig themselves a (deep) hole experimenting with unsupported stuff in Breezy right now......

---

### Post by svref on 2006-03-02
Sorry, but responses like that make me kinda angry, because you're effectively saying "essential broken hardware shouldn't be fixed by the users.".

In my case we're dealing with G3 ibook and airport card, perhaps THE best selling laptop of all time. Its like 3-4 years old, not bleeding edge.  I'm shocked, SHOCKED, that Linux as of 4 months ago is so far behind the times that simply *closing* the laptop causes a system lockup, and that the airport is not fully functional.

Of course its not your fault, so I shouldn't be mad at you.  But I think your calculus of "don't dist-upgrade, just wait", should be revised to "dist-upgrade iff the *borkenness of your current system&#8804; the expected borkenness of Breezy*".  With 50 days to release, that was a relatively simple calculation, favoring Breezy dist-upgrade.  Who knows, maybe everything will break in the next 50 days, and I'll wish I had my crash-on-close, non-wifi-functional laptop back.  But I doubt it.

---

