---
title: "mdadm 3.0.2 won't read mdadm.conf file"
date: 2009-09-27
forum: General Help
---

### Post by Loulisk on 2009-09-27
Hello everybody,

I am having trouble with the latest version of mdadm on Ubuntu 9.04.

A couple of days ago I realised that the mdadm that is included in the repositories (and accessible through apt-get) is pretty ancient (version 2.6 or something) compared to the latest version (3.0.2), found on [http://www.kernel.org/pub/linux/utils/raid/mdadm/](http://www.kernel.org/pub/linux/utils/raid/mdadm/). So, I decided to go with the new and improved version.

Of course, as it usually happens, my fondness for "new and improved" versions proved to be a recipe for frustration. 

I downloaded mdadm-3.0.2.tar.gz, unzipped it, and run "sudo make" and "sudo make install" commands. After that I was successful at creating a 4 partition raid 5 array, following [this]("http://bfish.xaedalus.net/?p=188") and [this]("http://ubuntuforums.org/showthread.php?t=517282") guides in conjunction. The partition mounted, the data was synchronized, and all was well in the kingdom of Denmark - so far.

For anyone who has used mdadm, the challenge is in the reboot. According to the guides, both /etc/mdadm/mdadm.conf and /etc/fstab need to be edited, so during boot mdadm will assemble the /dev/md0 array and then fstab will mount it. I have tried this method with the repository mdadm and it worked like a charm, on every boot I found the array waiting eagerly for me, mounted and ready to go.

When I tried the exact same procedure with mdamd 3.0.2, I run into trouble. The program hadn't created a /etc/mdadm/mdadm.conf, neither an /etc/mdadm.conf file. When I manually created one such file on both locations (/etc/mdadm/ and /etc/), and provided the correct array details (the very same that worked with repository mdadm), the program promptly ignored both the files, and I had to manually assemble and mount the array on each boot.

(btw, after the manual assembly and mount, the raid is completely available until the next reboot)

I seem to have the exact same problem with user Clievers on [this]("http://ubuntuforums.org/showthread.php?t=872092") thread, but he doesn't seem to have found any satisfactory answers.

Could you please help me make mdadm recognize the mdadm.conf file as it's configuration file?

Thanks in advance

Angelos

p.s. :Excuse my average English, it isn't my mother language.

---

### Post by Loulisk on 2009-09-28
Searching for the cause of my problem, I paid closer attention to the compilation of mdadm 3.0.2

As I found out, it mentions several times the paths /etc/mdadm.conf and /etc/mdadm/mdadm.conf, and I think it's hardly a coincidence

Could it be that I am doing something wrong during the compilation?

I have installed the building-essential and gcc packages from the repos, then I just type "sudo make" in the mdadm-3.0.2 directory.

I attach the complete message of the compilation

---

