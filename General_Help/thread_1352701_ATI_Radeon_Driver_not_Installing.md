---
title: "ATI Radeon Driver not Installing"
date: 2009-12-11
forum: General Help
---

### Post by farhan91 on 2009-12-11
Hello, I am a first time user for ubuntu and have got ubuntu 9.10 running fine except the video driver. I know it is my video driver that is the problem because when ever I do any multimedia, it lags and plays the media extremely choppy. I get this problem mostly while im on the Internet looking up a youtube video or just a flash document or even when minimizing a window. 

I am using the ATI Radeon X1650 as my video card. The driver I downloaded was: [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English)

After the download, I ran the ati-driver-installer-9-3-x86.x86_64.run by simply double clicking it and run as terminal. The installer seems to start, but after about 30 seconds, the terminal window closes and nothing else happens. I have tried changing the permissions of the file and sill I get the same problem. 

I tried the following command(s):
> sudo chmod +x ati-driver-installer-9-3-x86.x86_64.run
./ati-driver-installer-9-3-x86.x86_64.run

After that, I get the following output:
> Created directory fglrx-install.YdCXfe
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-16-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.YdCXfe

If anyone could help me, please and thanks. 

Regards,

Farhan Ahmad

---

### Post by hawthornso23 on 2009-12-11
There is an issue with the proprietary drivers for older ATI graphics cards not supporting the newest version of XOrg which has been in use since Jaunty. The upshot is that if you have one of those cards you can't use a proprietary driver with either Jaunty or Karmic because that driver won't work with the version of XOrg you have. You can install Hardy (long term service release) and have full 3-D acceleration with the proprietary driver, or stick with Karmic and use the open source driver without full graphics acceleration via the open source driver.

Your card may be one of those so afflicted as the message looks like it is complaining about versions. You need to check the ATI site to see what the exact situation is with your card. The cards with this problem are not all that old. Bascially ATI got behind in updating its drivers and got caught out by the update to XOrg. In order to catch up they then decided to abandon driver support for all but their newest cards. Back when Jaunty came in people with almost brand new equipment were being told their hardware was no longer supported  It sucks I know. 

I had this problem. I bought a new card.

---

### Post by MelDJ on 2009-12-11
have you tried the drivers available in system-admin-hardware drivers?

---

### Post by farhan91 on 2009-12-11
> **MelDJ said:**
> have you tried the drivers available in system-admin-hardware drivers?

How do I do that?

---

### Post by MelDJ on 2009-12-11
in the menu bar on the top left of the screen, click on system, then administration. then click hardware drivers and see whether there are drivers available there

---

### Post by farhan91 on 2009-12-11
> **MelDJ said:**
> in the menu bar on the top left of the screen, click on system, then administration. then click hardware drivers and see whether there are drivers available there

I don't see anything there.

---

### Post by farhan91 on 2009-12-12
So can anyone help me please? :?

---

### Post by farhan91 on 2009-12-15
Ok so can anyone help me. Bumped! :)

---

### Post by hawthornso23 on 2009-12-15
As I told you earlier, your card is no longer supported by ATI and the proprietary Catalyst drivers will not work with the new version of XOrg used in Jaunty and Karmic. ATI have no plans to fix this problem. Look here
[URL="http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English"]
http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.9&lang=English
[/URL]
In particular read this bit

"The Linux ATI Catalyst™ driver will only be supported in Linux distributions prior to February 2009 for the legacy products listed above."


Your card is one of the listed ones. February 2009 is when the new version of XOrg started appearing in distributions. 

The news is not good. You've got three options

[LIST=1]
[*] Use the open driver. You won't get 3-D accelleration and flashy graphics but everything will be stable and will work.
[*]Downgrade your ubuntu to Hardy. The proprietary driver will then work and you'll get full 3-D accelleration. But you won't be using the latest version of ubuntu.
[*]Buy a new graphics card.
[/LIST]
Don't go blaming ubuntu for this by the way. You'd have the same problem using any other linux distro as they are all switching to the new version of XOrg. The problem is crappy driver support on the part of the manufacturer of your video card. I'm afraid they've declared you obsolete.

---

### Post by Queue29 on 2009-12-15
> **hawthornso23 said:**
> 
Don't go blaming ubuntu for this by the way. You'd have the same problem using any other linux distro as they are all switching to the new version of XOrg. The problem is crappy driver support on the part of the manufacturer of your video card. I'm afraid they've declared you obsolete.


No, they have declared Linux support irrelevant. The card is still supported under the legacy ATi driver for Windows.

---

### Post by 3rdalbum on 2009-12-15
ATI no longer makes a driver for your card. Sorry. The good news is that there is an open-source driver that is currently in operation on your computer. It's not the best, but it works and it is still being improved on.

I would suggest buying an Nvidia graphics card, as they are less hasty about obsoleting older cards on Linux. If you've never bought a graphics card before, you will want to do some research about whether your computer uses AGP or PCI-E for connecting graphics cards - all current cards use PCI-E but you can often still find older Nvidia 6000 and 7000 series cards in AGP.

---

### Post by hawthornso23 on 2009-12-15
> **Queue29 said:**
> No, they have declared Linux support irrelevant. The card is still supported under the legacy ATi driver for Windows.

They don't offer Windows 7 support for these cards either. 

I think it is just lousy driver support all around, not a specifically anti-linux thing. But because the pace of linux development is so much faster than windows development, we notice it more acutely.

---

### Post by farhan91 on 2009-12-17
Ok thanks everyone for helping me out. Just to try, I installed Ubuntu 8.10 on my computer and it seemed to work fine but I was not able to get crossover to work properly. Anyways Im probably gona end up getting a new system anyways as my system is getting a little old. So thanks again to everyone that helped me out.

---

### Post by hawthornso23 on 2009-12-18
You are welcome. Sorry we couldn't give you a better result.

Merry Christmas
 ... from my Hamilton to yours ...

---

