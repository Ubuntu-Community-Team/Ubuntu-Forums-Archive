---
title: "Downgrade from Ubuntu 10.04 64 bit to 32 bit"
date: 2010-07-24
forum: General Help
---

### Post by Richiegs on 2010-07-24
I have used the 64 bit version of Ubuntu 10.04 for a while and am satisfied with it.  The problem is when I watch video (Bloomberg) and listen to radio at the same time, it uses up a lot of memory (My PC has 3 GB of Ram). It degrades the performance of the PC. I also read that the only reason to use a 64 bit version is when a PC has 4 GB of Ram. Therefore, I wonder if it is possible to downgrade my current 64 bit version of Ubuntu 10.04 to a 32 bit version. Thank you for anyone who helps.

---

### Post by sanderj on 2010-07-24
You can't downgrade from 64bit to 32bit, other than reinstalling.

Apart from that: are you sure it's a 64-bit problem? If you don't know, run a Ubuntu live-cd (both 32-bit and 64-bit) and see on which systems the slowness occurs.

---

### Post by QIII on 2010-07-24
Is the Bloomberg video presented in Flash?

Are you using the 64 bit version of Flash?

---

### Post by Richiegs on 2010-07-24
> **sanderj said:**
> You can't downgrade from 64bit to 32bit, other than reinstalling.

Apart from that: are you sure it's a 64-bit problem? If you don't know, run a Ubuntu live-cd (both 32-bit and 64-bit) and see on which systems the slowness occurs.

I read a few posts on the Internet which also described the large usage of ram in 64 bit Ubuntu. I have experienced this memory problem too. Moreover, since my PC has only 3 GB, not 4 GB, I guess there is no need to use a 64 bit Ubuntu.

---

### Post by PaulReaver on 2010-07-24
its not just for the extra ram.  (as you can use 4Gb ram on 32bit if you use a PAE kernel)
there are other performance improvments with ubuntu64.


Its near impossible to "convert" a 32 ubuntu to 64.
but you could install a 32bit web browser and 32bit flash plugin on ubuntu64.

sorry for the bad news... but if you want 32bit buntu you'll need to wipe your install and start again.

---

### Post by Richiegs on 2010-07-24
> **QIII said:**
> Is the Bloomberg video presented in Flash?

Are you using the 64 bit version of Flash?

It is not just Bloomberg video. It could be CNBC too and other video stuff.

---

### Post by Richiegs on 2010-07-24
Since it is not possible to convert to 32 bit from 64 bit Ubuntu 10.04, how can I make it an independent partition from Windows to take full advantage of 64 bit?
I tried LVPM, but it did not support Ubuntu 10.04 yet.

---

### Post by oldos2er on 2010-07-24
> **Richiegs said:**
>  I also read that the only reason to use a 64 bit version is when a PC has 4 GB of Ram. 

This is an urban myth one often sees in the forums here. 64-bit Ubuntu works just fine with 2GB RAM. If you've (i.e. anyone) got a 64-bit processor, why not make full use of it?

---

### Post by Zorgoth on 2010-07-24
If you want to switch 64 to 32-bit, it isn't that hard.  Back up your home folder, go to Synaptic and run "File > Save Marking As...," and save the markings, BEING ABSOLUTELY SURE TO CHECK THE BOX SAYING "SAVE FULL STATE, NOT ONLY CHANGES;" IF YOU DO NOT DO THIS YOU WILL HAVE TO FIND AND DOWNLOAD ALL OF YOUR PACKAGES AGAIN BEFORE YOU HAVE YOUR OLD SETUP BACK.

Then run a clean 32-bit install (of the same version of Ubuntu), starting up with a temporary user, load the Synaptic markings (which you have to back up somewhere you didn't overwrite with the new installation obviously; email would do) and apply them, along with all upgrades, then create a new account with the account name you always used, and put a copy of your old home folder in /home/<account_name>, boot up into the account, and it should have all your settings and data ready.  I have upgraded from 32 to 64-bit this way and it didn't cause trouble.  The other way will probably work fine too.

HOWEVER, I would probably not recommend doing this.  64-bit performance is generally better than 32-bit.  Are you sure you actually have a 64-bit problem?

---

### Post by linux18 on 2010-07-24
64 bit does not significantly increase ram usage, I've run a 64 bit xubuntu on 384 MB of ram  and in virtualbox, on 48 MB of ram ( I always test the veracity of these myths that keep coming out about computers ) you probably have a problem elsewhere, run this command when your ram usage spikes :```
 top -bs > ~/ram.log & sleep 3 && killall top & echo DONE 
```this will check your ram usage and output that to a file called " ram.log " in your home directory, post the output and we can see if you have a rogue program somewhere.

---

### Post by philinux on 2010-07-24
> **linux18 said:**
> 64 bit does not significantly increase ram usage, I've run a 64 bit xubuntu on 384 MB of ram  and in virtualbox, on 48 MB of ram .

On 32 bit I see about 300mb in use on 64 bit it's about 650mb.

I use 64 bit mainly. 32 bit is gf's lappy.
[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

---

### Post by Richiegs on 2010-07-27
[QUOTE run this command when your ram usage spikes :```
 top -bs > ~/ram.log & sleep 3 && killall top & echo DONE 
```this will check your ram usage and output that to a file called " ram.log " in your home directory, post the output and we can see if you have a rogue program somewhere.[/QUOTE]

THIS IS WHAT I GOT:

top - 18:30:33 up  3:48,  2 users,  load average: 1.21, 1.23, 1.24
Tasks: 189 total,   2 running, 185 sleeping,   0 stopped,   2 zombie
Cpu(s): 17.5%us,  4.7%sy,  0.0%ni, 77.2%id,  0.4%wa,  0.1%hi,  0.1%si,  0.0%st
Mem:   3090580k total,  3066076k used,    24504k free,   170236k buffers
Swap:   261112k total,     5288k used,   255824k free,   425632k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2377 windowsx  20   0 70776  26m  10m R   52  0.9  20:18.28 npviewer.bin       
 1151 root      20   0  221m  96m 9468 S   27  3.2  13:11.68 Xorg               
 1816 windowsx  20   0  757m 165m  40m S   25  5.5   7:08.63 firefox-bin        
 4258 windowsx  20   0  238m  20m  15m S   14  0.7   0:26.72 gnome-system-mo    
 4083 windowsx  20   0 69364  20m  11m S    4  0.7   1:12.07 operapluginwrap    
 1945 windowsx  20   0  759m 522m  26m S    2 17.3  15:29.99 opera              
 2395 windowsx  20   0  566m  33m  17m S    2  1.1  12:01.13 totem-plugin-vi    
 3626 windowsx  20   0 18192 6100 4892 S    2  0.2   0:14.19 npviewer.bin       
 3701 windowsx  20   0 18208 6172 4900 S    2  0.2   0:13.74 npviewer.bin       
    1 root      20   0 23708 1748 1272 S    0  0.1   0:01.25 init

---

### Post by Zorgoth on 2010-07-27
Opera is using a massive amount of memory...

---

### Post by Richiegs on 2010-07-27
With Opera closed. This is what I got:
top - 20:28:47 up  5:46,  2 users,  load average: 1.76, 1.76, 1.52
Tasks: 180 total,   3 running, 177 sleeping,   0 stopped,   0 zombie
Cpu(s): 18.5%us,  4.2%sy,  0.0%ni, 76.9%id,  0.3%wa,  0.1%hi,  0.0%si,  0.0%st
Mem:   3090580k total,  2899036k used,   191544k free,   206844k buffers
Swap:   261112k total,     7288k used,   253824k free,   432200k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1151 root      20   0  239m 124m 8328 R   24  4.1  37:12.82 Xorg               
 4258 windowsx  20   0  238m  20m  15m R   10  0.7  10:46.01 gnome-system-mo    
 5069 windowsx  20   0 19216 1300  920 R    2  0.0   0:00.02 top
2371 windowsx  20   0 2236m 1.4g  13m S    0 48.7   8:43.64 chrome 

Why did Chrome use so much memory?

---

### Post by linux18 on 2010-07-27
emulators, web browsers, and office programs generally use a lot of ram and cpu , aside from that everything else in the output of ram.log looks normal. many people have to remember that ram is used differently in linux compared to windows so just because your using 400MB on startup and XP uses 140MB doesn't mean you will run out of ram faster than xp when you stress the system. up to 80% of your ram usage can be cached and buffered ram which can be removed as needed. On the other hand, XP always uses the swap file even if there is sufficient free ram which makes it slower when multitasking and less efficient in taking advantage of the ram.  
Off Topic, can anyone suggest an improvement in my command that will keep the columns straight?

---

