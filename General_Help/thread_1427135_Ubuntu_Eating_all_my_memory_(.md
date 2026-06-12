---
title: "Ubuntu Eating all my memory :("
date: 2010-03-11
forum: General Help
---

### Post by jose187 on 2010-03-11
--------------------UPDATE--------------------

Thanks everybody for your help.

I have tried various things, including reconfiguring x-org. There hasn't been much improvement.

However, i have also seen mentioned that a recent upgrade on the nVidia driver is causing similar problems....but i am not too sure if this is the case here.

Also, i have noticed the problem arises when i use Inkscape. Once opened, even if i close it back down, the usage remains around the 95%.

I have a laptop with an Intel graphics card, with the same setup as my desktop, and the memory remains relatively low...about 15% of 2Gb ram. Therefore, the 95% of 4Gb ram on my desktop just seems too much, bearing in mind compiz is set up the same in both....


---------------------------------

Hi,

I have been using Ubuntu for two years now, and all has been great. But for the last two weeks I have noticed that my computer, for some reason, ends up eating all my memory. I have 4GB RAM and 4GB swap, but when i look at the usage, it is constantly at 95% for programs opened.

I entered TOP in the terminal and this is what i got

 ```

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND 
 5222 jose      20   0  551m 117m  29m S    9  3.0   1:17.76 firefox-bin        
 4696 jose      20   0  622m  57m  15m S    1  1.5   0:44.13 rhythmbox          
 2217 root      20   0 5384m 2.9g 5332 S    1 76.2  13:50.99 Xorg               
 2542 jose      20   0  239m 4684 3092 S    1  0.1   0:52.99 multiload-apple    
 2393 jose      20   0  329m 3816 2736 S    1  0.1   8:31.28 pulseaudio         
 5363 jose      20   0  214m  16m  10m S    1  0.4   0:01.02 gnome-terminal     
 2496 jose      20   0  372m  10m 6760 S    0  0.3   6:17.84 compiz.real        
 5384 jose      20   0 19132 1376  980 R    0  0.0   0:00.39 top
```

Please help...

thanks

---

### Post by Olav on 2010-03-11
> **jose187 said:**
> Please help...
As long as there is no degradation of performance I think you should not worry.

---

### Post by ajgreeny on 2010-03-11
I would suggest that there is something not quite right with your xorg setup, perhaps your graphics card is not using the best driver or something similar.

xorg using 76% memory is certainly not as it should be; my old system with an ati 9200SE card and with compiz running uses only about 2-3% of my memory, and I have only half of your system memory in my box.

---

### Post by coldraven on 2010-03-11
Running Karmic 64bit, I let it choose the swap automatically on installation.
With Firefox,Rythmbox, PDF reader,Open office and Gimp running see the screenshot.
Maybe fresh install needed!

---

### Post by muteXe on 2010-03-11
Gotta love these people who suggest a fresh install for any problem that comes along...

---

### Post by Intrepid Ibex on 2010-03-11
> **muteXe said:**
> Gotta love these people who suggest a fresh install for any problem that comes along...
Heh, well.. Some people just don't know the answer and still want to say at least something. But who knows, maybe the next step people start suggesting is to just wipe your Home directory.

I myself only suggest people using ancient Ubuntus to update to newer ones when they wonder why newer apps they manually installed won't work as they should.

@jose187, As what comes to the problem itself, did you "tweak" your xorg.conf.. at least a little bit? Did you try:
```
dpkg-reconfigure -phigh xserver-xorg
```
? If even that won't work, you should probably do a reconfigure of X without the "-priority high" (-phigh) switch:
```
dpkg-reconfigure xserver-xorg
```
Which will give you more stuff to reset to.
Also, if you use nvidia, running something like: 
```
sudo nvidia-xconfig
```
will clear out all the wrong config options you might have in your xorg.conf.

---

### Post by coldraven on 2010-03-12
MuteXe, I have no way of knowing Jose's competence and for me 9.10 works a lot better than 9.04.
Also I have managed to break my installation by fiddling with various things, I have learnt  
a lot since going Ubuntu. However, as this laptop is my main connection to the outside world I have to try to keep it working.
I think that one of the best things about Ubuntu is the ease of installation coupled with the low price of an external HDD backing up and restoring your data is easy.
Admittedly if you have a slow internet connection getting the updates are a chore.

Anyway it was only a friendly suggestion, for all I knew no-one else may have replied and at least Jose would not feel ignored.
So chill out, we are all learning at our own speed.
Did I mention that Ubuntu rocks? :D

---

### Post by jose187 on 2010-03-18
Thanks everybody for your help.

I have tried various things, including reconfiguring x-org. There hasn't been much improvement.

However, i have also seen mentioned that a recent upgrade on the nVidia driver is causing similar problems....but i am not too sure if this is the case here.

Also, i have noticed the problem arises when i use Inkscape. Once opened, even if i close it back down, the usage remains around the 95%.

I have a laptop with an Intel graphics card, with the same setup as my desktop, and the memory remains relatively low...about 15% of 2Gb ram. Therefore, the 95% of 4Gb ram on my desktop just seems too much, bearing in mind compiz is set up the same in both....

---

### Post by prodigy_ on 2010-03-18
Do you you use any proprietary video driver (ATI or nVidia)? Do you use Compiz? Because you obviously have huge memory leaks in Xorg and those are often caused by a faulty driver or by a DWM.

---

### Post by jose187 on 2010-03-18
> **prodigy_ said:**
> Do you you use any proprietary video driver (ATI or nVidia)? Do you use Compiz? Because you obviously have huge memory leaks in Xorg and those are often caused by a faulty driver or by a DWM.

Yeah, I have nVidia driver installed. Compiz too.

I have the same compiz setup on my laptop and the memory only runs at 15% of 2Gb.

---

### Post by bmuluu on 2010-03-18
I too have been experiencing problems with my system
these last few days.

Running ```
top
``` gives the following output
top - 21:07:13 up 56 min,  4 users,  load average: 0.17, 0.27, 0.63
Tasks: 196 total,   4 running, 192 sleeping,   0 stopped,   0 zombie
Cpu(s): 13.1%us,  5.6%sy,  0.0%ni, 80.6%id,  0.3%wa,  0.5%hi,  0.0%si,  0.0%st
Mem:   1985692k total,  1903520k used,    82172k free,   339776k buffers
Swap:  8000360k total,       28k used,  8000332k free,   884220k cached

Running ```
free -mt
``` produces:
              total       used       free     shared    buffers     cached
Mem:          1939       1872         67          0        332        876
-/+ buffers/cache:        663       1275
Swap:         7812          0       7812
Total:        9752       1872       7879

I still can't figure out what application is causing
my system to eat up all the RAM and slow down
like this.
Interestingly, the System Monitor still shows memory
usage of only 34.2% of my 1.9GB which is so different
from what top and free are showing.

---

