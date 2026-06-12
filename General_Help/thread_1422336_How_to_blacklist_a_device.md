---
title: "How to blacklist a device"
date: 2010-03-05
forum: General Help
---

### Post by leeper69 on 2010-03-05
Hi I am trying to find out how to blacklist a device in Ubuntu. 
I have a pchdtv 5500 card that I cant get the sound working on and found a reference to the problem on another forum they say to blacklist the device but don't give any instruction on how to do this. Can anyone help me with this?

---

### Post by nothingspecial on 2010-03-05
You need to add the kernel module to /etc/modprobe.d/blacklist.conf

---

### Post by leeper69 on 2010-03-05
I dont know how to do that!
 can you give me a clue?
I just came back to Ubuntu after using Mepis for the past 2 years and am trying to adjust to this operating system. 
thanks for your reply Nothing Special!!!

---

### Post by nothingspecial on 2010-03-05
Sorry,

I don`t know what instructions you are looking at but you need to find out what exactly you need to blacklist. This will be a kernel module that is controlling your sound.

I`m assuming that there is another module that you need to use. Blacklisting a module prevents it from loading at boot. It will not fix your sound unless you have an alternative to load instead.

To find it you could try ```
lsmod | grep snd
```

Then ```
sudo nano /etc/modprobe.d/blacklist.conf
```

and add the module to the end of that file.

I hope that is clearer. 

Perhaps if you posted the link to the instructions I could be of more help.

---

### Post by rnerwein on 2010-03-05
hi
just look in the file wich nothingspecial told you and use any editor ( running as root ) and insert your modul.
ciao

---

### Post by leeper69 on 2010-03-05
THANKS FOR YOUR HELP nothingspecial and merwein 

I used lsmod to find the device (cx88_alsa) then used the root terminal and ch /etc/modprobe. to change to the directory where the blacklist.conf file is then ls -l to see the attributes for blacklist.conf then  chmod og+wxr blacklist.conf to change the attributes so I could use gedit to alter the blacklist.conf file and then added the following lines to the file 
# fix for pchdtv 5500 card with no sound
blacklist cx88_alsa
then saved the file and rebooted 
it disabled the driver for the cx88 chip on the card and the card no longer showed up in the hardware tab in sound preferences but didn't fix my sound problem. 

this is week 2 of trying every venue to get sound out of this card!
 THANKS agin for your help!!!

---

### Post by rnerwein on 2010-03-08
hi
please don't permissions anywhere with out in your home and there only files where you are the owner.
change the permission back to -rw-r-r --r --r
for your sound - sorry no more idea.
ciao

---

### Post by leeper69 on 2010-12-28
I finally got the sound working with my pchdtv5500 card by making a patch cable that is hooked up to the rca output of my direct tv box and the line in on my sound card.

---

