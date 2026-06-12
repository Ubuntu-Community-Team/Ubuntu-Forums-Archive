---
title: "Performance booster"
date: 2006-04-01
forum: General Help
---

### Post by adamkane on 2006-04-01
In order to run Ubuntu at the highest performance possible, you need to have the correct Ubuntu base files installed. 

Ubuntu usually installs the safest base files possible, and leaves it to the user to install the base files that match the user's system.

An added benefit of having the correct base files installed is that you can install several applications that you couldn't previously. kqemu and cdemu are two examples.

If you proceed, there is a chance you won't be able to log in again. Please be sure to have a sound backup policy in place before proceeding.

The results of this:

```

uname -r

``` 
should be this if you have a Pentium PC:

> 
 2.6.12-10-686
  
or this if you have an AMD PC:

> 
2.6.12-10-k7
 
or this if you have an older legacy PC:

> 
 2.6.12-10-386
  

If you do not have the correct version for your system, then proceed.

Do this if you have a Pentium PC:

```

sudo apt-get install linux-686 linux-image-686 linux-headers-686 linux-restricted-modules-686

``` 
Do this, if you have an AMD PC:

```

sudo apt-get install linux-k7 linux-image-k7 linux-headers-k7 linux-restricted-modules-k7

``` 
There is also a 686-smb and k7-smb option for multi-processor PCs, but I'm not an expert on multi-processor systems.

Do this if you have an older legacy PC:
 
 ```

 sudo apt-get install linux-386 linux-image-386 linux-headers-386 linux-restricted-modules-386
 
``` 

Reboot.

After you reboot, do this again:

```

uname -r

``` 
If the result still doesn't match your system, then reboot. When Ubuntu starts to boot up, press [ESC] to access the GRUB menu. You should be able to select the correct kernel for system.

If you don't want to press [ESC] all the time, then you need to edit the GRUB menu list:

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
sudo gedit /boot/grub/menu.lst

``` 
Add "savedefault" along with the kernel you want to boot with. For example:

> 
title        Ubuntu, kernel 2.6.12-10-k7 
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.12-10-k7 root=/dev/hda1 ro quiet splash
initrd        /boot/initrd.img-2.6.12-10-k7
savedefault
boot


---

### Post by dcstar on 2006-04-01
[QUOTE=adamkane]In order to run Ubuntu at the highest performance possible, you need to have the correct Ubuntu base files installed. 
......[/QUOTE]
The appropriate place for something like this is the "Tips and Tricks" forum, and then post a message letting people know about it with a link to the post there.

While it can be helpful to have this information available, the forums will become more cluttered with posts in the wrong sections if people don't try and put things in the expected places.

---

### Post by adamkane on 2006-04-01
The forums will always be irrecoverably disorganized. Everything is mixed together, and I don't even attempt to post in the correct category. 

(I don't want to be critical. The moderators do an excellent job keeping the tone civil, and I could never be as helpful and knowledgable as they are.)

Also I would never seek to promote any of my posts to the level of HOWTO. The gods live in the HOWTO forums. I remain in the General/Gaming forums.

---

### Post by Ian Maxwell on 2006-04-01
After following these instructions, I am getting a kubuntu splash screen on bootup. This isn't the Worst Thing Ever, but is there something I can do about it?

---

### Post by adamkane on 2006-04-01
I found this on another post:

```

sudo update-alternatives --config usplash-artwork.so

``` 
If that doesn't work, search the forums for "boot screen".

---

### Post by djsroknrol on 2006-04-01
GUYS...really, you're both right...David, he's in the wrong message area..it makes searches almost useless..dcstar..no offence but if you want the newbs to learn, you want the searches to be relevent...you could try again...if nothing else but to make it easier for people to find the answers they need..have you tried searches these days???...they don't come up well at all these days...in fact, they're bordering with stupidy...sad....

anyway, a comment on the thread(finally)....

This is an excellent tutorial The right kernal as soon as possible makes all the difference as far as performance and stablity are concerned..Xcompmgr,3ddesk.even problem child ATI boards aren't half bad running in the right environment...

Thank you both for the help you've given me in the past. Again, no offence intended,  and I look forward to you both comming to my aid again...the both of you have knowledge that's badly needed here

---

