---
title: "Error: &quot;Please install &quot;network-manager&quot; via your normal software channels.&quot;"
date: 2012-10-08
forum: General Help
---

### Post by Katniss Everdeen on 2012-10-08
I accidentally removed the network packages, I have downloaded them on another computer. When I try to install it. I get "Error: "Please install "network-manager" via your normal software channels. Only install this file if you trust the origin."

I can't click "Install" button, it's not lit up. What do I do?

---

### Post by HiImTye on 2012-10-08
if you go to 'software sources' then you can enable the LiveCD/USB. then you can mount the LiveCD/USB and use it to install network-manager

---

### Post by Katniss Everdeen on 2012-10-08
> **HiImTye said:**
> if you go to 'software sources' then you can enable the LiveCD/USB. then you can mount the LiveCD/USB and use it to install network-manager

I've done this. I copied the deb files to the desktop, still have the same problem.

---

### Post by HiImTye on 2012-10-08
just install them from the software center (or synaptic, or apt-get, or w/e you use)

---

### Post by Katniss Everdeen on 2012-10-08
> **HiImTye said:**
> just install them from the software center (or synaptic, or apt-get, or w/e you use)
 
Software center is what I use.

I tried to install it via command line, but it didn't work.

---

### Post by HiImTye on 2012-10-08
try this
```
sudo apt-get update; sudo apt-get install network-manager
```

---

### Post by Katniss Everdeen on 2012-10-08
> **HiImTye said:**
> try this
```
sudo apt-get update; sudo apt-get install network-manager
```

Didn't work, probably because it doesn't have Internet.

---

### Post by HiImTye on 2012-10-08
if you enabled the liveCD/USB as a software source, that wouldn't matter

post the output of this:
```
apt-cache policy network-manager
```

---

### Post by Katniss Everdeen on 2012-10-08
> **HiImTye said:**
> if you enabled the liveCD/USB as a software source, that wouldn't matter

post the output of this:
```
apt-cache policy network-manager
```

> office1@Office1:~$ apt-cache policy network-manager
network-manager:
  Installed: (none)
  Candidate: 0.9.4.0-0ubuntu4.1
  Version table:
     0.9.4.0-0ubuntu4.1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates/main i386 Packages
        100 /var/lib/dpkg/status
     0.9.4.0-0ubuntu3 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main i386 Packages
Here it is, sorry for taking so long.

How do I install the package from the CD? All packages have that error.

---

### Post by Katniss Everdeen on 2012-10-08
Bump. Really important.

---

### Post by Katniss Everdeen on 2012-10-08
I'm going to reinstall the OS. It's all I can do.

---

### Post by pqwoerituytrueiwoq on 2012-10-08
you may be able to install the deb with [FONT=Courier New]dpkg -i /path/to/my.deb[/FONT]
you should be able to enable the cd source from [FONT=Courier New]software-properties-gtk[/FONT]

---

### Post by steeldriver on 2012-10-08
... or you could likely just bring up a temporary interface via the old networking service (provided you didn't remove those packages as well) via /etc/network/interfaces - like in this thread:

[http://ubuntuforums.org/showthread.php?t=2048040](http://ubuntuforums.org/showthread.php?t=2048040)

---

### Post by Katniss Everdeen on 2012-10-08
> **pqwoerituytrueiwoq said:**
> you may be able to install the deb with [FONT=Courier New]dpkg -i /path/to/my.deb[/FONT]
you should be able to enable the cd source from [FONT=Courier New]software-properties-gtk[/FONT]


I tried to install the deb file, not sure why it won't work. I can try again and post the outcome of it.

---

### Post by HiImTye on 2012-10-09
apparently just enabling the repository isn't enough. you also need to use apt-cdrom to tell Ubuntu the mount point. I'm not sure if it will work with a USB, though, because the man page says this:
```
 Mount point; specify the location to mount the cdrom. This mount
           point must be listed in /etc/fstab and properly configured.
```
but it doesn't hurt to give it a go, if it will save you an install. I'd give the man page a once-over, as I've never used it before
```
man apt-cdrom
```

anyway, if you succeed in adding it as a repository, then you should be able to install it as per usual

---

### Post by dcstar on 2012-10-09
> **Katniss Everdeen said:**
> I tried to install the deb file, not sure why it won't work. I can try again and post the outcome of it.

The Network Manager packages also has dependencies which will fail to install because you don't have a working network connection - it's a bit of a "Catch 22" situation.

I did this myself a month ago and had to boot my alternative 10.04 OS, then download the Network Manager package and the missing dependencies to my 12.04 partition and then manually install them (in the correct order) to fix things.

I have been using Ubuntu since 4.10 and found fixing my stupid Network Manager removal a challenge even with all the tricks I have accumulated over the years, I have a lot of sympathy for anyone else trying to do the same thing.

PS: I think that installing the **network-config** package could be the solution. This simple network configuration tool will allow you to get your networking back up so you can then get Internet access and properly reinstall the Network Manager package.

---

