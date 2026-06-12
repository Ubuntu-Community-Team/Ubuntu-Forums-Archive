---
title: "I must restart smbd to see printer shares!"
date: 2011-08-12
forum: General Help
---

### Post by bradcan on 2011-08-12
Today I discovered that my samba printer shares do not appear until I do:
sudo restart smbd

Presumably because smbd is starting before cups?

A little searching reveals that samba is started by the aptly named upstart!

What is the proper way to fix this?

I'm running a fresh upgrade to 10.04

The reason for this problem is that /etc/printcap does not exist at the time smbd is started! One solution is:

Copy the cups generated /etc/printcap to /etc/samba/printcap and include the following line in /etc/samba/smb.conf:

printcap name = /etc/samba/printcap

The new printcap should be edited to only include relevant printers. Also make sure load printers = yes is also present.

---

### Post by Toz on 2011-08-12
You can delay the starting of smbd via upstart by editing the **/etc/init/smbd.conf** file. Edit the "start on" line to include **and stopped rc** so that it doesn't start until all other startup scripts have been executed. In 11.04, the line looks like this:
> start on (local-filesystems and net-device-up)
The edited version would look like:
```
start on (local-filesystems and net-device-up and stopped rc)
```

---

### Post by thunderhooves on 2011-11-27
> **Toz said:**
> You can delay the starting of smbd via upstart by editing the **/etc/init/smbd.conf** file. Edit the "start on" line to include **and stopped rc** so that it doesn't start until all other startup scripts have been executed. In 11.04, the line looks like this:

The edited version would look like:
```
start on (local-filesystems and net-device-up and stopped rc)
```

This worked perfectly for me in a clean install of ubuntu 10.04. I can't tell you how many other "fixes" I tried and how many incredibly complicated workarounds I avoided prior to this simple solution. I was concerned about the following line:

stop on runlevel [!2345]

which I thought might stop the service at run level 2. What does that line do?

---

### Post by Toz on 2011-11-28
> **thunderhooves said:**
> I was concerned about the following line:

stop on runlevel [!2345]

which I thought might stop the service at run level 2. What does that line do?

**!** means NOT, so, in essence, stop when the runlevel being changed to is NOT 2,3,4,5 (in other words, only 0,1 or 6). See: [http://upstart.ubuntu.com/cookbook/]("http://upstart.ubuntu.com/cookbook/") (Section 7.1).

---

### Post by thunderhooves on 2011-11-28
I expected it must be something like that.

My network service busted again. What I realized was that in my  **/etc/init/smbd.conf** file for ubuntu 10.04 there never was a net-device-up entry. The original line in my file was:

     start on local-filesystems 

 not:

     start on (local-filesystems and net-device-up) 

like it was in your ubuntu 11.04 release. I removed the entry and added the condition you recommended to change it to:

     start on (local-filesystems and stopped rc) 

 for my ubuntu 10.04 release and it seems to work OK now. I have tested all known combinations of conditions. 

For some reason the smbd process never shows up in the system monitor. Even after I restart smbd when the assigned process ID is listed on the terminal I have only seen the smbd process show up in the system monitor once and even then it didn't have the process ID that had just been assigned to it. 

There is something fishy with smbd in this 10.04 release. I never had this problem in 8.04. I have also had a dual-boot with WinXP problem that took a long time to solve that I never had in 8.04. In 10.04 the distribution does not seem to work uniformly across all platforms. But, then, why should it?

Thanks again for your help.

---

### Post by Doug S on 2011-12-01
This was a very useful and timely thread, and it helped me solve a printing problem I have had for almost a year now. I only recently realized I even had a problem because it only occured after re-boot, which I rarely do, and because the problem was only on my wife's Windows 7 LapTop, and because the problem wouldn't exist the next day. I checked the logs and sure enough on the daily re-start of stuff, cups would be before samba. I have server 10.10, and so my smbd.conf line was as thunderhooves.

---

