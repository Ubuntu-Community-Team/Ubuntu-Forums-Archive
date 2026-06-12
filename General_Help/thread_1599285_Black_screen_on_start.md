---
title: "Black screen on start"
date: 2010-10-17
forum: General Help
---

### Post by kingbirdy on 2010-10-17
This is slighty different than the oter black screen threads I've seen, so could yu help me out? what it is, is I installed Maverick fresh (not an upgrade) and it now will go to were it says ubuntu, and has the loading dots, and it stays at a black screen after that. The 'thinking' light for my computer is not activationg. it is installed on a 20-30 Gb partition, on a dual boot with windows 7. I had had Lucid installed a while ago, but it was lost when my harddrive was wiped a while back. My specs:

Computer: Lenovo g555
CPU Type: AMD Athlon II Dual-Core
CPU Speed: M320(2.1GHz)
CPU L2 Cache: 1MB
HDD: 160GB
HDD RPM: 5400rpm
Memory: 3GB
Memory Speed: DDR2 800
Memory Type: 200-Pin DDR2 SO-DIMM

any help is appreciated.

---

### Post by Hippytaff on 2010-10-17
I assume you burned Maverick to CD...can you boot succesfully from the cd?

---

### Post by kingbirdy on 2010-10-17
> **Hippytaff said:**
> I assume you burned Maverick to CD...can you boot succesfully from the cd?
the CD works fine. The graphics are a little messy, but that's just a driver issue I had with Lucid too. I installed and messed around with the play from disc successfully with it.

---

### Post by Hippytaff on 2010-10-17
when you try to boot do you get a screen with options..if so boot into recovery mode...then we can take a look at things from command line and try to work out why it hangs.

---

### Post by kingbirdy on 2010-10-17
you mean the boot loader? yeah, I've got that. thats how I'm posting, from windows. So can you tell me what to do once I go ino recovery mode?

---

### Post by Hippytaff on 2010-10-17
Right, if you can get that far there are a number of things we can do and one of them is to look at log files.

post the results of this

```

cat /var/log/boot.log

```

---

### Post by kingbirdy on 2010-10-17
here you go:
```

Begin: loading essential Drivers ... done
Begin: Running scripts/init-premount ... done
Begin: mounting root file system ... Begin: Running /scripts/local-top ... done
Begin: running /scripts/local-premount ... done
Begin: running /scripts/local-bottom ... done
done
Begin: running /scripts/init-bottom ... done
fsck from until-Linux-ng 2.17.2
dev/sd6: clean, 135494/1201872 files, 726638/4798720 blocks
*starting AppArmor profiles
skipping profile in /etc/apparmor.d/disable:usr.bin.firefox

*setting sensors limit
skip stopping firewall: ufw(not enabled)
```

---

### Post by sandyd on 2010-10-17
> **kingbirdy said:**
> This is slighty different than the oter black screen threads I've seen, so could yu help me out? what it is, is I installed Maverick fresh (not an upgrade) and it now will go to were it says ubuntu, and has the loading dots, and it stays at a black screen after that. The 'thinking' light for my computer is not activationg. it is installed on a 20-30 Gb partition, on a dual boot with windows 7. I had had Lucid installed a while ago, but it was lost when my harddrive was wiped a while back. My specs:

Computer: Lenovo g555
CPU Type: AMD Athlon II Dual-Core
CPU Speed: M320(2.1GHz)
CPU L2 Cache: 1MB
HDD: 160GB
HDD RPM: 5400rpm
Memory: 3GB
Memory Speed: DDR2 800
Memory Type: 200-Pin DDR2 SO-DIMM

any help is appreciated.
Looks like X seems to have stalled.

post output of```

cat /var/log/Xorg.0.log
```
and see if you can get to some form of GUI. In recovery mode, run
```

startx
```

If it freezes and gives you a black screen, press ALT+PRINTSCREEN (hold down these two keys), and in succession (no need to hold, just press down) R+E+I+S+U+B

---

### Post by kingbirdy on 2010-10-17
startx did nothing, I just sayed at the command line. let me do the cat and get back to you.

---

### Post by sandyd on 2010-10-17
> **kingbirdy said:**
> **startx did nothing**, I just sayed at the command line. let me do the cat and get back to you.
thats not good.

try reinstalling xorg
```

sudo apt-get --reinstall install xorg-server
```

---

### Post by kingbirdy on 2010-10-17
well, the cat said nothing, and the install said it  couldnt find xorg-server. perhaps it coulnt connect to the internet? (I've not had a GUI, and therefor not set it up)

---

### Post by kingbirdy on 2010-10-17
any way for me to connect to the 'net through the command line?

---

### Post by sandyd on 2010-10-17
> **kingbirdy said:**
> well, the cat said nothing, and the install said it  couldnt find xorg-server. perhaps it coulnt connect to the internet? (I've not had a GUI, and therefor not set it up)
I think my brain has somehow fried somewhere between compiling the gentoo kernel and rebuilding a mac.

anyways...
```

sudo apt-get install xorg
```

---

### Post by kingbirdy on 2010-10-17
it said it coulnt find the package

---

### Post by sandyd on 2010-10-17
> **kingbirdy said:**
> it said it coulnt find the package
```

sudo apt-get update
```
if your plugged into ethernet, there should be no problems with internet

---

### Post by kingbirdy on 2010-10-17
I use wi-fi

---

### Post by Hippytaff on 2010-10-18
> **kingbirdy said:**
> I use wi-fi
 
Are you able to connect via ethernet? if so do that then update upgrade
 
```

sudo apt-get update && sudo apt-get ugrade

```

---

### Post by kingbirdy on 2010-10-18
I'll see if I've got a cable laying around somewhere. steal if from the router if I have to. But I have to ask, what does the ```
sudao
``` do?

---

### Post by Hippytaff on 2010-10-18
> **kingbirdy said:**
> I'll see if I've got a cable laying around somewhere. steal if from the router if I have to. But I have to ask, what does the ```
sudao
``` do?

sudo gives you temporary root priveledges, like being administrator for a bit

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

sudoa does nothing, I did a typo :-)

---

### Post by kingbirdy on 2010-10-18
okay, thanks. I know sudo, but thought that was something I just didnt know.

---

### Post by Hippytaff on 2010-10-18
> **kingbirdy said:**
> okay, thanks. I know sudo, but thought that was something I just didnt know.

no it was me being a duffer :-)

---

