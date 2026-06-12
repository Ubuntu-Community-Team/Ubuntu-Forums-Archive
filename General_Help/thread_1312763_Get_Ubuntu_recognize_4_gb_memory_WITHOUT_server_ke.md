---
title: "Get Ubuntu recognize 4 gb memory WITHOUT server kernel"
date: 2009-11-03
forum: General Help
---

### Post by josephmc on 2009-11-03
Every time I searched Google for a solution to read 4 gb of memory it said to either install the server kernel or the 64 bit kernel. Sounded like a windows type solution to me...

Not sure if the pae build is new for karmic but this is how I got my install to run with 4gb without the server or 64 bit kernel

```
sudo apt-get install linux-generic-pae linux-headers-2.6.31-14-generic 
```

DKM installed my nvidia drive and I was good to go! I couldn't find where this was documented anywhere but I'm hoping we can get a wiki entry or something because people don't need the server kernel on a desktop or the 64 bit version if they are 32 bit.

---

### Post by pi4r0n on 2009-11-03
> **josephmc said:**
> 
```
sudo apt-get install linux-generic-pae linux-headers-2.6.31-14-generic 
```


Unfortunately this does not work for me :(

> Linux version 2.6.31-14-generic (buildd@rothera) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009

and system still only see 3GB

Cheers

pi4r0n

---

### Post by josephmc on 2009-11-03
Is that the kernel your running ATM? you need to boot into the pae kernel in order for it to work.

---

### Post by SeanBlader on 2009-11-03
Please excuse my inexperience, but why wouldn't you just run the 64bit kernal?

---

### Post by pi4r0n on 2009-11-03
> **SeanBlader said:**
> Please excuse my inexperience, but why wouldn't you just run the 64bit kernal?

Unfortunately  for some reason my ATI Radeon card does not work under 64bit OS and all fixes I managed to find on internet did not work :(

**josephmc** I don't have a clue what kind of kernal I got. How do I find out whether is it ATM or other. 

Cheers

pi4r0n

---

### Post by wildweathel on 2009-11-03
ATM = At The Moment

```
uname -a
```

Tells you all you want to know about the currently-running kernel version.

---

### Post by pi4r0n on 2009-11-13
Hello ALL

I have finally managed to get 4GB of RAM on my Ubuntu 9.10 (Karmic) system.

In order to do this just run follow these steps:

Step 1 - Open a terminal and paste this

> sudo apt-get install linux-generic-pae

Step 2 - Reboot system and then select new kernel with ending PAE

Cheers

pi4r0n

---

### Post by sgage on 2009-11-13
I did a clean install of Karmic 32-bit, and the PAE kernel was installed automatically. I didn't even realize until I looked at the System Monitor one day.

Not that I ever get close to using all 4 of my GB of RAM, but it's kind of nice to see it all recognized.

---

### Post by josephmc on 2009-12-05
Yes you need to reboot and select the pae kernel. verify you are running the pae kernel with uname -r.

I just wanted to note that an upgrade I did broke the nvidia drivers (would prob break ATI also). It will bring you to a basic graphics mode. Drop to the command line, login, and run "sudo reboot". Your best off just booting into the normal kernel then install the headers. In this upgrade's case...

```
sudo aptitude install linux-headers-2.6.31-16-generic-pae
```

Hope that helps somebody save some headache

---

### Post by RomanIvanov on 2009-12-08
Thanks a lot for all, this works like a charm for Ubuntu 9.10, 32b linux, 4 Gb RAM:
```
sudo apt-get install linux-generic-pae linux-headers-2.6.31-16-generic-pae
```

---

