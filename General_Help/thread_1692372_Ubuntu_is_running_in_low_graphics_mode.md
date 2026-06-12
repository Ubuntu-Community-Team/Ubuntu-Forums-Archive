---
title: "Ubuntu is running in low graphics mode"
date: 2011-02-21
forum: General Help
---

### Post by Josep CA on 2011-02-21
Hi,
I have Ubuntu 10.10 and when I boot my PC I can see the following message: Ubuntu is running in low graphics mode and Ubuntu stops booting. I can-t boot in it I can only use command line.
I think I accidentally uninstalled some packages clicking at completely removal at some ipod utilities in synaptic. How can I fix this?
Your help is sincerely appreciated

Cheers

---

### Post by Arno_H on 2011-04-10
Hello,

I have had exactly the same problem and it also appeared when uninstalling some ipod utilities. The window crashed in the middle of the uninstallation. I have lloed through the forums for a solution, but haven't found one. 

I am running Ubuntu10.10, with an Nvidia graphics card

I checked for the file /etc/X11/xorg.conf, but it didn't exist. It doesn't exist on my rescue installation.

I found that the running [FONT=Arial Black]sudo apt-get update [/FONT]followed by [FONT=Arial Black]sudo apt-get upgrade [/FONT]should solve some issues, which it didn't.

I found that the command [FONT=Arial Black]nvidia-xconfig[/FONT] should resolve issues, but the command does not exist and could not be found.

I found a package [FONT=Arial Black]xserver-xorg-video-nv[/FONT], but could not run that as a command either. I used [FONT=Arial Black]sudo dpkg -P [/FONT]followed by [FONT=Arial Black]sudo apt-get install [/FONT]on xserver-xorg-video-all to make sure the packages were correctly installed, but that didn't work either.

So, could somebody help me.

Thanks in advance,

---

