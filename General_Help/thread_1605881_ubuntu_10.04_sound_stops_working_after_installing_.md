---
title: "ubuntu 10.04 sound stops working after installing nvidia drivers"
date: 2010-10-25
forum: General Help
---

### Post by d3drocks on 2010-10-25
ok, this is driving me insane.
i logged into my computer a few minutes ago with no issue. everything was working fine (including sound). i noticed i hadnt installed my nvidia drivers yet, so I did that and rebooted. after I rebooted, I had no sound, and my default sound device is "Dummy sound device". my ins and outs are no longer listed!!! what the hell? this is clearly not normal behaviour. anyone have a solution?

edit:
lspci outputs 2 sound devices now:
Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

im guessing i need to somehow switch it back to the intel one, but i dont know how.

EDIT#2: 
 just did: aplay -l 
with the output of:
aplay: device_list:223: no soundcards found...

still very lost, need some help.

---

### Post by d3drocks on 2010-10-25
1 view so far? seriously ide really appreciate some help. this is one of very few times i cant figure it out on my own. ive never had a freaking graphics driver screw over sound on my system before. ide really like some insight on how to fix this.

---

### Post by ellgor on 2010-10-26
Hi,

I read that the nvidia drivers dont always load in correctly, = problems, so I found this guide that gets them loaded in and running:

Download the newest drivers for your card from the nvidia site, keep them handy

Open a terminal and stop the gdm(gnome display manager) with this:

sudo gdm-stop

A black screen wil be presented with terminal access, cd to the downloaded nvidia package

 Install driver:

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run (or whichever package you have) be precise as errors will result in "no such file"

Note: If you get an error message like this "Unable to find kernel source tree", do this:
$ sudo apt-get install linux-headers -`uname -r'

then run the installer again

Follow the onscreen guide from Nvidia and when done

Start GDM:

sudo service gdm start

Hope this of help,

Regards, Ellgor.

---

