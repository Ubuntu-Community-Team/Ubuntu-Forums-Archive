---
title: "Crashes/Freezes Frequently, Need to Reboot"
date: 2012-09-07
forum: General Help
---

### Post by rockstarrem on 2012-09-07
Hey guys,

I am not sure what information I can give you, but tell you exactly what is happening when my computer crashes/freezes:

[LIST]
[*]A lot of the time I can just be running Chromium and the computer will crash.
[*]Other times it can be VLC Media Player.
[*]I am using the LXDE desktop when most crashes occur, but I did experience a crash about 30 minutes ago with the i3 desktop.
[*]My reset button on my computer doesn't even work during these crashes. I need to hold down the power button.
[/LIST]

Please tell me what information you need and I will be happy to provide it. Thank you for your time.

---

### Post by Epodx64 on 2012-09-07
What kind of video card are you using?

---

### Post by rockstarrem on 2012-09-07
> **Epodx64 said:**
> What kind of video card are you using?

2x 1GB nVidia GeForce GTX 560 Ti DS Superclocked (in SLI)

BTW: The drivers I'm using are the post-release one, not the "recommended" one.

---

### Post by Epodx64 on 2012-09-07
Try installing the 304.x driver from x-swat when I was using a Nvidia card in my last setup the 29x.x drivers seemed to be regressed for some reason the 304.x drivers work great though ill get you the link to the ppa 

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/)

I'd bet this fixes it. the 17x-29x Drivers where problematic to say the least.

---

### Post by rockstarrem on 2012-09-07
Thanks, I will try that and let you know.

---

### Post by rockstarrem on 2012-09-07
Do you know the name of the package I should install once I have the PPA added?

---

### Post by Epodx64 on 2012-09-07
Just run 

sudo apt-get update
sudo apt-get upgrade

and it will grab the newest drivers.

---

### Post by Epodx64 on 2012-09-07
After you added the PPA of course.

---

### Post by rockstarrem on 2012-09-07
Are you sure? It installed xserver-xorg-video-intel that's only 266 kb. Maybe it's trying to install drivers for my internal?

---

### Post by Epodx64 on 2012-09-07
Yeah it'll install the intel drivers too. but if that didn't work boot up jockey and see if its listed if its not then try sudo apt-get install nvidia-current

---

### Post by rockstarrem on 2012-09-07
nvidia-current worked. I'll let you know if I experience any more instability. Thank you for your help so far.

---

### Post by Epodx64 on 2012-09-07
Yeah no problem.

---

### Post by rockstarrem on 2012-09-08
It did not work. My computer crashed again. I have a feeling that it is Deluge causing the problem, so I'll try a different torrent client for now and see if it helps.

---

### Post by idoitprone on 2012-09-08
> **rockstarrem said:**
> It did not work. My computer crashed again. I have a feeling that it is Deluge causing the problem, so I'll try a different torrent client for now and see if it helps.

```
 free -m
```

Do you have swap?

---

### Post by rockstarrem on 2012-09-08
No, but I have 16GB of RAM.
```

             total       used       free     shared    buffers     cached
Mem:         15940      15738        201          0       5636       9016
-/+ buffers/cache:       1086      14853
Swap:            0          0          0
        0          0          0

```

Do I need to add a swap?

What could be taking up all that memory...

---

### Post by Epodx64 on 2012-09-08
> **rockstarrem said:**
> No, but I have 16GB of RAM.
```

             total       used       free     shared    buffers     cached
Mem:         15940      15738        201          0       5636       9016
-/+ buffers/cache:       1086      14853
Swap:            0          0          0
        0          0          0

```Do I need to add a swap?

What could be taking up all that memory...

Damn there's a memory leak somewhere try running top for awhile and see whats causing it. I'd still add like 2Gb of swap even with 16gb of ram though.

---

### Post by rockstarrem on 2012-09-08
I had the task manager of LXDE open for a while to see if it was memory, and the system crashed even when less than 1 GB of RAM was being used. I'm not sure if it's memory or not.

---

### Post by idoitprone on 2012-09-08
> **Epodx64 said:**
> Damn there's a memory leak somewhere try running top for awhile and see whats causing it. I'd still add like 2Gb of swap even with 16gb of ram though.


No, no, no. There is no memory leak

op add a swap file, make it 1GB at least

Linux is a bad copy of unix. That is the problem it is just a bad copy. Unix back then require swap, since linux is also a copy, it also needs swap.

In fact, all major operating system have swap, if they dont they will freeze

It stupid, you have 16 gig and you dont really need any more memory, but os will always try to use swap

[https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F](https://help.ubuntu.com/community/SwapFaq#How_do_I_add_more_swap.3F)

if you change your swappingness 0 then you can migrate the effects of no swap, but it is not the solution

---

### Post by rockstarrem on 2012-09-08
Alright, I made a 10.3 GB swap file since I had some crazy unallocated space, let's see what happens!

---

### Post by rockstarrem on 2012-09-08
Nope, even with the swap file it crashed...

---

### Post by idoitprone on 2012-09-08
> **rockstarrem said:**
> Alright, I made a 10.3 GB swap file since I had some crazy unallocated space, let's see what happens!


You will only need that much swap if you are hibernating

Swap space have to be activated 

```
sudo fallocate -l 1024 /mnt/1024MiB.swap

sudo mkswap /mnt/1024MiB.swap
sudo swapon /mnt/1024MiB.swap
```make sure you have something like this in /etc/fstab
/mnt/1024MiB.swap  none  swap  sw  0 0
```
gksudo gedit /etc/fstab
```

here is the link to change swappiness
[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

---

