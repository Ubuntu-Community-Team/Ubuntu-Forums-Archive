---
title: "I am blocked from my Ubuntu"
date: 2011-04-29
forum: General Help
---

### Post by bill23 on 2011-04-29
[URL="http://forums.delphiforums.com/crossborn/messages?msg=1452.1"]
[/URL] 
[SIZE=4][FONT=Palatino Linotype][COLOR=#800000]I  have Ubuntu 10.04 on one side of my PC and today I was using the Ubuntu  side. Things were going along just fine, no problems. Then I decided to  install openoffice.org suites. The installation seemed to be going  along normally, then without a warning of any kind. My desktop  background came up. But there was something wrong.  Sure the image was  there but nothing else, the icons for Firefox, Thunderbird, Opera even  Evolution and the others normally across the top banner were not there. I  started tapping keys to no avail. The only thing I managed to do was to  get to the 'opening' page but it too was blank. I clicked the power  button a couple times only succeeded in shutting the PC off. I waited a  few moments then turned it on and when the option came up whether to  switch to Windows XP side or Ubuntu,  well I clicked the Ubuntu side. My  thinking was it was a glitch and the sign in box would pop up and that  would be that. No  sign in box, nothing but the Ubuntu screen with  nothing else. Once again I fruitless tapped numerous keys hoping  something would click and I would at least be able to sign in, but like  before no such luck. As before I tapped the power button several times  and the PC was shut off. When I restarted it, this time I did not select  Ubuntu and within a few moments I was back on the Windows side.

I  have never heard of something like this happening to any Linux distro  and especially not to an Ubuntu one. I am at a loss to understand what  happened? Did my attempt to install OpenOffice.Org Suites in some way  caused my Ubuntu to crash? If I had open office already installed would  the installation have gone forward or would I have been told;  "OpenOffice" already installed. I got no such warning, just a sudden  blank desktop.

I still have the installation disk. If necessary I  will reinstall Ubuntu 10.04 but before I do I am hoping someone here  might have an idea what happened and what I can do to rectify the  situation.

One thing which keeps coming up is: myname@myname-desktop: ~$         I do not know what to put after those symbols?

bill23
[/COLOR][/FONT][/SIZE]

---

### Post by dino99 on 2011-04-29
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

sudo rm /etc/X11/xorg.conf

reboot

---

