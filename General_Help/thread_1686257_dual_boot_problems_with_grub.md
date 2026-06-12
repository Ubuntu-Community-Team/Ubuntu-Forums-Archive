---
title: "dual boot problems with grub"
date: 2011-02-12
forum: General Help
---

### Post by billcecil on 2011-02-12
I have been using Ubuntu for a couple of years and have always had issues with GRUB. Today I lost all my data from my PC trying to get back to ubuntu . If windows has a problem, and you try to repair it, it messes up the MBR and you loose the grub and can't boot to Ubuntu. I suppose I need to just stick to windows for another 20 years or until I can figure this stuff out. Tired of loosing all my data and pictures due to a small issue between the two OSes. I'de use Ubuntu only if I had a printer that would run in linux, but I haven't found one that I could get running and stay running with ubuntu in 2 years either. Search the net to try and get the ubuntu running, and get a bunch of SUDO GREEK that confuses me even more, and copy word for word and just get error or access denied till you get tired and just format the drive. Does anyone know of a stable OS besides windows that will run on PC and can use printers, web cams, etc...?

---

### Post by samacaster on 2011-02-12
First...What type of printers are you trying to run? Ubuntu actually supports quite a large array of printers. Example, I have a Canon IP1800, Ubuntu (and derivatives) only support IP2000 and above. Did I worry...no. Google is your best friend.

One problem: If you've been using Ubuntu for years..shouldn't you have familiarised yourself with some of the basics? Grub (1 or 2) is ridiculously simple. Grub finds all OS's bootloaders...even those that aren't Debian based..... 

As for the "two OS's" BS...You need to look at what your doing wrong.

---

### Post by billcecil on 2011-02-12
One problem: If you've been using Ubuntu for years..shouldn't you have familiarised yourself with some of the basics? Grub (1 or 2) is ridiculously simple. Grub finds all OS's bootloaders...even those that aren't Debian based..... 

Grub is ridiculously simple if you can get to it. If you boot your PC for  a couple months with no problem, then for what ever reason you have a problem, it dont boot. You get to another pc, google, write down what you find. Then go back to your pc, do it, Following any and all I find on Google still causes me to repartition/ format. All I'm saying, is that it's only stable until there's a problem. I didn't grow up on linux. WHen there is a problem, I'll just go straight to the format process and quit wasting my time trying to learn it. back up daily, until I can find out how to fix this ridiculously simple issue. 
 I'm sure I'm doing something wrong, but so far, no one can explain it in such a way that I can understand. I had some problems with windows occasionally not booting, and put in a "Boot disk" and problem solved.

---

### Post by An Sanct on 2011-02-12
Well, if you have problems loading Ubuntu, you can still browse the Ubuntu partition with [ExtFS]("http://www.fs-driver.org/") it is a Windows EXT driver, that will let you see Ubuntu's files.

IMHO there are no problems with printers, 99.9% are plug and play or just use default printer drivers...

I can hardly believe "sudo greek" ... After more than a year, anyone manages to know what they are doing.

GRUB: ... Just **don't** let windows "*fix*" your MBR "*problems*" and you should be fine ...

---

### Post by thefasterblueone on 2011-02-12
> **billcecil said:**
>  If windows has a problem, and you try to repair it, it messes up the MBR and you loose the grub and can't boot to Ubuntu.

Windows broke you MBR, not Ubuntu. This can be a problem when dual booting. But can easily be fixed using Ubuntu, Windows can't fix it, but it will break it.

Try Ubuntu without "dual booting" and learn to fix some of the hardware issues. 
What kind of printer is it? Maybe we can help you get it working.
Everything I plug into Ubuntu works without searching for drivers.

Nobody is making you use Ubuntu. There is a "learning curve". 
If Windows is working so good for you then just keep using it.:P

---

### Post by thefasterblueone on 2011-02-12
> **billcecil said:**
>  If windows has a problem, and you try to repair it, it messes up the MBR and you loose the grub and can't boot to Ubuntu.

Windows broke your MBR, not Ubuntu. This can be a problem when dual booting. But can easily be fixed using Ubuntu, Windows can't fix it, but it will break it.

Try Ubuntu without "dual booting" and learn to fix some of the hardware issues. 
What kind of printer is it? Maybe we can help you get it working.
Everything I plug into Ubuntu works without searching for drivers.

Nobody is making you use Ubuntu. There is a "learning curve". 
If Windows is working so good for you then just keep using it.:P

---

### Post by billcecil on 2011-02-12
Finally someone beginning to make sense If I'm stupid, don't ask for help. I'm on a few other forums, and when folks have problems, other folks help them. Here, you do a search, and spend days trying to make sense of what seems to be easy to all of the people here that have master's degrees in linux, and if it don't make sense to some one, don't bother us at almighty UBUNTU forum.

---

### Post by Rubi1200 on 2011-02-13
> **billcecil said:**
> Finally someone beginning to make sense If I'm stupid, don't ask for help. I'm on a few other forums, and when folks have problems, other folks help them. Here, you do a search, and spend days trying to make sense of what seems to be easy to all of the people here that have master's degrees in linux, and if it don't make sense to some one, don't bother us at almighty UBUNTU forum.
Hi and welcome to the forums :-)

There is no such thing as a stupid question and you are obviously struggling with certain issues. We are here to try and help.

If you need further assistance, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

The results will hopefully give us a clearer picture of what is going on and will certainly make offering solutions easier.

Thanks.

---

### Post by billcecil on 2011-02-13
Thanks Rubi1200 for trying to answer with an understanding that I'm not a linux guru. 
I think what my problem is, is that the answers I get when using the search here on the forum, are from folks assuming everyone has the same ubuntu knowledge they have. I think I need to go to the library and get a book that starts at the beginning.

Thanks again Rubi but it's all still over my head.

---

### Post by Rubi1200 on 2011-02-13
> **billcecil said:**
> Thanks Rubi1200 for trying to answer with an understanding that I'm not a linux guru. 
I think what my problem is, is that the answers I get when using the search here on the forum, are from folks assuming everyone has the same ubuntu knowledge they have. I think I need to go to the library and get a book that starts at the beginning.

Thanks again Rubi but it's all still over my head.
With anything new there is a learning curve. Reading is a very good place to start. Here are some links that might also help:
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)
[http://sites.google.com/site/easylinuxtipsproject/Home](http://sites.google.com/site/easylinuxtipsproject/Home)
[https://help.ubuntu.com/community/CommonQuestions](https://help.ubuntu.com/community/CommonQuestions)

Feel free to ask for help and I will try and assist you as best I can.

---

### Post by hippi80 on 2011-02-13
I like Billcecil am having some troubles with my dual boot.  from what i have read here the prob is likely one caused by windows.  I also am a bit of a novice in linux.  the biggest prob. i run into is that while i can fallow instructions and usually work out a prob, i don't realy know what these commands mean, ( with a few exceptions ) and don't really know how to do anything without the GUI.  so the two questions i have are: 

1 should i do what you recomended billcecil do with booting ubuntu ( i get an error 3 times then it either boots or doesn't, and windows just takes about 5 mins to boot now).  no exaggerations.  

2, where should i start in learning how to actually operate this os ?  


subnote, i really only stick with windows because i can't play most of my games in linux or watch netflix instant watch.   i still try and learn how to do it on linux out of sheer stuborness and a strong dislike for windows the corp. 

ty for your time :)

---

### Post by Quackers on 2011-02-13
billcecil, a tip.
If your Ubuntu installation is broken (whether by Windows or not), there is no need to go looking for a second computer. Boot from the live cd/usb, connect to the internet and you're good! Any required fixes can be done from the live cd environment. If the fix is to re-install grub, it will take no more than 5 minutes (and possibly more like 60 seconds).
It will save you many re-installs :wink:

---

### Post by mr clark25 on 2011-02-13
if grub ever gives you any issues, boot a live cd/usb, connect to the internet and run the following:
```

cd ~/Desktop/ && wget http://207.68.218.64/linux/scripts/grubfix && sudo bash ~/Desktop/grubfix

```

this is a script i made a while back that will ask you some questions about your partition layout, and then (re)install grub for you. (usually fixing any grub issues no matter how messed up it was)

this could be just what you are looking for.

---

### Post by billcecil on 2011-02-13
> **hippi80 said:**
> I like Billcecil am having some troubles with my dual boot.  from what i have read here the prob is likely one caused by windows.  I also am a bit of a novice in linux.  the biggest prob. i run into is that while i can fallow instructions and usually work out a prob, i don't realy know what these commands mean, ( with a few exceptions ) and don't really know how to do anything without the GUI.  so the two questions i have are: 

1 should i do what you recomended billcecil do with booting ubuntu ( i get an error 3 times then it either boots or doesn't, and windows just takes about 5 mins to boot now).  no exaggerations.  

2, where should i start in learning how to actually operate this os ?  


subnote, i really only stick with windows because i can't play most of my games in linux or watch netflix instant watch.   i still try and learn how to do it on linux out of sheer stuborness and a strong dislike for windows the corp. 

ty for your time :)

I see I'm not the only one on the planet that hasn't got it yet. I can't tell you how to do it or what to do as far as the dual boot problem, but as for me, I now have two separate hard drives, with fresh installs of each, one with windows, and one with ubuntu. I'll unplug the drive and plug it into the other if I need to switch. Until I learn, I'll do it that way. no more GRUB for me. I've lost too much time and data to go through it again.

---

### Post by billcecil on 2011-02-13
I'm sure that each of you has given sound advice and the things that you've told me to do probably have worked, but for what ever reason, I loose all I have on my hard drive each time.

---

### Post by VinDSL on 2011-02-13
> **billcecil said:**
> [...] no more GRUB for me. [...]GRUB isn't the problem; it's the cure!

The 'problem' is, your computer is infected with Windows...  :D

I have two machines that I dual boot Linux/Windows via GRUB (a Mint/Vista lappy and a Mint/XP netbook).

I don't have time to write a step-by-step tutorial, but...

Basically, I divide a clean HDD in half (2 equal size partitions) using GParted.  Then, I HIDE the second partition.

On the first partition, I install Windows.

Then (once again) I use GParted to HIDE the first partition, and UNHIDE the second partition.

Next, I install Linux on the second partition.  

GRUB will find Windows, even though it's hidden.  Windows will not recognize Linux, even if it's unhidden.

Finally, after Linux/Windows is installed, I tweak my GRUB entries to HIDE Windows when I select Linux -- and HIDE Linux when I select Windows.

Hopefully, that makes sense!

Bottom line:  It's best to hide Linux from Windows, on a dual boot machine.  

Microsoft hates Linux (et al.) and Windows will stomp on your Linux install, like a cockroach, if you let it!  ;)

---

### Post by hippi80 on 2011-02-14
Mr Clark, thanks for the script, but i keep getting this error
 { starting...
mount: wrong fs type, bad option, bad superblock on file:///media/52b60377-49d4-4989-b3a8-40c52a482fa3/boot/grub,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

/usr/sbin/grub-probe: error: cannot find a device for /mnt/hd/boot/grub (is /dev mounted?).
if no errors were produced, the grub install should have gone smoothly.}

i don't know what i have done wrong.  when asked for address of hd i coppy past from file browser, and as for boot folder i have tried coppy pasting both that and the grub folder addy's.  no love.  any ideas ?  

ty

should i try using the hd that windows is installed on ?  strikes me as a bad idea ...

---

### Post by hippi80 on 2011-02-14
nm previous, i figured out what i was doing wrong.  now to figure out other probs ....

and thanks again for grub fix  :D

---

