---
title: "Online Video Problem with 12.04"
date: 2012-05-12
forum: General Help
---

### Post by CanuckArborist on 2012-05-12
I have just upgraded to 12.04 and now online videos, You Tube etc will not play. There is no frame or controls displayed. Any help greatly appreciated.

---

### Post by CanuckArborist on 2012-05-13
Ok, 97 views and absolutely no answer? I have done all of the usual things... reinstalled flash, updated FireFox etc. I'm not a Linux novice and I'm stumped. As I said ANY help would be greatly appreciated.

---

### Post by kolinab on 2012-05-13
Hi!

Do you remember if you selected to install third party plugins when you first installed ubuntu? If not, you could try:

sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ffmpeg

These are the packages suggested on: [http://www.omgubuntu.co.uk/2012/04/10-things-to-do-after-installing-ubuntu-12-04/](http://www.omgubuntu.co.uk/2012/04/10-things-to-do-after-installing-ubuntu-12-04/)

Some people also recommend installing ubuntu-restricted-extras, ([http://www.itworld.com/software/272630/install-third-party-codecs-ubuntu-1204](http://www.itworld.com/software/272630/install-third-party-codecs-ubuntu-1204)) but I don't have it installed on my system and don't have any problems with youtube.

Let us know how it goes!

K

---

### Post by CanuckArborist on 2012-05-13
Thanks for bothering to reply. If only it were that easy, I've tried all of that already. I'm having other minor issues so I think that I might just go for a full re-installation, new and as yet empty 2TB drive anyway. But if anyone else has any suggestion, please feel free to post up.

---

### Post by SciFiFan on 2012-05-14
Had much of the same problem.

Found that there is some problem with the Nvidia drivers. One used with 11.10 had an end number of 35. Ubuntu updated it to a 40 that has problems. Used Synaptic to update the driver to a 49. It works fair, although on some videos and websites the entire screen blanks out for 2-3 seconds repeatedly. Haven't found an answer to that one yet.

Try updating the drivers if it's not Nvidia.

---

### Post by CanuckArborist on 2012-05-14
No luck so far with any codecs or drivers.

---

### Post by CanuckArborist on 2012-05-14
Bump...

---

### Post by CanuckArborist on 2012-05-15
This is getting a little infuriating, this is meant to be a help forum and so far very little help has been offered. 

ANY further suggestions would be greatly appreciated.

---

### Post by jefsview on 2012-05-15
> **CanuckArborist said:**
> This is getting a little infuriating, this is meant to be a help forum and so far very little help has been offered. 

ANY further suggestions would be greatly appreciated.

Well, usually folks will give more info that "this doesn't work."

If you off info about your computer specs, someone might have a starting place to try and help you.

What type of computer, cpu, gpu, ram, etc.

Also, did you try installing another browser such as Chromium or Google Chrome, just to see if it's the brwoser and not your computer?

What were you upgrading from?

More info helps to offer you help.

-- Jeff

---

### Post by SeijiSensei on 2012-05-15
In Firefox, what do you see at Tools > Add-on Manager?  What version of Flash plugin is installed?  You should be running 11.2.

How did you install the plug-in?  Did you activate the partner repository and install the package "adobe-flashplugin" from there?  That's the current approved method.

---

