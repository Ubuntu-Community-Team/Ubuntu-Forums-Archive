---
title: "Update broke graphics drivers and mouse support."
date: 2010-10-05
forum: General Help
---

### Post by kazza765 on 2010-10-05
Hi.

I'm running Ubuntu 10.04 on an Apple iMac 27". After updating yesterday, I no longer have working graphics drivers or a working mouse. The graphics card in question is an ATI HD 5750, and mouse is an Apple bluetooth 'magic' mouse.

So far I've managed to fix the mouse, but not the graphics.

At first I didn't have _any_ display at all, but I was able to ssh into the machine and get part way through the proprietry graphics driver installation. The installation failed, but at least I have *something* displaying on the screen now.

I have tried the fix in this thread:

[http://ubuntuforums.org/showthread.php?t=1584684](http://ubuntuforums.org/showthread.php?t=1584684)

and installed the ATI hotfix at [http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx](http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx)

The installation of this completes, however the graphics driver is not working. If I go to Administration > Hardware Drivers, then Ubuntu tells me the ATI driver is in use, but it's clearly not (takes 3 seconds to move a window).

I've tried booting into the .24 kernel instead of the .25, but that's even worse since not the mouse doesn't work in .24 (it used to work fine).

Can anyone help here? This is bloody ridiculous that this was update pushed through.


edit: Oh, and for some reason Firefox has renamed itself to the version codename, Namoroka. WTF?

---

### Post by kazza765 on 2010-10-06
Ok, here are the steps I took to fix it in case anyone else reads this. I can't be 100% sure what the fix was, since I tried a lot of different things.


1. Uninstall fglrx -> sudo apt-get remove fglrx

2. Follow the steps given here:
[http://dolphinaura.com/linux/fglrx-fix-for-catalyst-10-9](http://dolphinaura.com/linux/fglrx-fix-for-catalyst-10-9)

3. Install fglrx from synaptic -> sudo apt-get install fglrx (I don't know if this is necessary, but this is what I did so I'll list it anyway).

4. Reboot

5. Download and install the updated ATI drivers from here:
[http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx](http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx)

6. Reboot

5. Switch off update manager so this rubbish never happens again.

---

### Post by Sepiraph on 2010-10-06
Well unfortunately it happens too often than not, if only graphics card makers would supply linux compatible drivers. ](*,)

---

