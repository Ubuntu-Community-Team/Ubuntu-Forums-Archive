---
title: "Trying to get ClamAV"
date: 2010-11-27
forum: General Help
---

### Post by I_Use_Windows on 2010-11-27
I have a nasty little virus on my computer, which runs x64 win7. It can't boot, and my repair disc and several antivirus discs won't work either.

I have Ubuntu on a disc though, and it works. I'm on it trying to get an some AV happening. Everyone seems to use clam so thats what im trying to get. It isn't really working though. This is what my terminal looks like:
> ubuntu@ubuntu:~$ sudo apt-get install clamav
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  clamav-base clamav-freshclam libclamav6
Suggested packages:
  clamav-docs libclamunrar6
The following NEW packages will be installed:
  clamav clamav-base clamav-freshclam libclamav6
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 4,798kB of archives.
After this operation, 11.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main libclamav6 0.96.1+dfsg-0ubuntu0.10.04.1
  404  Not Found [IP: 91.189.92.167 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main libclamav6 0.96.1+dfsg-0ubuntu0.10.04.1
  404  Not Found [IP: 91.189.92.169 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main clamav-base 0.96.1+dfsg-0ubuntu0.10.04.1
  404  Not Found [IP: 91.189.92.169 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main clamav-freshclam 0.96.1+dfsg-0ubuntu0.10.04.1
  404  Not Found [IP: 91.189.92.169 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main clamav 0.96.1+dfsg-0ubuntu0.10.04.1
  404  Not Found [IP: 91.189.92.169 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/clamav/libclamav6_0.96.1+dfsg-0ubuntu0.10.04.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/clamav/libclamav6_0.96.1+dfsg-0ubuntu0.10.04.1_amd64.deb)  404  Not Found [IP: 91.189.92.169 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-base_0.96.1+dfsg-0ubuntu0.10.04.1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-base_0.96.1+dfsg-0ubuntu0.10.04.1_all.deb)  404  Not Found [IP: 91.189.92.169 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-freshclam_0.96.1+dfsg-0ubuntu0.10.04.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/clamav/clamav-freshclam_0.96.1+dfsg-0ubuntu0.10.04.1_amd64.deb)  404  Not Found [IP: 91.189.92.169 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/clamav/clamav_0.96.1+dfsg-0ubuntu0.10.04.1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/clamav/clamav_0.96.1+dfsg-0ubuntu0.10.04.1_amd64.deb)  404  Not Found [IP: 91.189.92.169 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ubuntu@ubuntu:~$ 

I really need to get this working, can anyone tell me what I need to do? Also remember i'm a complete linux noob.

---

### Post by I_Use_Windows on 2010-11-27
Wow, furiously spamming the comand line worked./ Ok now I have clamav... but it doesnt work. Heres my terminal:

> ubuntu@ubuntu:~$ clamscan -r --remove=yes /media/E4C2CC93C2CC6AFE
LibClamAV Error: cli_loaddb(): No supported database files found in /var/lib/clamav/
ERROR: Can't open file or directory

----------- SCAN SUMMARY -----------
Known viruses: 0
Engine version: 0.96.3
Scanned directories: 0
Scanned files: 0
Infected files: 0
Data scanned: 0.00 MB
Data read: 0.00 MB (ratio 0.00:1)
Time: 0.008 sec (0 m 0 s)
 

Maybe I'm doing something wrong. Any help, please?

---

### Post by WorMzy on 2010-11-27
Run freshclam first to obtain a virus definition database.

```
sudo freshclam
```

Then run clamscan (preferably with sudo).

```
sudo clamscan -r --remove=yes /media/E4C2CC93C2CC6AFE
```

Be careful with the remove flag, clamscan may return false positives. I'd suggest using the -i and --move flags instead.

e.g.

```
sudo clamscan -ri --move=/home/$USERNAME/ /media/E4C2CC93C2CC6AFE
```

---

### Post by jmszr on 2010-11-27
I_Use_Windows,

If clam doesn't get the job done, I suggest that you try the Trinity Rescue Kit: [http://trinityhome.org/Home/index.php?pid=1](http://trinityhome.org/Home/index.php?pid=1) .

It's quite a useful tool(s).

---

### Post by I_Use_Windows on 2010-11-27
Thanks both. I might try TRK because im sick to death of ubuntu :D sorry guys.

Will TRK work if I just copy the .iso onto my USB? i've gone through like 3 (expensive) blank CD's.

EDIT: this download is gonna take ages. Wormzy, could you explain the "sudo clamscan -ri --move=/home/$USERNAME/ /media/E4C2CC93C2CC6AFE" will it just move the files to my desktop(desktop?) 

Also, where does all this crap im downloading get stored?

---

### Post by wilee-nilee on 2010-11-27
Many of the AV providers have live cd's for use. They boot download the latest definitions and go afder those nasty critters h ere is one link.
[http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/](http://www.techmixer.com/free-bootable-antivirus-rescue-cds-download-list/)

You should be running your MS setup in a limited account anyway with very strong passwords if your not doing this already. Cuts out about 90% of the danger except the one between the chair and the screen.;) That is the outlier if you understand statistics.

---

### Post by I_Use_Windows on 2010-11-27
So how do I run these off a memory stick? can i just put the .iso on there or what? I also burnt kapersky to a CD and it didnt do anything. (yes, i have my boot order sorted) It went to the black screen wit hthe flashing white underscore.

EDIT: is it possible for the virus to ruin rescue discs or not?

---

### Post by WorMzy on 2010-11-28
This is tricky to explain, but basically, you have to burn the image, not the iso. The iso contains the image, but the iso itself is just a file. Most CD burning applications will have several options, one of which should be "burn image", or "create disk from iso", you'll need to look at your burning software to see if you can find this option.

---

