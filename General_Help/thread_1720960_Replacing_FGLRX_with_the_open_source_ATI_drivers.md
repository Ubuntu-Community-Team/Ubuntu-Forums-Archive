---
title: "Replacing FGLRX with the open source ATI drivers?"
date: 2011-04-03
forum: General Help
---

### Post by Blackcamaro8 on 2011-04-03
I have an ATI Radeon 4200 HD Mobility, with 256 MB of my RAM dedicated to it. I installed FGLRX, but the performance actually dropped compared to the open source drivers that come installed by default. I removed fglrx, and reinstalled the Radeon packages, but no avail.

Now, when I boot, I get the error, "unable to load module 'fglrx'," and my only option is to run Ubuntu in Safe Graphics Mode. This tells me that the computer is still trying to load FGLRX, and there's something that needs to be altered down at the boot level. 

 Anyone able to help?

It's much appreciated. Thank you all, in advance.

---

### Post by gerowen on 2011-04-03
I remember doing this manually a long time ago.  You have to sudo dpkg --reconfigure something or other after you uninstall the ATI drivers.  I'll have to do some googling and get back to you on that.

---

### Post by alphacrucis2 on 2011-04-03
> **Blackcamaro8 said:**
> I have an ATI Radeon 4200 HD Mobility, with 256 MB of my RAM dedicated to it. I installed FGLRX, but the performance actually dropped compared to the open source drivers that come installed by default. I removed fglrx, and reinstalled the Radeon packages, but no avail.

Now, when I boot, I get the error, "unable to load module 'fglrx'," and my only option is to run Ubuntu in Safe Graphics Mode. This tells me that the computer is still trying to load FGLRX, and there's something that needs to be altered down at the boot level. 

 Anyone able to help?

It's much appreciated. Thank you all, in advance.


Which version of fglrx did you install? The latest was released by AMD last week (Catalyst 11.3). That works very well on my machine.

---

### Post by Blackcamaro8 on 2011-04-03
I don't mind; I can currently use the computer in Safe Graphics Mode, I just won't be able to do anything that requires graphical acceleration. If I want to game, I'll just use W7 until I can get the open source drivers working. 

Thanks!

---

### Post by Blackcamaro8 on 2011-04-03
I installed the fglrx from the repositories. Does their new release work with 10.04, installing correctly and everything?

---

### Post by alphacrucis2 on 2011-04-03
> **Blackcamaro8 said:**
> I installed the fglrx from the repositories. Does their new release work with 10.04, installing correctly and everything?

Yes it does. Install via the buildpkg method as described in the ATI binary driver howto. Cat 11.3 doesn't work with Natty though. No doubt AMD will release a pre version of 11.4 or 11.5 for that as they usually do.

---

### Post by Blackcamaro8 on 2011-04-09
Thank you all for the answers, but I finally got it working with the open source drivers. 
The main drop in performance was with Docky's smoothness. It became jerky, and just overall lagging. 

I used the dialogue after "X server could not start correctly," to restore the graphics configuration to the default, and the open source drivers worked fine. The only thing that was not satisfactory with them was odd misshapen clouds when playing Minecraft... 

So then I tried the buildpkg method, and it worked! But then Docky slowed down again... So I decided to see if it was a bug. Turns out that Docky has problems with both NVidia and ATI proprietary drivers. Then, I ran Docky in 'netbook' mode with the -n switch, and the performance drastically improved, but not to the full speed of the open source drivers. Oh well, I hope there's a bug fix released sometime.

---

