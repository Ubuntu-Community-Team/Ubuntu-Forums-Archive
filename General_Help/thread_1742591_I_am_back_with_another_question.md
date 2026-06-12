---
title: "I am back with another question"
date: 2011-04-29
forum: General Help
---

### Post by mattintc10 on 2011-04-29
Again since you guys are very smart people and very helpful i thought id ask again. 

I am beyond confused as to how to use System rescue or Gparted to correct my stupid error of the laptop shutting down while installing ubuntu with out dismounting or what ever may of happend. Any help with this would be much appreciated. :confused:

---

### Post by morgue on 2011-04-29
Don't fully understand. Would you care to elaborate in the issue?

---

### Post by mattintc10 on 2011-04-29
> **morgue said:**
> Don't fully understand. Would you care to elaborate in the issue?

Where i had gone through the installation process of ubuntu i got to harddrive allocate or something like that and it completely froze so i help the power button and it shut off. I went to boot up and **** went south and now it doesn't work for nothing or comes up with an error message and i have google'd it to my fullest and cant figure it out and they say to use System Rescue or Gparted to fix my problem. It sucks big time.

---

### Post by morgue on 2011-04-29
> **mattintc10 said:**
> Where i had gone through the installation process of ubuntu i got to harddrive allocate or something like that and it completely froze so i help the power button and it shut off. I went to boot up and **** went south and now it doesn't work for nothing or comes up with an error message and i have google'd it to my fullest and cant figure it out and they say to use System Rescue or Gparted to fix my problem. It sucks big time.

Mind posting the error message?

Are you familiar with gparted? Looks like you may have interrupted the format process of the drive, or it crashed for some reason, and it seems this is causing the issue.

---

### Post by mattintc10 on 2011-04-29
> **morgue said:**
> Mind posting the error message?

Are you familiar with gparted? Looks like you may have interrupted the format process of the drive, which seems to be causing the issue.

Not really familer all im trying to do is fix my mistake. i wasnt formatting nothing on the harddrive and i made sure not to interupt that.

---

### Post by lisati on 2011-04-29
My thought would be to try the installation again, manually pointing it to any partitions you've already prepared.

---

### Post by mattintc10 on 2011-04-29
> **lisati said:**
> My thought would be to try the installation again, manually pointing it to any partitions you've already prepared.

iv tried the installation over and over and i cant get past the ubuntu loading screen :(

---

### Post by morgue on 2011-04-29
If you can boot to a live cd, try to check what gparted shows.

---

### Post by mattintc10 on 2011-04-29
> **morgue said:**
> Yeah if you can boot to a live cd, just try the install again.

and as i say i try and try and it comes up with an error and what not. i can not get past it and i dont know what i can do if i can boot back into windows and clear something out or what.

---

### Post by morgue on 2011-04-29
> **mattintc10 said:**
> iv tried the installation over and over and i cant get past the ubuntu loading screen :(

Which loading screen? Can you get the wizard going at all?

---

### Post by mattintc10 on 2011-04-29
> **morgue said:**
> Which loading screen? Can you get the wizard going at all?

Loading screen where it says " ubuntu 10.10 " with the dots running back and forth. It will litterly sit there forever or come up with some kind of error.

---

### Post by morgue on 2011-04-29
> **mattintc10 said:**
> and as i say i try and try and it comes up with an error and what not. i can not get past it and i dont know what i can do if i can boot back into windows and clear something out or what.

I edited my message after reading your previous comment.

This sounds like the boot record got damaged, fixing grub might be it, try this
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

---

### Post by mattintc10 on 2011-04-29
> **morgue said:**
> I edited my message after reading your previous comment.

This sounds like the boot record got damaged, fixing grub might be it, try this
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

I feel stupid asking this but how do i open a terminal window? i have yet to figure it out.

---

### Post by morgue on 2011-04-29
> **mattintc10 said:**
> Loading screen where it says " ubuntu 10.10 " with the dots running back and forth. It will litterly sit there forever or come up with some kind of error.

This happens after a fresh install? You need to try to install ubuntu again.

---

### Post by morgue on 2011-04-29
> **mattintc10 said:**
> I feel stupid asking this but how do i open a terminal window? i have yet to figure it out.

Accessories -> Terminal

---

### Post by mattintc10 on 2011-04-29
> **morgue said:**
> This happens after a fresh install? You need to try to install ubuntu again.

No i was never able to install it. it comes to that screen and stops and sits there.

---

### Post by mattintc10 on 2011-04-29
> **morgue said:**
> Accessories -> Terminal

You must understand i never have installed it besides the demo. I am sitting at a purple screen with " ubuntu 10.10 " and 4 dots with a red dots going through. and my CD drive is going nutters

EDIT: now its black and my CD drive is still going nutters

---

### Post by morgue on 2011-04-29
> **mattintc10 said:**
> No i was never able to install it. it comes to that screen and stops and sits there.

Yeah, but if you boot into the live cd and try the fresh install again, what happens?

---

### Post by mattintc10 on 2011-04-29
> **morgue said:**
> Yeah, but if you boot into the live cd and try the fresh install again, what happens?

Well i think its going into demo mode or something strange..... i dont know what the hell i did.

---

### Post by mattintc10 on 2011-04-29
> **morgue said:**
> Yeah, but if you boot into the live cd and try the fresh install again, what happens?

it just sits there and freezes and does nothing at all. or errors out.

---

### Post by morgue on 2011-04-29
> **mattintc10 said:**
> You must understand i never have installed it besides the demo. I am sitting at a purple screen with " ubuntu 10.10 " and 4 dots with a red dots going through. and my CD drive is going nutters

EDIT: now its black and my CD drive is still going nutters

Ok, I guess my suggestion will be to try a live usb image then,  since it's much faster than a cd rom.

Or you can wait for it to load, depending in the system it could take a while to get the live version going.

---

### Post by mattintc10 on 2011-04-29
> **morgue said:**
> Ok, I guess my suggestion will be to try a live usb image then,  since it's much faster than a cd rom.

Or you can wait for it to load, depending in the system it could take a while to get the live version going.

**** it cant connect to the internet this is a big problem. i think its going to get really confused.

---

### Post by morgue on 2011-04-29
> **mattintc10 said:**
> **** it cant connect to the internet this is a big problem. i think its going to get really confused.

Yeah you will definitely need another computer for this

Just go here and follow the "USB stick" steps
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by mattintc10 on 2011-04-29
> **morgue said:**
> Yeah you will definitely need another computer for this

Just go here and follow the "USB stick" steps
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)


I got two computers. the one im replying to you guys with and the one that is the victum of the installation software

---

### Post by mattintc10 on 2011-04-29
> **morgue said:**
> Yeah you will definitely need another computer for this

Just go here and follow the "USB stick" steps
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Mktemp: error while loading shared libraries: /lib/librt.so.1:cannot read file 
Data: input/output error

and then some other stuff of can not open this and that.

Kernal panic - not syncing: attempted to kill init! 

A whole bunch of different stuff. i have pics if you want

---

### Post by morgue on 2011-04-29
> **mattintc10 said:**
> Mktemp: error while loading shared libraries: /lib/librt.so.1:cannot read file 
Data: input/output error

and then some other stuff of can not open this and that.

Kernal panic - not syncing: attempted to kill init! 

A whole bunch of different stuff. i have pics if you want

A search around the forums suggests the Kernel panic message could be RAM or faulty hardware
[http://bit.ly/jo58KQ](http://bit.ly/jo58KQ)

Try to run hardware diagnostics
[http://www.howtogeek.com/howto/16666/diagnose-hardware-problems-with-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/16666/diagnose-hardware-problems-with-an-ubuntu-live-cd/)

I'm out of suggestions myself if it isn't hardware related other than trying to format the hard drive on another computer.

---

### Post by mattintc10 on 2011-04-29
> **morgue said:**
> A search around the forums suggests the Kernel panic message could be RAM or faulty hardware
[http://bit.ly/jo58KQ](http://bit.ly/jo58KQ)

Try to run hardware diagnostics
[http://www.howtogeek.com/howto/16666/diagnose-hardware-problems-with-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/16666/diagnose-hardware-problems-with-an-ubuntu-live-cd/)

I'm out of suggestions myself if it isn't hardware related other than trying to format the hard drive on another computer.


Well if you can be patient instead of trying to use picture's and words il get something better like a youtube video if it will help you any.

---

### Post by morgue on 2011-04-30
> **mattintc10 said:**
> Well if you can be patient instead of trying to use picture's and words il get something better like a youtube video if it will help you any.

[sarcasm]
Sorry for trying to help you solve your issue as fast as possible, my bad. :-s
[/sarcasm]

---

### Post by lisati on 2011-04-30
> **mattintc10 said:**
> Well if you can be patient instead of trying to use picture's and words il get something better like a youtube video if it will help you any.

Um..... if we're not using pictures (or videos) and we're not using words ...... :confused:

---

### Post by yossell on 2011-04-30
> **mattintc10 said:**
> Well if you can be patient instead of trying to use picture's and words il get something better like a youtube video if it will help you any.

I took this merely to mean:

`Well, if you don't mind waiting a bit for me to get it together then I can put together a video demonstrating the issue, rather than (as I've been attempting so far) trying to describe in words or posting low resolution, difficult to read pictures - if you think that would be better'.'

---

### Post by morgue on 2011-05-01
> **yossell said:**
> I took this merely to mean:

`Well, if you don't mind waiting a bit for me to get it together then I can put together a video demonstrating the issue, rather than (as I've been attempting so far) trying to describe in words or posting low resolution, difficult to read pictures - if you think that would be better'.'

Well that is much better, I misinterpreted the previous message.

---

