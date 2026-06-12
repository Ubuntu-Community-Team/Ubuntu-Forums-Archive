---
title: "Unable to run DSET tool"
date: 2010-10-08
forum: General Help
---

### Post by Azirus on 2010-10-08
Hello everyone I am very very new too linux, so please bare with me :) and im sorry if I created this thread in the wrong spot.
 
We had someone setup a webserver for us and they installed Ubuntu Server on the new server and im not sure what setting were setup. 
 
Recently the server has been restarting at specific times either around 3:30pm or 6:00pm. So I contacted Dell incase this was a hardware issue and they told me to run DSET on the server. So I downloaded the Linux version of the file onto my flash drive, mounted it and copied the file to server and tried to run it using ./delldset_v2.0.0.119_A01.bin and I just get alot of 
 
./delldset_v2.0.0.119_A01.bin: 49: typeset: not found
./delldset_v2.0.0.119_A01.bin: 50: typeset: not found
./delldset_v2.0.0.119_A01.bin: 51: typeset: not found
./delldset_v2.0.0.119_A01.bin: 56: typeset: not found
./delldset_v2.0.0.119_A01.bin: 59: typeset: not found
 
and at the bottom of the "typeset: not found" errors it says 
 
./delldset_v2.0.0.119_A01.bin: 366: Bad substitution
./delldset_v2.0.0.119_A01.bin: 1: typeset: not found
sleep: missing operand
Try `sleep --help' for more information.
 
There is no GUI installed on this server so im not sure if im typing in the commands wrong or if I need to do something else to make it work.
 
The server is a Dell PowerEdge 1900 and the OS is Ubuntu Server.
 
Any help would be greatly appreciated. Thanks :)

---

### Post by ryan.dooley on 2011-03-08
I'm pretty sure this isn't going to work easily.

* Dell's DSET package assumes that /bin/sh is really BASH.
* DSET really wants to extract and install an RPM package.
* You can extract the rpm and use alien on it, however, there are issues with converting it to a DEB package, I had better luck with producing a Slackware TGZ.
* The binaries look for /lib/ld-linux.so.2 for my x86_64 platform.

I've mostly given up on trying to convert the package today so I just ended up telling Dell I'm running Ubuntu and I can't get logs for you with the DSET tool.

---

### Post by Azirus on 2011-03-08
Thanks Ryan I gave up on it as well and told them I couldn't generate the reports.

---

