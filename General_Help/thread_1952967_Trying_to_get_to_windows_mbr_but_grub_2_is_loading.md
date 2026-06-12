---
title: "Trying to get to windows mbr but grub 2 is loading."
date: 2012-04-05
forum: General Help
---

### Post by Twilk73 on 2012-04-05
Ok I did a big noob mistake. I spent days looking up linux and how to install it and I spent 0 minutes figuring out how to uninstall it. Thus my big mistake.

Ok I turned on my thinkpad and instead of using ubuntu i switched to windows. While in vista I decided I didnt have the the time to learn the whole new language of linux and went to advance user options and cleared the linux partition then merged it back into my vista partition. This left me with my back up partition and windows vista. I turned off my pc and I thought all was good. 

After I start the pc back up it shows my thinkpad screen then goes to a grub 2 error screen. Now I do not have a back up windows cd but I did back up my windows vista on a separate hard drive. I found a way to fix my problem with the windows cd but I dont have a windows cd so is there another option. Can I manually load my windows vista back up. Is their a command I can use to skip grub 2. I was thinking about reinstalling ubuntu and then looking up how to properly remove it but I am not sure if thats the best or easiest way to do this or if thats even possible. 

Things I can do at start up. Load the f12 screen and the think vantage button also works but it takes me to the boot screen and giving me options I am not familiar with. 

Things I have. Windows backed up on a separate hard drive (but I dont know how to load it). I also have ubuntu 11.10 on a pen drive if I have to reinstall it. 

Thanks, Thomas

Would it just be easier to load the pen drive and select the option to dual boot windows and linux then find out how to properly un-install it?

---

### Post by Cheesemill on 2012-04-05
You can fix the Windows MBR using your Ubuntu USB stick:

[http://tips.mistergeek.com/87](http://tips.mistergeek.com/87)


Edit - You are using Ubuntu 11.10 so the instructions will be slighlty different:

In Step 2 hit the Windows key and type 'software sources' and hit the enter key, then enable the Universe repository.
In Step 3 hit the Windows key and type 'terminal' and hit the enter key to open the terminal.

---

### Post by Twilk73 on 2012-04-05
In step two I cant find universal repository so I assumed I was supposed to check
 community-maintained open source software (universe)

but then I get stuck on step three with unable to locate package ms-sys?

ubuntu@ubuntu:~$ sudo apt-get install ms-sys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ms-sys
ubuntu@ubuntu:~$

btw I am running this from the pen drive without actually installing it and I currently have the wifi connected.

---

### Post by Cheesemill on 2012-04-05
Try doing:
```
sudo apt-get update
```
and then continue with installing ms-sys

---

### Post by Twilk73 on 2012-04-05
that command worked however i am still getting unable to locate package ms-sys. I am wondering if I did step two correctly. The only thing I could find close to anything universal was "downloadable from the internet and I checked community-maintained open source software (univers) however proprietary drivers for devices (restricted) is still checked if that matters.

---

### Post by Cheesemill on 2012-04-05
OK, I've had a look for you and it seems it has been removed from the repositories for legal reasons (source [https://answers.launchpad.net/ubuntu/+source/ms-sys/+question/28349](https://answers.launchpad.net/ubuntu/+source/ms-sys/+question/28349)).

You can install it from the internet instead:
```
wget http://ppa.launchpad.net/lenski/ms-sys/ubuntu/pool/main/m/ms-sys/ms-sys_2.2.0-1ubuntu1_i386.deb
sudo dpkg -i ms-sys_2.2.0-1ubuntu1_i386.deb
```

Then continue with step 4 on the page I linked to earlier.

---

### Post by Twilk73 on 2012-04-05
I was just about to post this I found this in the forum. 

[http://ubuntuforums.org/archive/index.php/t-1009707.html](http://ubuntuforums.org/archive/index.php/t-1009707.html)

I tried your way first though and so far so good I will report back in a few minutes.

---

### Post by Twilk73 on 2012-04-05
Your way worked like a charm. You sir are the man!

Man linux was great. I love having the ability to have total control of the device. I really want to make the switch to linux but right now just might not be the time. My time is pretty much used up with everything else going on right now. 

My biggest issue with linux was learning how to install things without using the ubuntu store. If you have any reading on that I would greatly appreciate it. I would also like to know how linux works. I was trying to figure out how much resources it was using what was actually running at start up those sorts of things. I understood some of it but a lot of it was just another language. Lastly if I was to say go back to giving linux another shot tomorrow what would be version to go with.

I have a sprint evo I rooted it the old fashion way with terminal two years ago. I am currently running cm7.2rc1 and to me its the perfect os. Its got a tone of options and its light on the bloat. I removed everything I didnt want including some cm7 stuff and this phone works like a charm. If I could get a linux version with lots of options and is light so that I could only add what I want that would be perfect. However I am new and maybe thats not the way to go for me. If you read this far thanks. You dont have to answer all my questions but if you can point me in any sort of direction weather it be a web site or a good book. I am willing and ready to learn. I tend to really dive deep and learn as much as I can and I think thats why I backed out so quickly with this. Because I got in and I got stuck to many times. I did a lot of reading before hand but obviously not enough.

Anyway sorry for the rambling. This thread is solved.

---

