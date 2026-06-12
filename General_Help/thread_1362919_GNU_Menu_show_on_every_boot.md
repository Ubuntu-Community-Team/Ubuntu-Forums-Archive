---
title: "GNU Menu show on every boot"
date: 2009-12-23
forum: General Help
---

### Post by generator85 on 2009-12-23
Since a little while, when I start my computer I get the GNU GRUB menu. I'm using my PC as a HTPC, so this is very annoying. I've tried editing etc/default/grub, but the changes aren't reflected in the menu. I have to manually select an option every time, there is no timer or anything.

I shut down my computer using the menu, so this can't be the problem right?

Another problem is that my deamons don't start at boot anymore (ssh, sabnzbd, netatalk). Maybe this has something to do with it? (Or maybe someone knows how to fix this).

---

### Post by Jose Catre-Vandis on 2009-12-23
Sounds like you are using grub2.

Have you run **sudo update-grub2** after making your changes?

/etc/default/grub has these settings as default:
```
GRUB_DEFAULT=0
GRUB_TIMEOUT=10
```

Also check out the grub2 howto in tutorials for more info on the inner workings of grub2

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by generator85 on 2009-12-23
Yes I've run **sudo update-grub2. **And the settings are set to the default values. I've read the website you linked to, but I couldn't find anything that could lead to a fix.

I've just been using Linux for 2 weeks, so I don't really know where to look, except for Google.

---

### Post by Jose Catre-Vandis on 2009-12-24
So lets understand this a bit more:

Your PC boots up, and presents the grub screen.

Does it then, after 10 seconds, boot the default option, or does it just stay there doing nothing, until you press enter?

If it does boot up the default option then everything is working, if it doesn't and you have to select (up/down arrow) and press Enter to get things going then something is wrong.

What/How many other choices are in your grub menu?

Is the partition / hard drive setup straight forward or complicated?

You could try reinstalling or reconfiguring grub:

```
sudo grub-install /dev/sda

or

sudo dpkg-reconfigure grub-pc
```

which might clear out any gremlins.

---

### Post by Leppie on 2009-12-24
check [this bug report]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420077"). seems you're not the only one with this problem.

---

### Post by generator85 on 2009-12-24
@Jose: It does nothing untill I press Enter. I can choose between 8 options (3x Ubuntu, 3x Ubuntu Recovery and 2 memtests). Ubuntu starts normally when I choose an option and press enter.
I've got 2 HDD's.  As far as I know everything is mounted as normal (though this is the first time I ever installed Ubuntu). The second HDD is mounted as mnt.

I'll try reinstalling It when I get home.

@Leppie: Thanks for the link. That looks like the same problem I'm having. I'll try some of the fixes mentioned in the report this evening.

---

### Post by generator85 on 2009-12-24
Unfortunatly reinstalling and reconfiguring didn't fix it for me :(

---

### Post by generator85 on 2010-01-08
After weeks of searching i've finally found the reason why everything stopped working:

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/500520](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/500520)

Apparently it's a bug in upstart, and it can be fixed by downgrading it:
- Go to Synaptics Package Manager and find upstart
- Go to the Package menu item and click Force Version
- Choose 0.6.3-10 and click Apply
- Choose  "Lock Version" in the Package menu item

This fixes both of my problems (the init.d services not starting, and the Grub menu)

Very frustrating that 1 update caused all this trouble. It took me quite some time to find the solution.

---

