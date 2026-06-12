---
title: "Wired problem  with ATI driver!!"
date: 2009-07-21
forum: General Help
---

### Post by chipsy on 2009-07-21
okey I first downloaded the driver from this site

 [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.36&lang=English)


then I found out I should  enable POSIX shared memory 
I'm not sure I've done that part correct :confused:
[ATTACH]121887[/ATTACH]
and they also said I should run a command in the terminal
[ATTACH]121896[/ATTACH]


ATI RADEON HD 4870
RAM 4GB

PS. sorry for my bad English.

---

### Post by devildoc5 on 2009-07-21
ok I have never tried this but from looking at this thread here: [http://ubuntuforums.org/showthread.php?t=122712](http://ubuntuforums.org/showthread.php?t=122712)

What you need to do isopen a terminal and type in:
```

sudo gedit /etc/fstab

```

inside of this you need to add
```

tmpfs /dev/shm tmpfs defaults 0 0

```

Save and exit.

Back in the terminal you need to type in:
```

sudo mount /dev/shm
sudo mount | grep "shm"

```
 In response the terminal should print out something that looks like this:
```

tmpfs on /dev/shm type tmpfs (rw)

```

That will enable POSIX

Now to start the installer you need to open a terminal (or use the same one if it is still open) and type in:

```

sh ./ati-driver-installer-9-5-x86.x64_64.run

```

then follow the on screen prompts and you should be golden from there.....

---

### Post by chipsy on 2009-07-21
thank you very much I really like this forum :D

---

### Post by devildoc5 on 2009-07-21
> **chipsy said:**
> thank you very much I really like this forum :D

Just post on here if you have any problems with this after following the above steps, someone will help you.

And once you make sure that you have got it working do everyone a favor and go to thread tools at the top and click "solved"

---

