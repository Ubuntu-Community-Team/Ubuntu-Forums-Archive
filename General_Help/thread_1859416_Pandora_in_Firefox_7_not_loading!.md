---
title: "Pandora in Firefox 7 not loading!"
date: 2011-10-13
forum: General Help
---

### Post by linuxuser12345 on 2011-10-13
Hi, I am running Ubuntu 11.10 with Firefox 7, and every time I login to Pandora.com, my music feed NEVER shows up! It was working fine before, but now after the update I just can't seem to get it to work. Maybe it is a website issue?

---

### Post by TyBauz on 2011-10-16
I think this is a problem with Flash. I am getting frustrated with this same problem. Pandora works in Chrome but I want to use Firefox. Any help would be appreciated.

---

### Post by TyBauz on 2011-10-17
Install Synaptic Package Manager. Do a search for "flash" and remove any packages that have "flash" in the name (no need to remove restricted extras, etc). After the packages are removed go to Adobe's website to download flash; however, DO NOT download the flash for 64 bit Ubuntu. Click on "different operating system or browser" & select 32 bit Linux and flash player 11 for Ubuntu. After I did this I was able to get Pandora to load. Please let me know if this worked for you.

---

### Post by LinuxN00b92 on 2011-10-31
I unfortunately do not have a different solution, and I would prefer not to use the 32 bit version. I just wanted to confirm the bug, I am able to get a single song to load, but when it is finished, or I try to pause/skip it with the controls, it hangs and I get a message from firefox about a non-responsive script. Opening Chromium also fixes the problem for me, but I would like to keep using firefox.

---

### Post by RayJer on 2011-11-05
Same problem here.  Pandora does not play under Firefox 7.0.1 using Ubuntu 11.10 64 bit.  Have not tried installing 32 bit version.

---

### Post by Armando Penblade on 2011-11-07
Same issue here in Firefox 7, Flash64, Ubuntu 11.10. Works A-OK on Chromium. Not really interested in switching over to 32-bit flash atm, so hoping that this gets patched by, well. . . someone :)

---

### Post by derrek.cooper on 2011-11-07
same here.. pandora and amazon cloud player do not work, you tube does.. i think its a flash issue..

---

### Post by memilanuk on 2011-12-03
Dunno if y'all found the solution... I'd had flash (specifically Pandora) working fine in 11.04 and then 11.10 working fine on my laptop, but when I installed 11.10 on my desktop, nada.  I found this thread:

[http://ubuntuforums.org/showpost.php?p=10335579&postcount=2](http://ubuntuforums.org/showpost.php?p=10335579&postcount=2)

and I gotta say, that FlashAid works beautimously ;)  Stick with the 'stable' flash version, though...

---

### Post by oldtimer7777 on 2011-12-03
> **linuxuser12345 said:**
> Hi, I am running Ubuntu 11.10 with Firefox 7, and every time I login to Pandora.com, my music feed NEVER shows up! It was working fine before, but now after the update I just can't seem to get it to work. Maybe it is a website issue?

You can try using the latest version of Firefox by installing it from the PPA:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

It is about 1/4th the way down that checklist.

And also don't forget to install the Flash Aid plugin for Firefox and make sure to configure it to use the "Stable" version of flash.

---

### Post by gfd_2 on 2011-12-03
I'm listening to the Pandora via the Web on Firefox 8.0 on Ubuntu 11.10 upgrade from 11.04 with no issues and with no checking/ unchecking of the default Firefox settings.

---

### Post by vishnu_sresht on 2011-12-09
> **gfd_2 said:**
> I'm listening to the Pandora via the Web on Firefox 8.0 on Ubuntu 11.10 upgrade from 11.04 with no issues and with no checking/ unchecking of the default Firefox settings.

I have a fresh install of Ubuntu 11.10 (64bit) running on my laptop and I was able to get Pandora to work on Firefox 8.0 using the [Flash-Aid Plugin]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/"). After installing the plugin and running the Flash Aid Wizard, I chose to install the 'Adobe Beta' version of Flash. One automated script execution and browser restart later, I had my music back ! :D

---

