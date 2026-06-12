---
title: "How do i compile/install SiS Drivers? I have video problem with the current Drivers"
date: 2009-09-21
forum: General Help
---

### Post by GrfyGrumpyBear on 2009-09-21
Hi,

I have a laptop with SiS 661fx and the problem is that the current installed drivers sucks 100% because the screen stucks and i can't scroll down to webpages or see any video from youtube for example or with any video player,even VLC or Totem.

The installed driver package is the following: xserver-xorg-video-sis package

I found a sis wikipage with information about sis gpus on linux,and i found some drivers named "Winischhofer resurected"
[http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=OpenSourceDrivers](http://ncc-1701a.homelinux.net/~linux-sis/index.php?page=OpenSourceDrivers)

From what i read there they supposed to be one of the best sis drivers,and i can't wait to install them.

The problem is...

How do i compile drivers? I found some info on the net about compiling with some commands but i didn't understand thing and the commands doesn't work.

Can someone explain me almost step by step?

I'm using Ubuntu 9.04.

---

### Post by GrfyGrumpyBear on 2009-09-22
bump? :S

---

### Post by GrfyGrumpyBear on 2009-09-22
Second bump...

On the third bumb i will go nuts and i'll get out naked screaming "I NEED LINUX HELP DAMMIT":)

---

### Post by 3rdalbum on 2009-09-22
**Backup your data first.** If you can't install graphics drivers without extra help, then I'm sure you can't recover your earlier graphics drivers if the new ones stuff up.

Install the kernel-headers-generic package. Install the xorg-dev package. Install build-essential.

Open a terminal and navigate it to the directory with the source code of the driver you downloaded - or you can use the "nautilus-open-terminal" package (which puts an "Open in Terminal" entry into your right-click menu after you log in again).

Run the commands that it says to run. If it says to run a command as root, put "sudo" in front of it. If it says to run the "su" command, instead run "sudo -i".

In future, don't just say "the commands didn't work"; tell us what error message was given, there's usually a simple explanation.

---

### Post by GrfyGrumpyBear on 2009-09-22
Well thank you very much for your response on this shithole crap site but did you see the news?

I ain't DID ANYTHING! hahaha yes,i'm a badass lucky son of a bitch,after HOURS of searching on the net about how to compile a f&#965;cking driver package,the solution came from the sky!

I found precompiled deb package and i installed it smoooooth and fast baby :)

hehehe but again,no 2d acceleration enabled because when it's enabled if i open youtube tab the damn thing would throw me back to the login screen.

Well.... again,i ain't give a sh&#943;t,thank you very much :)

---

### Post by geri1994 on 2009-11-24
> **GrfyGrumpyBear said:**
> Well thank you very much for your response on this shithole crap site but did you see the news?

I ain't DID ANYTHING! hahaha yes,i'm a badass lucky son of a bitch,after HOURS of searching on the net about how to compile a f&#965;cking driver package,the solution came from the sky!

I found precompiled deb package and i installed it smoooooth and fast baby :)

hehehe but again,no 2d acceleration enabled because when it's enabled if i open youtube tab the damn thing would throw me back to the login screen.

Well.... again,i ain't give a sh&#943;t,thank you very much :)

 PLEASE can you tell mee what package do you download :D

---

