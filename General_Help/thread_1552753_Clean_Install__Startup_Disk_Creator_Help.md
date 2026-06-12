---
title: "Clean Install / Startup Disk Creator Help"
date: 2010-08-14
forum: General Help
---

### Post by hooligandisco on 2010-08-14
This Thread is sort of a continuation of [my previous one]("http://ubuntuforums.org/showthread.php?t=1549686").. (Please refer to it for background information)

I decided to upgrade my 8.04.2 to 10.04 via a (ubuntu-10.04-desktop-i386.iso) usb start up disk. I download the ISO file and I have a usb ready but my problem is that I don't have the 'Startup Disk Creator' on my system. 

At this point, there is no other computer to use for this installation.. How can I make a bootable usb with the lucid lynx on it if I don't have the program or any help?

Any comments are appreciated, thanks

---

### Post by kerry_s on 2010-08-14
try this-> [http://mirrors.kernel.org/ubuntu/pool/main/u/usb-creator/usb-creator_0.1.10_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/u/usb-creator/usb-creator_0.1.10_all.deb)

download & double click on it.

if that fails, check if unetbootin is in the synaptic repo.

---

### Post by kpuz on 2010-08-14
Hi,
Check to see if you can install Startup Disk Creator from the synaptic package manager. Search for usb-creator and install the version for kde (if you are using kde) or the gtk version.

---

### Post by hooligandisco on 2010-08-14
> **kerry_s said:**
> try this-> [http://mirrors.kernel.org/ubuntu/pool/main/u/usb-creator/usb-creator_0.1.10_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/u/usb-creator/usb-creator_0.1.10_all.deb)

download & double click on it.

if that fails, check if unetbootin is in the synaptic repo.

Hey, thanks alot. I really own you one. I still have a question though (of course) I'm not sure what to select for the last option of the start creator. *Image Attached*

---

### Post by kerry_s on 2010-08-14
> **hooligandisco said:**
> Hey, thanks alot. I really own you one. I still have a question though (of course) I'm not sure what to select for the last option of the start creator. *Image Attached*

i always select "discarded" cause i only run it live to check things work. i don't want it installing any mistakes i made & it saved. :D

---

### Post by kerry_s on 2010-08-14
> **kpuz said:**
> Hi,
Check to see if you can install Startup Disk Creator from the synaptic package manager. Search for usb-creator and install the version for kde (if you are using kde) or the gtk version.

usb-creator wasn't made till 8.10, i don't think it came standard till 9.04.

---

### Post by hooligandisco on 2010-08-14
> **kerry_s said:**
> i always select "discarded" cause i only run it live to check things work. i don't want it installing any mistakes i made & it saved. :D

uh-huh.. so what exactly should I select if I want to try it then install it? 

> "Finally, you can choose whether you want your USB system to be persistent between boots, or static like a live CD (changes will stay or discarded). Adjust the slider to choose how much space Ubuntu will have on the disk to expand to, or select the Discarded on shut-down option(this will remove all changes you done on the ubuntu on your flash)."

I don't exactly know what that means, haha.

---

### Post by kerry_s on 2010-08-14
they both will work live, so you can try it before install. they both will install.

the difference is with the first option you can change things & it will remember. for example you change the background, it will always boot with your new background.

the second option you can change things to, but it will not be saved.

i select the second option so i know it's a clean install. i save the installer in case i need to reinstall.


don't worry about it, you can redo the key on the new install for next time. it's not a big deal. :D

---

### Post by hooligandisco on 2010-08-14
i used a 4 GB USB and tried the 10.04 before tryin to install it and i enjoyed it.

i restarted it to install it instead of try it and as it went through the process it continued to give me errors that i know nothing about.

there are only 7 steps to the installation and i couldn't even get past no.3!

Here is a list of a few errors i could write down:

> ubi-language crashed failed with exit code 1
ubi-migrationassistant crashed failed with exit code 141
ubi-console-setup crashed failed with exit code 2
ubi-usersetup crashed failed with exit code 10

Each error said something along the lines of "continue or installation may fail entirely or maybe broken. Refer to /var/log/syslog for more info"

I then cancelled the installation since it left me no other options. D'OH No idea what to do now... **Is 10.04 even worth it?**

---

### Post by kerry_s on 2010-08-14
try writing the iso to usb again, if it fails you might have a bad download.

---

### Post by hooligandisco on 2010-08-15
Finally installed last night and I am happy to say I am running 10.04 now. 

A big thanks to everyone who helped me this week, i appreciate it!

---

### Post by kerry_s on 2010-08-15
let us know if you need help with anything else, lots of changes in 10.04 compared to older versions.

i recommend you install "ubuntu-restricted-extas" & get all the good stuff for media enjoyment. :D

---

