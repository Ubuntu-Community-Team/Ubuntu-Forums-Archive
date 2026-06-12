---
title: "How can I install package w/wget and dpkg in chroot?"
date: 2010-01-03
forum: General Help
---

### Post by kansasnoob on 2010-01-03
I've been playing with the concept of using a mount and chroot to repair broken *buntu's for a few months now with excellent success on machines right in front of me (sadly about 50% success rate trying to instruct others).

Anyway sometimes people have apt/synaptic/package management pretty well hosed. While I can usually fix things editing sources.list w/nano and finally get the package list updated, once in a while it would be great to be able to install a .deb using nothing but the Terminal in a chroot.

So, just as an experiment in Karmic:

```
lance@lance-desktop:~$ wget http://security.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_1.97~beta4-1ubuntu4.1_i386.deb
--2010-01-03 15:35:55--  http://security.ubuntu.com/ubuntu/pool/main/g/grub2/grub-pc_1.97~beta4-1ubuntu4.1_i386.deb
Resolving security.ubuntu.com... 91.189.88.37
Connecting to security.ubuntu.com|91.189.88.37|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 433532 (423K) [application/x-debian-package]
Saving to: `grub-pc_1.97~beta4-1ubuntu4.1_i386.deb'

100%[======================================>] 433,532      328K/s   in 1.3s    

2010-01-03 15:35:57 (328 KB/s) - `grub-pc_1.97~beta4-1ubuntu4.1_i386.deb' saved [433532/433532]

```

Cool, wget worked! And after a bit of looking:

```
lance@lance-desktop:~$ ls /home/lance
bank statement                          Oh no I can't boot!.abw
Desktop                                 Pictures
Documents                               Projects
Downloads                               Public
error firefox.abw                       Templates
examples.desktop                        Videos
**[COLOR="Red"]grub-pc_1.97~beta4-1ubuntu4.1_i386.deb[/COLOR]**  Xorg crack pushers updates
Music                                   Xorg crack pushers updates~

```

So there it is in /home/lance but after a few hours of googling I decided to ask for some help.

How in the world would I use dpkg from the Terminal to install that package? Remember this is in a chroot so I can not access things via gui.

I'm sure there's a simple answer but I'm stumped :confused:

Thanks in advance.

---

### Post by sisco311 on 2010-01-03
```
sudo dpkg -i packagename.deb
```
or 
```
sudo gdebi packagename.deb
```

---

### Post by sisco311 on 2010-01-03
> **kansasnoob said:**
> 
Remember this is in a chroot so I can not access things via gui.


Why not? Just run:
```
xhost +
```on the host system.

then```
gdebi-gtk packagename.deb
```

---

### Post by kansasnoob on 2010-01-03
> **sisco311 said:**
> ```
sudo dpkg -i packagename.deb
```
or 
```
sudo gdebi packagename.deb
```

I figured that I would somehow have to include a location so dpkg would know where to find the package? I see it seems to have worked though.

---

### Post by kansasnoob on 2010-01-03
> **sisco311 said:**
> Why not? Just run:
```
xhost +
```on the host system.

then```
gdebi-gtk packagename.deb
```

I'd never even heard of xhost. I'll certainly give it a ride!

Many, many thanks. I love learning this stuff :guitar:

---

### Post by sisco311 on 2010-01-03
> **kansasnoob said:**
> I figured that I would somehow have to include a location so dpkg would know where to find the package? I see it seems to have worked though.

dpkg is looking for the package in the current working directory (pwd), but you can specify a relative or absolute path to the package.
```
dpkg -i /home/user/packagename.deb
```
```
dpkg -i ./downloads/packagename.deb
```

---

### Post by sisco311 on 2010-01-03
> **kansasnoob said:**
> I'd never even heard of xhost. I'll certainly give it a ride!

Many, many thanks. I love learning this stuff :guitar:

As root, you already should be able to run GUI apps.

I prefer to log in as a regular user:
```
sudo -u username -i
```

that's why I have to allow my user to connect to the X server.

xhost + grants access to everyone, 
a safer approach would be something like:
```
xhost + SI:localuser:**username**
```

---

### Post by kansasnoob on 2010-01-03
I gave dpkg several spins with various packages and just as you said, example:

```
sudo dpkg -i '/home/lance/grub-pc_1.97~beta4-1ubuntu4.1_i386.deb'
```

Funny thing, I think you may have taught me this once before when gdebi was borked during Karmic development :P

Maybe it'll stick with me this time :)

I tend to be far too reliant on using the gui option whenever possible, which I guess is OK, but it's also nice to keep learning.

Now I'll have to do some serious studying about xhost, many thanks again.

---

