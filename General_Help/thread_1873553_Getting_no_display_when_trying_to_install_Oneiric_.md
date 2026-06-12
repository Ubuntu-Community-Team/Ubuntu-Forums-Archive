---
title: "Getting no display when trying to install Oneiric on an HP Pavilion dv6-6000 series."
date: 2011-11-01
forum: General Help
---

### Post by inameiname on 2011-11-01
I'm having trouble getting Ubuntu 11.10 Oneiric to even run on Live Disc  (or to use its installer) on a new laptop, an HP Pavilion dv6-6110us. 

I am certain it has something to do with the graphics, as upon startup  of the live disc/flash drive, the screen goes black almost immediately. I  tried the safe graphics mode, and all of the other methods to run it as  well. 

One thing to note: this laptop is only about 6 months old, and from the  time I got it, there have been issues with Ubuntu on it, supplemented by  numerous readings of threads on these HP Pavilion dv6-6000 series  machines. For Natty, I had to install an ATI driver (which wasn't fully  supportive), just to get the desktop effects working. Unfortunately, not  even that works now, in Gnome3/kernel 3.0.0-12/Oneiric.

Again, it sounds like these laptops are new enough to not have full support yet in Linux. I just don't understand what might be causing the issue in Oneiric now, in which I cannot even install a fresh installation of Ubuntu. 

So if  anybody has a clue about this, I would love to hear it. 

Thank you in advance.

---

### Post by inameiname on 2011-11-02
Bump.

I'm surprised nobody else has mentioned having some sort of issues with that series of notebook computers as I know there are a number of threads out there about other issues with them.

---

### Post by gandaran on 2011-11-02
for the black screen try one of the options on this thread
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

has for the ATI drivers it's probably best to continue using the default open source drivers on ubuntu 11.10, many users are having problems with them.

---

### Post by inameiname on 2011-11-02
> **gandaran said:**
> for the black screen try one of the options on this thread
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

has for the ATI drivers it's probably best to continue using the default open source drivers on ubuntu 11.10, many users are having problems with them.

Thanks for the link. The problems mentioned there do seem to be a part of what my issue is. However, after trying all of the possible combinations, it still fails to boot into the live disc. 

Using the "nomodeset" option at startup does make it retain a picture, and it actually does go to the usual Ubuntu splash screen. Sadly, though, it doesn't do anything past that. Often the result is a message saying this:

"(initramfs) Unable to find a medium containing a live file system"

I've tried a number of other options, all alone and then with "nomodeset" (which seems to be required to get a picture), but none work. Oddly by selecting all of the choices it got me to a command prompt.

And as for the ATI drivers, they seem to work just fine, albeit having to install a hack of sorts to remove the 'unsupported' water logo at the bottom right after installation. Not a huge deal.

It is just I cannot even get to that with the first issue to even decide on whether or not I should install the ATI drivers.



One final thing to mention, back in Natty I also had issues (blank screen) whenever I tried to install the 3.0.0 Linux kernel. As such, I can be fairly positive it is a kernel issue, presumably one similar to that which was mentioned in that link you gave.

---

