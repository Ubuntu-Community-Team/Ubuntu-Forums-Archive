---
title: "Nvidia Restrcited Driver Issue... Crash???"
date: 2010-05-05
forum: General Help
---

### Post by ephman on 2010-05-05
hi,

so i installed a fresh copy of 10.04 amd64 the other day.  and then enabled the recommended restricted nvidia driver.  and a few hours later my machine locks up. the mouse still moves around though.  but the machine is unresponsive to any clicking.  i have a nvidia 9650m gt, card in an asus m70vn notebook. any ideas?

thanks,

ephman

---

### Post by dino99 on 2010-05-05
edit the boot line and add video=vesa, then you can use the system

---

### Post by ephman on 2010-05-05
do you know how long i've been dealing with this crashing issue?  for what seems like forever at this point.  since 9.04 i've been having to force the powermizer on max to solve this issue.  but with 10.04, that didn't seem to work.  ok i will report back with the results of your suggestion.  huge karma goes back to you if it works!

ephman

---

### Post by dino99 on 2010-05-05
thanks man :p

in case you have some external devices plugged when you have these issues, try when they are unplugged

looking at .xsession-errors and logs might help a little

---

### Post by coetzewc on 2010-05-05
Have the same issues on Desktop with NVIDIA 6500 pci-e card. When I load  the Nvidia drivers the PC locks up with black screen only. Seems to  also affect the Screen saver. NVIDIA drives shows screensaver nicely but  crashes system. When I use the Plymouth driver my relolution sucks  especially in browsing, text seems "jittery" for a lack of a better  word.

can't find anything related to this on the web
Oh and cant drop into terminal ALT F1 with NVIDIA drivers does not ask  for password and prompts login again but with Plymouth drivers that  works fine.

I know this is many issues for this thread but it all seems related to  the NVIDIA driver??

---

### Post by dino99 on 2010-05-05
> **coetzewc said:**
> Have the same issues on Desktop with NVIDIA 6500 pci-e card. When I load  the Nvidia drivers the PC locks up with black screen only. Seems to  also affect the Screen saver. NVIDIA drives shows screensaver nicely but  crashes system. When I use the Plymouth driver my relolution sucks  especially in browsing, text seems "jittery" for a lack of a better  word.

can't find anything related to this on the web
Oh and cant drop into terminal ALT F1 with NVIDIA drivers does not ask  for password and prompts login again but with Plymouth drivers that  works fine.

I know this is many issues for this thread but it all seems related to  the NVIDIA driver??

first into: system admin hardware driver, is nvidia-current activated ?

---

### Post by coetzewc on 2010-05-05
I have tried Admin | hardwase drivers, system crashes with those.

---

### Post by dino99 on 2010-05-05
is it Lucid installed or karmic ?

if you can open "synaptic" (system admin synaptic), tell me if, in the repo tab, you have some third party repo or ppa activated, in case uncheck them.(of course, all the repo need to be with the same distro and release)
You should only have: nvidia-current, nvidia-current-modaliases, nvidia-common and nvidia-settings installed.

now into console:

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure plymouth
sudo update-initramfs -u
sudo grub-mkconfig && update-grub

---

### Post by coetzewc on 2010-05-05
10.04 Lucid Fresh install will check the Synaptic stuff, just now. Thanks so far.

---

### Post by dino99 on 2010-05-05
> **coetzewc said:**
> 10.04 Lucid Fresh install will check the Synaptic stuff, just now. Thanks so far.

so with synaptic: first remove/purge the nvidia packages installed (right click) then install the ones i've given in the previous post

---

### Post by coetzewc on 2010-05-05
enabled Canonical-supported OSS (main)
enabled Community-maintained OS (universe)
enabled Proprietary drivers for devices (restricted)
enamled SW restricted blah blah (multiverse)

under Other Software 
enabled only [Http://archive.canonical.com/ubuntu](Http://archive.canonical.com/ubuntu) lucid partner

Updates 
enabled (lucid-security)
enabled (lucid-updates)

Nothing else.

Now for the console stuff....
a few minutes....

---

### Post by coetzewc on 2010-05-05
On my quest 
removed all nvidia stuff with synaptic and installed 
nvidia-current
nvidia-settings 
have to install nvidia-173-modaliases
have to install nvidia-96-modaliases
nvidia-common then

Did the console commands, and rebuit.
Then used System Administration hardware to enable NVIDIA driver again. That is the correct wat to enable it, yes??

Started FTP download from local repositry and X crashed agter some screensaver activity, I'm sure. I was able to get into console ALT F1 this time but it seems af my path was "enviromental variables" was lost, had to cd into filesestem to see what I could run. could not execute "top" to check what's holding up the processor but it seems as if the cpu was working overtime 100% utilisation because I could see after hard reset over heating/ high heat from bois sensor. This usually, tells me cpu worked to hard. This is more or less what my inital symtoms were and still is.

As I said with the Kernel (plymouth) driver, all seems stable but resolution is crap when browsing and screensaver is very slow. 

Can GLX have something to do with this I red somewhere to revert to glx 1.2, current version is 1.4??? does this make sence or ring any bells? I don't know how to down grade this but could find out i'm sure. I'm trying my best to understand all this and I'm not a programmer so stabbing in the dark here?

---

### Post by coetzewc on 2010-05-05
Also worth a mention had none of these issues win 9.04 or 9.10.

---

### Post by ephman on 2010-05-06
ok about 24 hours now running with the addition of editing the boot line by adding video=vesa.  can report my computer did crash.  once.  when i rebooted i went and pumped the powermizer setting up to maximum, and so far no crash.  but i'm back on the system and doing my normal stuff now, and we'll see... will report back if we crash again.  if you don't hear from me life is good and the powermizer max setting help something. 

ephman

---

### Post by ephman on 2010-05-07
CrAsH!!!!  ok it crashed.  ;(  had to restart x. sucks.  plugged my google nexus one phone in the usb, and kaboom.  going to search around for something to help fix this.  oh well ;(

ephman

---

