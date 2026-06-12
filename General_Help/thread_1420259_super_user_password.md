---
title: "super user password"
date: 2010-03-02
forum: General Help
---

### Post by wrgarrett on 2010-03-02
I was using 8.04. WHen I installed 8.04, I was prompted with a driver that I installed. It worked perfectly. I decided to remove 8.04 and install 9.10. I cannot get the video to work correctly. 

I am wanting to get my ATI Radeon 9600 video card to work correctly so I went to the ATI site and downloaded the drivers and install instructions. I followed the instructions and after they seemed to process, I was prompted that I must be super user to complete this task. 

At the terminal, I entered su and was prompted for a password. I entered the password that I login with but it is not accepted. How do I find out what password it wants? I only entered one password when I installed 9.10.

---

### Post by asmoore82 on 2010-03-02
Put `sudo` in front of any commands that need root privilege,
This will accept your user password in the same way that Admin programs such as Synaptic do.

For example, if they say "run `ls -l /etc` *as root*," you would run
```
sudo ls -l /etc
```

---

### Post by 98cwitr on 2010-03-02
*sudo su*

will give you root access, then type exit to get back to your profile.

---

### Post by asmoore82 on 2010-03-02
> **98cwitr said:**
> *sudo su*

will give you root access, then type exit to get back to your profile.

if you must, ```
sudo -i
``` is preferable,
but neither are recommended if at all avoidable.

---

### Post by darolu on 2010-03-02
You can run
```
$ sudo ./atidriver.run
```

But, I'm affraid the Catalyst 9.3 driver does not work with Ubuntu 9.10; ATI no longer supports your card, they stopped creating new drivers for a lot of cards a year ago (Feb 09)... leaving a lot of us without a working driver.
The free/open source driver works fine though, I don't have any problems with it, compiz runs fine, the 3D games I've tested work fine (open arena, yo frankie!) and even Blender.
Here is the complete list of "legacy" ATI cards:
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English)

---

### Post by wrgarrett on 2010-03-03
> **darolu said:**
> You can run
```
$ sudo ./atidriver.run
```

But, I'm affraid the Catalyst 9.3 driver does not work with Ubuntu 9.10; ATI no longer supports your card, they stopped creating new drivers for a lot of cards a year ago (Feb 09)... leaving a lot of us without a working driver.
The free/open source driver works fine though, I don't have any problems with it, compiz runs fine, the 3D games I've tested work fine (open arena, yo frankie!) and even Blender.
Here is the complete list of "legacy" ATI cards:
[http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.24&lang=English)

Thanks for the info. Where do I find the open source driver?

---

### Post by mcduck on 2010-03-03
> **wrgarrett said:**
> Thanks for the info. Where do I find the open source driver?

you already have it (and are using it) by default.

What kind of problems are you having with your video?

---

### Post by wrgarrett on 2010-03-03
My resolution is 800X600 max. I cannot set any of the advanced display options. It says not available. I have a 23" display and I have to use scroll bars to read any open windows. Appearance is as Windows in Safe Mode. I have Kubuntu 8.04 on a separate partition and it is using the old ATI drivers, I guess, as it is displays 1600X1200 really great.

---

### Post by mcduck on 2010-03-03
Most likely the problem is just in the way how your graphics driver detects (or rather *doesn't detect*) your monitor. You could simply create the /etc/xorg.conf file and define the correct resolution there.

(Radeon 9600 series actually work just fine with the opensource driver, I had one machine with 9600XT until I sold it recently. Not that there really is any other option than using the OS driver, anyway...)

---

### Post by wrgarrett on 2010-03-03
I stated above it was a Radeon card but I looked at it and it says All-In-Wonder. Based on that, here is where I downloaded the drivers: [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
I thought they were the same, maybe not?

---

### Post by wrgarrett on 2010-03-03
> **mcduck said:**
> Most likely the problem is just in the way how your graphics driver detects (or rather *doesn't detect*) your monitor. You could simply create the /etc/xorg.conf file and define the correct resolution there.

(Radeon 9600 series actually work just fine with the opensource driver, I had one machine with 9600XT until I sold it recently. Not that there really is any other option than using the OS driver, anyway...)

I have no idea how to create the /etc/xorg.conf file. Could you point me in the right direction?

---

### Post by mcduck on 2010-03-03
One simple way would be this:

1. Move to TTY (by pressing Ctrl-Alt-F1) and kill the graphical desktop:
```
sudo service gdm stop
```

2. Generate default configuration file automatically:
```
sudo Xorg -configure
```

3. The above command created a file called xorg.conf.new in your current location, so you'll need to move it to correct place and rename it:
```
sudo mv ~/xorg.conf.new /etc/X11/xorg.conf
```

4. Next edit the file to add correct resolution: 
```
sudo nano /etc/X11/xorg.conf
```

5. When done, restart X again:
```
sudo service gdm start

```

These links should be useful for finding out more about the actual configuration options in xorg.conf:
[http://www.ghacks.net/2009/02/04/get-to-know-linux-understanding-xorgconf/]("http://www.ghacks.net/2009/02/04/get-to-know-linux-understanding-xorgconf/")
[http://wiki.archlinux.org/index.php/Xorg]("http://wiki.archlinux.org/index.php/Xorg")

---

### Post by wrgarrett on 2010-03-03
Thanks   for all your efforts but something went wrong. After #5. was completed, my monitor displayed "No Signal" then went black. I went ahead and deleted my Ubuntu 9.10 partition and if I decide to work with Ubuntu I think I will re-install 8.04.

9.10 is just a pain. Had major pain with Kubuntu 9.10, it would not install at all after repeated attempts so I reverted it to 8.04.

---

