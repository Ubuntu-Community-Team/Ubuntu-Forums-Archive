---
title: "SSHFS and FUSE can't get working."
date: 2010-03-14
forum: General Help
---

### Post by jflcooper on 2010-03-14
Hi Everyone,

Sorry if this is in the wrong place i am new to these forums and would like your help if possible.

I am running Ubuntu 8.10 on a webbynode account and am attempting to create a kind of network drive to another one of my servers running the exact same thing.

I have followed instructions from many different sites on getting this up and running but still running into problems.

What i have done.

```

sudo apt-get install sshfs

```I then added the user to the 'fuse' group
```

sudo adduser root fuse

```I then tested a connection with  the following example
```

sshfs xxx.xxx.xxx.xxx:/path/to/local /path/to/remote

```Which then produces this
```

fuse: device not found, try 'modprobe fuse' first

```so i do as it asked
```

modprobe fuse

```and get this
```

FATAL: Module fuse not found.
FATAL: Error running install command for fuse

```Now... sorry for dragging on but i have tried ABSOLUTELY EVERYTHING... including restarting the server stopping it then starting several times to even installing fuse manually without any success.

can anyone help PLEASE!!!!!!!

Is there a better way of doing what i need?

Cheers
Coops

---

### Post by gare on 2010-03-14
Hello,


I'm no expert on fuse, but a search of your error produces some interesting results, such as ". Not loading the module automatically is a bug." at

[http://myy.helia.fi/~karte/mount_sshfs.html](http://myy.helia.fi/~karte/mount_sshfs.html)

you are typing 'sudo' before your commands?

The latest version of fuse may give you better results.

---

### Post by jflcooper on 2010-03-14
Hi gare,

Thanks for the reply. I to checked that article out and it was of no support unfortunately. i have tried installing FUSE manually version 2.8.3 which i think is the latest from what i could find but it still doesn't load it as a module like i require.

Do you know of any further documentation about installing fuse 2.8.3 manually and getting it to display as a module? i have done this

```

lsmod

```

but it still isn't showing in there...
If you know of any docs/tuts i will try them also.

Cheers
Coops

> **gare said:**
> Hello,


I'm no expert on fuse, but a search of your error produces some interesting results, such as ". Not loading the module automatically is a bug." at

[http://myy.helia.fi/~karte/mount_sshfs.html]("http://myy.helia.fi/%7Ekarte/mount_sshfs.html")

you are typing 'sudo' before your commands?

The latest version of fuse may give you better results.

---

### Post by jflcooper on 2010-03-14
gare,

I will redeploy the server again as a fresh install and do the article suggested again from scratch and see if it helps. will post results.

Cheers
Coops

---

### Post by jflcooper on 2010-03-14
Ok i followed that article and still no luck... this is stupid...

Surely someone has to of come across this problem and found a fix or something??

---

### Post by gare on 2010-03-14
Hi -

Googling around for your error suggests a kernel / version incompatibility:

> If you do &#8216;modprobe fuse&#8217;, as they tell you to, and you get:
modprobe fuse
FATAL: Module fuse not found.

That means your running kernel is not the same version as the one you compiled with. You have two options here:
1) you can upgrade your kernel by typing: yum update kernel
2) find the source files for the kernel you have running and recompile fuse.

source: [http://crazytoon.com/2008/10/07/sshfs-how-do-you-install-sshfs-and-fuse-centoslinuxredhat/](http://crazytoon.com/2008/10/07/sshfs-how-do-you-install-sshfs-and-fuse-centoslinuxredhat/)


---

### Post by gmargo on 2010-03-14
> **jflcooper said:**
> I will redeploy the server again as a fresh install and do the article suggested again from scratch and see if it helps. will post results.
Check if FUSE is compiled into the kernel - it may not be a module.

About a week ago I posted how to figure that out over here: [http://ubuntuforums.org/showpost.php?p=8920533&postcount=2](http://ubuntuforums.org/showpost.php?p=8920533&postcount=2)

By default, the 9.10 Karmic generic kernel has FUSE compiled in.  But the default 8.10 Intrepid server kernel does not.  _Exactly_ what kernel are you running?

---

### Post by jflcooper on 2010-03-14
Hi gare and gmargo,
 
First... Thank you both soooooo much for replying haha 
 
Ok i checked my kernel version and its **2.6.18-92.1.22.ex15xen**
 
hope this helps?
 
So gare and gmargo if i run sudo update kernel this should fix my problem? and i won't have to install fuse manually yeah?
 
Also doing this... will it stuff up my apache and ruby and anything else etc etc?
 
Thanks again for all your help.

Cheers
Coops

---

### Post by gmargo on 2010-03-14
> Ok i checked my kernel version and its **2.6.18-92.1.22.ex15xen**I believe that is a CentOS or RHEL kernel version, not an Ubuntu 8.10 kernel version.  Is this correct?

---

### Post by jflcooper on 2010-03-14
ummm i'm not sure... i am sure its Ubuntu only because when i login to my webbynode account it tells me the server is ubuntu 8.10.
 
 
ohhh i just checked on the net how to check the version so i did this
 
```

cat /etc/issue

```
 
and it said...
 
```

Ubuntu 8.10 \n \l

```
 
Cheers
Coops

---

### Post by jflcooper on 2010-03-15
From what i have just read about kernel versions etc... it looks like i have an old version i have tried a few things to try and update it but it has failed.

Can you please tell me how to update my kernel to the latest version?

Cheers
Coops

---

### Post by gmargo on 2010-03-15
The proper command to show the distribution version is "lsb_release -a".  The proper command to show the kernel version is "uname -a" and/or show which linux-image-* package is in use.

---

