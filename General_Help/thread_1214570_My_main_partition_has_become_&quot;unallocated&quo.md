---
title: "My main partition has become &quot;unallocated&quot;"
date: 2009-07-16
forum: General Help
---

### Post by felinoel on 2009-07-16
I was following some directions for dual booting Windows and Linux, when I got to a part where it said to free up a partition using the partition editor, I did, it said unalloacted while the main remained, I went to install Windows into the unallocated space and it showed only one partition, when there should have been three. So I read ahead and see it says Windows needs to be installed on the primary partition because its fickle like that, so I go back to the unallocated space and turn it primary, and my main partition seemed fine with that. So then I went back to install Windows again and it still only showed one partition, so I was going to give up and ask for help here but it seems my unallocated partition has taken over my main partition, there is only one, unallocated partition now... 

So my question is, is there any way for me to get my main partition from this merged unallocated partition, or is it not merged, and is erased and unable to unerase?

---

### Post by Legace on 2009-07-16
Post a screenshot of gparted (partition editor).

---

### Post by felinoel on 2009-07-16
> **Legace said:**
> Post a screenshot of gparted (partition editor).

[http://i46.photobucket.com/albums/f130/felinoel/Screenshot.png](http://i46.photobucket.com/albums/f130/felinoel/Screenshot.png)

---

### Post by ramnarayan on 2009-07-16
> **felinoel said:**
> [http://i46.photobucket.com/albums/f130/felinoel/Screenshot.png](http://i46.photobucket.com/albums/f130/felinoel/Screenshot.png)

seems like something did away with your partitions ?? not sure what

Did you have anything you required to keep from the partition.

If not you can go the whole fresh way - first make a small partition for windows (through gparted ) and install windows on that.

Then next install Linux on the remainder

If you want help on this partitioning - ask - will help

---

### Post by ramnarayan on 2009-07-16
if you need to recover anything you might want to use testdisk


[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

which should be available on your live cd session

---

### Post by felinoel on 2009-07-16
> **ramnarayan said:**
> seems like something did away with your partitions ?? not sure what

Did you have anything you required to keep from the partition.

If not you can go the whole fresh way - first make a small partition for windows (through gparted ) and install windows on that.

Then next install Linux on the remainder

If you want help on this partitioning - ask - will help

Sigh, well at least according to the guide it is easier to start with Windows and then add Linux, I was doing it the other way before so easier is good, I will try the TestDisc thing

---

### Post by ramnarayan on 2009-07-16
> **felinoel said:**
> Sigh, well at least according to the guide it is easier to start with Windows and then add Linux, I was doing it the other way before so easier is good, I will try the TestDisc thing

Its very painful installing windows after Installing Linux so avoid that.

testdisk works well - just make sure you read all the help stuff first. And it *really* works

---

### Post by felinoel on 2009-07-16
> **ramnarayan said:**
> Its very painful installing windows after Installing Linux so avoid that.

testdisk works well - just make sure you read all the help stuff first. And it *really* works

I was just about to post for help installing testdisc, but I see you say they have a help page I should look at, lol

---

### Post by felinoel on 2009-07-16
Ok, so I have it running, but it is not showing my main drive, it noticed my dvd drive and a jump drive, then it says some partitions may not appear unless I am root user, I am running an installation disc of Linux, I guess that makes me not the root user? Can I become a root user while only using this disc? I don't want to install Linux for fear I might delete something but is that my only option to become root user?

---

### Post by ramnarayan on 2009-07-16
yes you can do things as root user by typing sudo in front of the command

like```
sudo testdisk
```

if you are on a live version of Ubuntu then testdisk will be available for you to use.

---

### Post by felinoel on 2009-07-16
I used this to figure out how to run it
[http://ubuntuforums.org/showthread.php?t=609586](http://ubuntuforums.org/showthread.php?t=609586)

When I used sudo testdisk it says command not found?

---

### Post by az on 2009-07-16
> **felinoel said:**
> I used this to figure out how to run it
[http://ubuntuforums.org/showthread.php?t=609586](http://ubuntuforums.org/showthread.php?t=609586)

When I used sudo testdisk it says command not found?

sudo apt-get install testdisk

---

### Post by felinoel on 2009-07-16
> **az said:**
> sudo apt-get install testdisk

Thanks, and just curious, above your avatar, is that quoting Zaphod?

---

### Post by felinoel on 2009-07-16
It found my old partition and I thought I restored it, it told me to restart my computer for it to take effect... but nothing... maybe I did it wrong?

---

### Post by felinoel on 2009-07-16
How do I find out my partition table type?

---

### Post by felinoel on 2009-07-16
I am here with TestDisk, and am unsure what to do from here?

[http://img123.imageshack.us/img123/4012/screenshotn.png](http://img123.imageshack.us/img123/4012/screenshotn.png)

---

