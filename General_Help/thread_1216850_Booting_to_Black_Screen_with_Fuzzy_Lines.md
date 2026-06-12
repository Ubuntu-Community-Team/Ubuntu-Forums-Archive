---
title: "Booting to Black Screen with Fuzzy Lines"
date: 2009-07-18
forum: General Help
---

### Post by jdorenbush on 2009-07-18
Running Ubuntu 9.04 64. Tried to install ATi driver today. After what seemed to be a successful install I rebooted only to end up stuck at a black screen with some fuzzy colored lines at the top portion of my screen.

It goes through a normal boot process, I see the Ubuntu splash loading screen, and right about the time I should be seeing my login window -- instead I get the black screen with fuzzy lines.

**Update:** More descriptive...
- Small red lines at the top 1/4 inch of my screen.
- About an inch thick green and purple lines 3/4 the way to the top of my screen.
- The screen blinks three or four times than just sits there, with the weird colored lines.

Any idea how to fix or just uninstall the driver? I've uninstalled/reinstalled *xserver-xorg-video-ati* and uninstalled *xorg-driver-fglrx* -- neither seemed to the fix the problem.

---

### Post by roccivic on 2009-07-18
Boot into "recovery mode", select "drop to a shell", uninstall the driver in question

---

### Post by jdorenbush on 2009-07-18
> **roccivic said:**
> Boot into "recovery mode", select "drop to a shell", uninstall the driver in question

Thanks for the quick response. I'm at the shell. Any chance you can help with command to uninstall driver? I ran this:
```
sudo apt-get remove xorg-driver-fglrx
```

That apparently didn't work though. I am still having the problem.

This is the [driver]("http://linux.softpedia.com/progDownload/ATI-Radeon-Linux-Display-Drivers-Download-6719.html").

---

### Post by cwbar_1 on 2009-07-18
I believe the correct command would be "sudo dpkg-reconfigure xserver-xorg"  (without the quotes)

---

### Post by philcamlin on 2009-07-18
> **roccivic said:**
> Boot into "recovery mode", select "drop to a shell", uninstall the driver in question

id suggest that too

---

### Post by jdorenbush on 2009-07-18
> **philcamlin said:**
> id suggest that too

I did uninstall it. At least I think I did. sudo apt-get remove xorg-driver-fglrx

> **cwbar_1 said:**
> I believe the correct command would be "sudo dpkg-reconfigure xserver-xorg"  (without the quotes)

I ran through that process too. No luck.

---

### Post by cwbar_1 on 2009-07-18
Check out [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by jdorenbush on 2009-07-18
> **cwbar_1 said:**
> Check out [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Thanks. I got it fixed. From that link I found [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

Just did all of the following:
```

  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  dpkg-reconfigure xserver-xorg

```

---

