---
title: "Installing Handbrake"
date: 2009-07-06
forum: General Help
---

### Post by Bradj47 on 2009-07-06
I just downloaded a .deb package from [http://handbrake.fr/?article=download](http://handbrake.fr/?article=download) but I can't install it. When I try it gives me this error: 
> Could not open 'HandBrake-0.9.3-Ubuntu_GUI_i386.deb' The package might be corrupted or you are not allowed to open the file. Check permissions of the file.
So I did a chmod 777 on it and I tried again and got the same thing. Then I ran this command on it: 
```

brad@rockstar:~/Desktop$ sudo gdebi "HandBrake-0.9.3-Ubuntu_GUI_i386.deb"
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done
Failed to open the software package
The package might be corrupted or you are not allowed to open the file. Check the permissions of the file.

```
And of course it didn't work. So then I tried downloading the other file, CLI (Ubuntu 8.10 x86 Binaries). The other one was  	GTK GUI (Ubuntu 8.10 x86 Binaries). I extracted the file from the .tgz file and got a file called HandbrakeCLI. I don't know what to do with this. I also tried sudo apt-get handbreak and the package wasn't found. So I'm stuck now. Can anyone help in any way? Like give me a valid link or tell me how to open either of these files?

---

### Post by jkarcz on 2009-07-07
Link looks good.  Have you tried running md5sum on the file to see what the checksum matches what's on the site?

Tried sudo apt-get install?

---

### Post by mc4man on 2009-07-07
It may or may not be because you're on jaunty (,,?) and it's an intrepid package.

Here's a well done ppa with current handbrake versions for 8.04 thru 9.04

Either add the repo to your sources and install from synaptic or apt-get or download and install manually.

 to do manually dl and install the handbrake-common first, then the handbrake-gtk

[https://edge.launchpad.net/~handbrake-ubuntu/+archive/ppa](https://edge.launchpad.net/~handbrake-ubuntu/+archive/ppa)

---

