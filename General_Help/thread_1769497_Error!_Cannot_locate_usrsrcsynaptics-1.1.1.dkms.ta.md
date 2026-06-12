---
title: "Error! Cannot locate /usr/src/synaptics-1.1.1.dkms.tar.gz.File does not exist."
date: 2011-05-28
forum: General Help
---

### Post by The_Autonomist on 2011-05-28
I keep getting this error message whenever I try to upgrade, install, or uninstall something: 

> Error! Cannot locate /usr/src/synaptics-1.1.1.dkms.tar.gz. File does not exist.

Does anyone know what's going on?????:confused:

---

### Post by linuxinstalledfromhdd on 2011-05-28
Try running:

dpkg --configure -a

---

### Post by The_Autonomist on 2011-05-28
I tried that and I got the exact same error message. After i gained root privileges (which it made me do) this is what it told me:

> Setting up synaptics-dkms (1.1.1) ...
Loading new synaptics-1.1.1 DKMS files...

Error! Cannot locate /usr/src/synaptics-1.1.1.dkms.tar.gz.
File does not exist.
dpkg: error processing synaptics-dkms (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 synaptics-dkms


???????????????:confused:

---

### Post by The_Autonomist on 2011-05-28
**??????????????????/**

---

### Post by The_Autonomist on 2011-05-28
NO ONE on this entire forum knows the answer to this problem???

---

### Post by drs305 on 2011-05-28
I may be able to tell you how to avoid getting the error message by renaming the post-installation script. It doesn't fix the problem but it's a workaround.
```

sudo mv /var/lib/dpkg/info/synaptics-dkms.postinst /var/lib/dpkg/info/synaptics-dkms.postinst.bad
sudo apt-get update 
```

I do not have that package on my system. Type to .../synaptics-d  and then press TAB. If the file exists as I posted it should autocomplete.

If the update works, try reinstalling whatever package you were trying to install, as well as the synaptics... one above.

What we are doing is removing the post-installation script. Finding the missing folder/files would be a better solution, but I can't help you with that; the error is telling you what file it is looking for and where it is located.

---

### Post by The_Autonomist on 2011-05-28
THANK YOU FOR YOUR RESPONSE! I'm going to try that, but something else you said in your post made me think and re-read the error message I kept getting. So, i went and looked for the file where it should be, and it wasn't there. There's a regular folder named "synaptics-1.1.1" in the directory, but not a TAR.GZ file, which is what it's looking for. I don't know how to make a tar.gz, so i decided to look online to see if i could download the package. I tried to re-install the synaptics deb package, but i received another error message. so, i decided to go into package managers, and completely remove it, and then re-install it to see if that would fix my issue.

It didn't and it gave me yet another error message, the same one i got the first i tried to reinstall the package without removing it first. even after removing it, it still gave me this error message.

> Error! Bad return status for module build on kernel: 2.6.38-9-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/synaptics/1.1.1/build/ for more information.
0
0
ERROR: binary package for synaptics: 1.1.1 not found
dpkg: error processing synaptics-dkms (--install):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 synaptics-dkms
:confused::confused::confused::confused: Fml. Any thoughts??

---

### Post by The_Autonomist on 2011-05-29
I also just tried your solution, and it did not work. =/

---

### Post by Macskeeball on 2011-05-29
Here's a thread in which someone else had the same problem and got the help needed to solve the problem: [http://ubuntuforums.org/showthread.php?t=1738264](http://ubuntuforums.org/showthread.php?t=1738264)

---

### Post by The_Autonomist on 2011-05-29
I  just tried the solution you posted! I won't know if it works until I get another major update, but he was indeed having the exact same problem that I was. Thank you!!!!

---

### Post by cbennett926 on 2011-08-01
Please mark this as Solved and reference that you used the link that assited you in it being solved.

---

