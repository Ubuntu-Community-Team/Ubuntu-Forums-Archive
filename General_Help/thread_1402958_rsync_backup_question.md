---
title: "rsync backup question"
date: 2010-02-09
forum: General Help
---

### Post by Bartly on 2010-02-09
I need to backup ubuntu data to a windows file share. I have the file share mounted in ubuntu and can successfully copy files to it and backup mysql to it.
To backup files/folders my research indicates I should use rync. The rub is that every article I have read says to automate rysnc by using ssh keys. I don't believe that is going to on a wndows file share. We will not be running ssh on the windows server, and I do not require that kind of security in this private network. So how do I automate the logon when using a rsync script with cron? I am sure htis is simple but I am a newb, thanks for helping. Also, if there is some other way besides rsync I should be doing this I am all ears.

---

### Post by HermanAB on 2010-02-09
Howdy,

Those guides you read are correct.  You really should install Cygwin with SSHD.  Then use rsync to connect to the Windows machine over port 22 with "rsync -e ssh" and public keys.

A have frequently found that a Windows machine can be crashed and unusable, while you can still log into SSH, fix it and reboot it remotely.  Soooo....

---

### Post by Bartly on 2010-02-09
> **HermanAB said:**
> Howdy,
 
Those guides you read are correct. You really should install Cygwin with SSHD. Then use rsync to connect to the Windows machine over port 22 with "rsync -e ssh" and public keys.
 
A have frequently found that a Windows machine can be crashed and unusable, while you can still log into SSH, fix it and reboot it remotely. Soooo....
 
Although I understand the Linux communities (which I consider myself a part of)  disdain for Windoze (and I am a Windoze Network Manager because, hey, its a job!) I am not concerned about my server crashing to the point of needing ssh to get into it, hasn't happened in the six years I have been I.T. Manger here. Plus it's just a host for the SAN where the data really resides (Ha, you are correct, the SAN runs on Linux, yay!). 
 
So again, if SSH is the only way to do it I will look into it, but I assume there is some way to emulate sudo in a script. Meanwhile I'll take a look at Cygwin.  
Thanks

---

### Post by Bartly on 2010-02-12
Since the windows file share is mounted locally it is not considered a remote server and you do not use ssh (my confusion in my original post). So I finally figured out to simply create a shell script for the rsync backup and run it as a root cron job. In this case it needs to be root to access the file share. 
 
[https://help.ubuntu.com/community/MountWindowsSharesPermanently](https://help.ubuntu.com/community/MountWindowsSharesPermanently)
 
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)
 
Now I am happy as a clam because I have a production Linux server running in my Windows network. Ubuntu is a great community.

---

