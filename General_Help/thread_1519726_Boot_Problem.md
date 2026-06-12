---
title: "Boot Problem"
date: 2010-06-28
forum: General Help
---

### Post by Johnny13811 on 2010-06-28
I'm currently running 10.04, when I went to go turn on visual effects it gave me a prompt to install an nVidia driver, after installation was complete it said I had to restart. When I start it up the screen flickers from being on and off, it then finally stops at being on but nothing shows up. Please help. My graphics card is nVidia G210M. Sony Vaio.

---

### Post by garvinrick4 on 2010-06-28
> **Johnny13811 said:**
> I'm currently running 10.04, when I went to go turn on visual effects it gave me a prompt to install an nVidia driver, after installation was complete it said I had to restart. When I start it up the screen flickers from being on and off, it then finally stops at being on but nothing shows up. Please help. My graphics card is nVidia G210M. Sony Vaio.
Remove the offending driver:
Put in install CD and boot off of it and pick Try Ubuntu. When it comes to desktop choose
disk Utilitity and click on drive on left and the click on your install be it sda1 or sda2 or sda5 whichever is 10.04 install. In lower right choose to Edit Label and the label it.
I am going to say you choose to label it lucid for this example.
 Now go into a Terminal. ctrl/alt/t. And put in this code.
I am using sda1 and lucid use your own.
```
sudo mkdir /media/lucid
``````
sudo mount /dev/sda1 /media/lucid
``````
sudo chroot /media/lucid
``````
 apt-get remove (the name of driver you installed, package name)
``` Hit keys ctrl/d```
sudo umount /media/lucid
```Now you should be back before you installed offending graphics driver. That is not a typo umount.

---

### Post by garvinrick4 on 2010-06-28
#For previous post:
I am sorry I forgot to tell you what your did.
Install being 10.04 lucid lynx. lucid was the label and sda1 was partition (use your own)

You labeled your install.
You made a directory for your install. (folder).
You mounted your install.
You gave yourself root powers in the install
You removed a package in the install.
ctrl/d gets you out of root powers.
You unmounted your install.

---

### Post by rollin on 2010-06-28
Above is excellent. If you do need a driver though I'd recommend getting an official version from [www.nvidia.com](www.nvidia.com) as I had problems  with the Ubuntu versions also.

---

### Post by Johnny13811 on 2010-07-08
oh okay cool I'll give that a shot. I re-installed Ubuntu 9.10 from a CD. Somehow I managed to install a driver called nVidia Riva/TNT/GeForce instead of the recommended nvidia version 185. the Riva driver gave me an AIGLX rendering method, when I installed the recommended version, the rendering method disappeared. I re-installed the Riva driver but the rendering method never appeared. Any ideas on what's going on? It seems I cant have a rendering method and an nvidia driver installed at the same time. Sorry about not replying instantly I was on vacation. Thanks for the help guys! :p

---

