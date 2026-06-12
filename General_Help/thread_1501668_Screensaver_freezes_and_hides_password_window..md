---
title: "Screensaver freezes and hides password window."
date: 2010-06-04
forum: General Help
---

### Post by jbrodmann on 2010-06-04
I'm using:
ubuntu 10.04 64 bit
proprietary fglrx drivers for ati 4890.

When shaking the mouse to bring up the computer, the screensaver will freeze and not display the dialog box to log back into my profile.  However, even though I can't see it, if I blindly and correctly type in my password it will work.

Thanks for the help.

**[COLOR="Red"][update][/COLOR]** I posted this question while at work where I do not use Ubuntu...sadly.  Anyway, when I got home, I locked the screen, the gl fish screensaver came up.  bam, no login dialog box.  ok, tried the gl matrix screensaver, bam, no dialog box.  Finally, I tried a non-gl screensaver, and what do you know, there's my login dialog box.  Something is up with the gl screensavers.  

Just to reiterate, when I activate the mouse or keyboard during a gl screensaver I do not see the login dialog box.

So, problem not solved, but, work around found.

---

### Post by dcstar on 2010-06-05
> **jbrodmann said:**
> I'm using:
ubuntu 10.04 64 bit
proprietary fglrx drivers for ati 4890.

When shaking the mouse to bring up the computer, the screensaver will freeze and not display the dialog box to log back into my profile.  However, even though I can't see it, if I blindly and correctly type in my password it will work.
.........

There are bugs where similar things happen when switching users and it is a Gnome screensaver issue.

You may want to ensure that you have the latest gnome-screensaver package - 2.30.0-0ubuntu2 - available in the Lucid Updates repository.

---

### Post by jbrodmann on 2010-06-07
> **dcstar said:**
> There are bugs where similar things happen when switching users and it is a Gnome screensaver issue.

You may want to ensure that you have the latest gnome-screensaver package - 2.30.0-0ubuntu2 - available in the Lucid Updates repository.

Gotcha.  Thank you.

---

### Post by RJ12 on 2010-06-07
Same thing is happening to me...

---

### Post by pricorp on 2010-07-16
Same problem.
If you found a solution please post.
Thanks,

---

### Post by IraGainesUK on 2010-08-02
Exactly the same problem for me too.

---

### Post by purcellchristopher on 2010-08-10
I observed a similar problem today.  Enabled the robotic ant screen saver and when I wiggled the mouse to log in, there wasn't a log in dialog.  On a whim, I just typed my password and hit enter.  The screen saver unlocked and I was back at my desktop.

---

### Post by nate1010smith on 2010-09-09
This is happening to me too. As jbrodmann mentioned, this problem seems to occur only with openGL screensavers.

My current setup is using the ATI/AMD proprietary FGLRX driver on Ubuntu 10.04 64bit. gnome-screensaver version 2.30.0-0ubuntu2 is installed

Does anyone have any patches/workarounds other than simply using non openGL screensavers?

---

### Post by misiek1928 on 2010-09-22
I have the same problem with my HD4850...

---

### Post by xeross on 2010-09-24
I have the same problem here, however you can still type in your password and hit enter even when the dialog doesn't show.

AMD Phenom x4
ATI Radeon HD 5850

---

### Post by nate1010smith on 2010-09-26
> **nate1010smith said:**
> This is happening to me too. As jbrodmann mentioned, this problem seems to occur only with openGL screensavers.

My current setup is using the ATI/AMD proprietary FGLRX driver on Ubuntu 10.04 64bit. gnome-screensaver version 2.30.0-0ubuntu2 is installed

Does anyone have any patches/workarounds other than simply using non openGL screensavers?

Update:

My card is an ATI Radeon HD 5770.
I've also been having some issues where the machine will lock up completely after the screen saver runs regardless of whether or not it was an OpenGL screensaver. I think this may be an unrelated issue though, possibly related to the display not waking up after going to sleep - I haven't done much testing on that yet.

---

### Post by Smiff2 on 2011-08-16
just run into this problem also..

Ubuntu 10.10 32bit, Radeon 9600 AGP with open source driver. latest kernel update 2.6.35-30-generic and all security updates applied.
using the "RSS" opengl screensaver package.

can use CTRL+ALT+F1 to access console, see the screensaver is maxing out cpu with top, kill it with killall -9 solarwinds or whichever screensaver it is, then CTRL+ALT+F7 and log back in normally.

problem is, its a multiuser system and no one else knows how to do this (or has the permissions to do it anyway!). so for now i have to set all screensavers to blank screen i think?
shame as otherwise 3d seems to work well, so does Compiz. and the same screensavers work on the other machines on the network, meaning no screensavers anywhere. this isn't a disaster, unless opengl apps are affected (google earth? haven't tried it yet).

i notice it's all ATI hardware users having this problem? all with KMS enabled?


don't see much in logs except for this:

> kernel: [30238.702371] [drm:drm_mode_getfb] *ERROR* invalid framebuffer idno resolution found?
not keen to try randomly applying updates (e.g. xorg, compiz etc) from Recommended in case they cause other problems.

I suspect it may be related to power saving whilst running OGL. this machine also doesn't power off when halted, possibly ACPI or HAL issue, could that also freeze OGL screensaver? that may sound serious but literally everything else works fine afaik and this machine stays on 24/7.

here's my xorg.log in case that helps
[http://pastebin.com/Ykjrtn16](http://pastebin.com/Ykjrtn16)

---

### Post by N8N on 2011-12-20
> **dcstar said:**
> There are bugs where similar things happen when switching users and it is a Gnome screensaver issue.

You may want to ensure that you have the latest gnome-screensaver package - 2.30.0-0ubuntu2 - available in the Lucid Updates repository.

I just re-set up a box that I'd been using a year or so ago but not since.  Ran all the updates.  *Now* I am having the same problem as the OP where I wasn't before.  Am using ATI Catalyst proprietary drivers.  Also on 10.04 and I *do* have the latest gnome-screensaver package, or at least the one that you reference above.

---

### Post by bbrg548 on 2012-02-19
I'm having the same issue, and after I installed the Kubuntu packages it also happens in KDE.

Any ideas?

Toshiba Satellite L775D-S7305 (AMD A6-3400M)
Ubuntu/Kubuntu 11.10
Last update 18 Feb 2012

---

### Post by klaymenn on 2012-03-12
I think that this topic: [http://ubuntuforums.org/showpost.php?p=10798466&postcount=50](http://ubuntuforums.org/showpost.php?p=10798466&postcount=50) could help. Basically - turn off synv to VBlank in OpenGL plugin in Compiz Manager tool.

---

### Post by bbrg548 on 2012-03-18
> **klaymenn said:**
> I think that this topic: [http://ubuntuforums.org/showpost.php?p=10798466&postcount=50](http://ubuntuforums.org/showpost.php?p=10798466&postcount=50) could help. Basically - turn off synv to VBlank in OpenGL plugin in Compiz Manager tool.

Doesn't fix if for me.

---

