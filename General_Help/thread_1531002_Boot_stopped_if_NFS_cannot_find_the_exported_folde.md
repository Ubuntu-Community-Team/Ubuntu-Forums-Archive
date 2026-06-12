---
title: "Boot stopped if NFS cannot find the exported folder"
date: 2010-07-14
forum: General Help
---

### Post by Turtle.net on 2010-07-14
I have several ubuntu PCs at home, so I decided to use only one /var/cache/apt/archives.
So I have decided to export the folder from on box via NFS.
The other two boxes can mount the NFS folder without the single problem, access it, and write to it.
So I decided to automount this folder at boot. I added this to my /etc/fstab file 
```
#Entry for nfs apt/archives mount
huygens:/var/cache/apt/archives /var/cache/apt/archives nfs rsize=8192,wsize=8192,timeo=14,hard,intr
```

The problem is when I boot up my machine and the server is not accessible (i'm not at home for instance), I receive during boot the error message saying that the export cannot be located, and that I should type S to pass the mount of this folder.
The problem is : if i don't type on the S early enough (let say i started my PC then went away to grab a cofee) the boot process enters an endless loop, and I cannot bring it back. The system is still responsive (i can press Escape and see the lines telling that it tries to reach the server and fail ... then try again).
In few words : the timeo option doesn't seem to work.

Any idea ?
(I also tried the option soft instead of hard for the mount point, no luck with that)

---

### Post by bodhi.zazen on 2010-07-14
Add noauto to the options.

You will then need to either manually mount the nfs share, or better, try autofs

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

---

### Post by Turtle.net on 2010-07-14
> **bodhi.zazen said:**
> Add noauto to the options.

You will then need to either manually mount the nfs share, or better, try autofs

[https://help.ubuntu.com/community/Autofs](https://help.ubuntu.com/community/Autofs)

Autofs sounds cool, but only solve one half of the problem.
After some testings (not scientific at all) it seems that i could use the options soft,timeo=7,retrans=1,intr

If I could use both (timeo, soft, retrans and autofs) that should do the trick.
I will do some testing and post the results

---

### Post by Turtle.net on 2010-07-14
In the end that was pretty simple.
I installed autofs
```
$ sudo apt-get install autofs

```then I commented out everything in /etc/auto.master then I added this line at the end
```
/- /etc/auto.nfs

```and i created /etc/auto.nfs with this line in it
sudo nano /etc/auto.nfs 
```
/var/cache/apt/archives -rw,soft,intr,rsize=8192,wsize=8192 huygens:/var/cache/apt/archives

```
Then we have to restart autofs
```
$ sudo service autofs restart

```
And now it works !
autofs handles pretty well the situation when the server is not reachable, after a minute or less an error is returned when you try to reach the server. I tried different timeo options with no improvements.

For me it's really good since i can even stop autofs with one command if I want to install something (then apt-get needs access to the folder) without the server reachable.

Thanks a lot

I used these pages to solve the entire puzzle :
[Automounting a Remote Directory Using a Direct Map]("http://docs.hp.com/en/B1031-90061/ch03s07.html?btnPrev=%AB%A0prev")
[Common NFS Mount Options]("http://www.redhat.com/docs/manuals/enterprise/RHEL-5-manual/Deployment_Guide-en-US/s1-nfs-client-config-options.html")
[Mounting NFS File Systems using autofs]("http://www.redhat.com/docs/manuals/enterprise/RHEL-3-Manual/sysadmin-guide/s1-nfs-mount.html")

---

### Post by bodhi.zazen on 2010-07-14
Glad it worked for you. Autofs is sweet.

I agree it takes a little time to understand the concept, but IMO it is well worth it.

---

