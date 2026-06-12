---
title: "Cannot Initialize NVIDIA Kernal Module every time I boot up."
date: 2012-01-12
forum: General Help
---

### Post by KillJarrod on 2012-01-12
Hi there!

I just downloaded and installed Ubuntu 10.04 recently and I have managed to install all my drivers correctly but for reason I do not know why my NVIDIA Driver is not working correctly

I have the GeForce GTX 460 SE and installed the NVIDIA-Linux-x86_64.290.10.run Driver 10 times now with success and my Monitor is able to produce the high resolutions that it can produce (It is a LG twenty something inch wide screen monitor" Once I reboot the computer and boot up Ubuntu again however the driver just fails and says that it cannot initialize the NVIDIA kernal module and always have to run in low-graphics mode.

I have been trying rigorously to solve the issue but after countless installs, I am losing hope. Can someone please help a poor soul like me?

---

### Post by BC59 on 2012-01-12
Try installing the latest NVIDIA drivers

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
```

---

### Post by Cavsfan on 2012-01-12
Or the other possibility is you can install the most recent driver and then create a script that will install that driver 
into any new kernel that gets installed.

[[COLOR=blue]_Get the latest nVidia driver here._[/COLOR]]("http://www.nvidia.com/Download/index.aspx?lang=en-us")

[[COLOR=blue]_Instructions on how to install nVida driver._[/COLOR]]("http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html") - instructions on installing the driver.

You will need to print steps 4 through 8 to be able to do after rebooting.
When you enter the step 8 command, viola your system will be ready to login to.

This is a tutorial someone in this forum wrote that still works beautifully.
[[COLOR=blue]_HOWTO: Automatically update manually installed NVidia drivers after kernel updates_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=835573")

Just be careful and do exactly as it says and you will be fine.

I have the LTS, a 28" monitor and the latest nVidea driver 290.10 installed for my Geforce 9800 GT and it works very well.

---

### Post by Randy Schilling on 2012-01-12
Say, I felt the kind of frustration you're feeling
2 or 3 years ago when I went through a month of repeated failure
at installing Ubuntu. This was my first encounter with Ubuntu.
The main symptom was failure to boot after installation. 
I got many suggestions from this forum, tried hundreds of ideas: contacted nVidia for help, tried their new drivers, beta this and that, tried different brands of discs for the iso file, tried different cd/dvd player.  It went on and on.

What finally worked was to install a new graphics card.
Don't know why it worked, wasn't having any discernible 
graphics problems.  I don't even recall why I thought it was
a graphic problem in the first place. Could not believe how easily Ubuntu installed with the new card. I still have 25 or so cds with working Ubuntu 10.04 iso files.  Maybe my card was getting old,  vintage 2006.

Anyway, it might be worth trying a new graphics card. Best Buy's liberal return policy is what got me through this crisis. They let you try things and return them without hassle. Just keep your receipts.

Good Luck - Randy

---

### Post by Cavsfan on 2012-01-13
**KillJarrod**, you need to let us know what you did and if it worked. Then you can mark this thread as solved.
At the top in red click on "Thread tools" and then at the bottom of the list click on "Mark this thread as solved".
 :)

---

