---
title: "Setting up an Ubuntu Server, have some questions:"
date: 2006-04-08
forum: General Help
---

### Post by Johhhn on 2006-04-08
Hi,

I'm setting up an Ubuntu 'server' for a relative of mine in an office of about 3-4 windoze xp machines.  The machine that will be the server is a P4 1.3ghz Gateway.

I'm not a complete novice, but have been out of the Linux game for quite some time-- I'm experienced in OS X and have been using some degree of Unix since '90 or so.  With that said, I have the following questions:

1- I plan on setting up the server with a 200G internal drive.  Am I limited by the IDE controller in the PC to be able to set this up as one partition?  Or, do I need a newer IDE card?  I was thinking of getting a newer IDE card anyway, as I'm sure the one that's built-in is ATA 66 or similar.

2- The backup drives I want to use will either be
    a) Two external 200G Firewire, which leads me to another question:
         i) Can I install any FireWire card in this computer and it 'automagically' work?
    b)  I may setup, instead, two additional internal 200G drives with removable trays.

Question: Are both options easy to do?

3- Backup Software
    a) I want incremental backups- any 'simple' backup programs exist to do this?  Or should I just use rsync to backup the server to the backup drives?
    b) My cousin wants to be able to take one of the backup drives home every night, is it
         i)  OK to just unplug the FireWire drive and have him take it, and then in the morning plug it back in?  Or will I have to write a script to unmount and remount?
         ii) If we do the internal removable drive setup, is it the same as the above?

4- Stability/Speed/Admin
     a) Will be using Samba to allow the other 3-4 XP machines to access the server.  The server will host several gigs of AutoCad and word/excel files.  Any known issues of storing AutoCad files on a samba server?
     b) This will be on a 100mbit network, so speed **shouldn't** be an issue, but will a P4 1.3 with 512M be sufficient?  
     c) The server will be in a closet, ventiliated and if necessasry, I'll install extra fans in the machine to keep it cool.  No one will have access to the server, but myself and my cousin- whose limited function will be to remove and reinstall the backup drive on a daily basis.
     d) Webmin? Or is there something else in Ubuntu that can be used to configure Samba, etc.?  I prefer to use GUI over cli, simply because I'm on a Mac and there have been many GUI'd terminal apps written- I hope the same exists on Linux??  I know it may not be as widespread, but shit, it's 2006!! :-D Either way, like I mentioned earlier, I can use the terminal if necessary.
     e) Want to make sure-- if Bobby is using xyz.doc file, and Jimmy tries to access that same file, will Samba not allow it? 

I think I have most of my questions/concerns covered.  I'm very eager to start this (hopefully next week) and so want to make sure I'm convered on things I'm not as familiar with.

Please add anything else that I should pay attention to on things I may have overlooked.

Thanks in advance!!

---

### Post by Johhhn on 2006-04-18
74 views and no replies???

bump!

---

### Post by jamesdodd on 2006-04-18
Your asking quite a lot of questions. Most of which aren't even Ubuntu related :-k 

But I will try and answer a few for you

[QUOTE=Johhhn]
1- I plan on setting up the server with a 200G internal drive.  Am I limited by the IDE controller in the PC to be able to set this up as one partition?  Or, do I need a newer IDE card?  I was thinking of getting a newer IDE card anyway, as I'm sure the one that's built-in is ATA 66 or similar.
[/QUOTE]
You might want to test the drive in the machine first before splashing out on an ATA card. But you might want to consider one anyway. Possibly SATA or ATA 133 for that extra performance...


[QUOTE=Johhhn]
2- The backup drives I want to use will either be
    a) Two external 200G Firewire, which leads me to another question:
         i) Can I install any FireWire card in this computer and it 'automagically' work?
[/QUOTE]
I'd probably reccomend USB2 drives:
a) the card would be cheaper if the machine doesn't have it already
b) More computers have USB than firewire so accessing backups isn't as limited

[QUOTE=Johhhn]
    b)  I may setup, instead, two additional internal 200G drives with removable trays.
[/QUOTE]
Internal Drives will probably need to the machine to be powered down before removal (could be different for some computers with hot swap bays etc...)


[QUOTE=Johhhn]
3- Backup Software
    a) I want incremental backups- any 'simple' backup programs exist to do this?  Or should I just use rsync to backup the server to the backup drives?
[/QUOTE]
Probably. just google for them
I'd probably write a few small scripts, but then I've not tried other software for the purpose :confused: 


[QUOTE=Johhhn]
    b) My cousin wants to be able to take one of the backup drives home every night, is it
         i)  OK to just unplug the FireWire drive and have him take it, and then in the morning plug it back in?  Or will I have to write a script to unmount and remount?
[/QUOTE]
Probably best setting up a small script to to unmount the drive first, just incase its being accessed (don't want to damage it do you :))...


[QUOTE=Johhhn]
Any known issues of storing AutoCad files on a samba server?
[/QUOTE]
Not that I'm aware of....


[QUOTE=Johhhn]
     b) This will be on a 100mbit network, so speed **shouldn't** be an issue, but will a P4 1.3 with 512M be sufficient?  
[/QUOTE]
Depends on how much it will be accessed and what sort of file sizes its dealing with. You mentioned AutoCad, So I will presume pretty large...
an extra 512MB wouldn't harm it and I would reccomend it...
But then I'd also reccomend 1Gbit Network, but this will be too costly so ignore me

[QUOTE=Johhhn]
     d) Webmin? Or is there something else in Ubuntu that can be used to configure Samba, etc.?  I prefer to use GUI over cli, simply because I'm on a Mac and there have been many GUI'd terminal apps written- I hope the same exists on Linux??  I know it may not be as widespread, but shit, it's 2006!! :-D Either way, like I mentioned earlier, I can use the terminal if necessary.
[/QUOTE]
I'd say webmin or similar if you can afford the extra resources... but if you can cope with terminal then use it... the more you use it the more comfortable you get :) GUI are designed to be self explanatory in most cases so if you ever switch there isn't a learning curve


[QUOTE=Johhhn]
     e) Want to make sure-- if Bobby is using xyz.doc file, and Jimmy tries to access that same file, will Samba not allow it? 
[/QUOTE]
I have no idea :confused: I wouldn't think so... I've never encouted that problem, but don't think I've tested it, might be able to let you know later...
But I'd have to say that there wouldn't be a problem at the moment...

The only problem could be down to different versions of the file:
Bobby opens file at: 10am, modifies and saves at 10:50am
Jimmy opens file at 10:15am modifies and saves at 10:30am

---

### Post by Johhhn on 2006-04-18
Thanks James, I appreciate your response. While, some of my questions aren't exactly Ubuntu related, some of them *are* still 

1- The external drives will be COMBO, so they will have both USB and Firewire. Firewire is a lot faster than USB, hence why I want to get a firewire card.

2- If I go SATA, do I still need to power down?

3- I read a thread on SlashDot about Ubuntu and a lot of people talked about how xyz version is 'stable', etc.. Is Ubuntu, or any other Linux variant, inherently unstable and so people have to comment on how stable it is??

---

### Post by Face1 on 2006-04-19
Actually, USB2 *is* faster than firewire. True USB2 = 480 mb/s, IEEE1394 = 400 mb/s, I believe.

You will probably need to power down, yes, as it is an intenal drive.  I've never heard about internal drives being removable while on.  But hey, there's lots of things I've never heard of.

Can't help you with 3.

---

### Post by Johhhn on 2006-04-19
Actually, USB2 is not.  Sure, the 'specs' for it says it is, but in actual reality, it is a lot slower.

Not sure how versed you are, but I invite you to google many of the benchmarks out there, or purchase a combo drive yourself so you can see how much faster Firewire is ;)

Not all computers have to power down- if you have a removable sled, you should be able to unmount it, then remove it, but alas, not familiar with Ubuntu, hence my questions.

[QUOTE=Face1]Actually, USB2 *is* faster than firewire. True USB2 = 480 mb/s, IEEE1394 = 400 mb/s, I believe.

You will probably need to power down, yes, as it is an intenal drive.  I've never heard about internal drives being removable while on.  But hey, there's lots of things I've never heard of.

Can't help you with 3.[/QUOTE]

[QUOTE=jamesdodd]Your asking quite a lot of questions. Most of which aren't even Ubuntu related :-k 

But I will try and answer a few for you


You might want to test the drive in the machine first before splashing out on an ATA card. But you might want to consider one anyway. Possibly SATA or ATA 133 for that extra performance...



I'd probably reccomend USB2 drives:
a) the card would be cheaper if the machine doesn't have it already
b) More computers have USB than firewire so accessing backups isn't as limited


Internal Drives will probably need to the machine to be powered down before removal (could be different for some computers with hot swap bays etc...)



Probably. just google for them
I'd probably write a few small scripts, but then I've not tried other software for the purpose :confused: 



Probably best setting up a small script to to unmount the drive first, just incase its being accessed (don't want to damage it do you :))...



Not that I'm aware of....



Depends on how much it will be accessed and what sort of file sizes its dealing with. You mentioned AutoCad, So I will presume pretty large...
an extra 512MB wouldn't harm it and I would reccomend it...
But then I'd also reccomend 1Gbit Network, but this will be too costly so ignore me


I'd say webmin or similar if you can afford the extra resources... but if you can cope with terminal then use it... the more you use it the more comfortable you get :) GUI are designed to be self explanatory in most cases so if you ever switch there isn't a learning curve



I have no idea :confused: I wouldn't think so... I've never encouted that problem, but don't think I've tested it, might be able to let you know later...
But I'd have to say that there wouldn't be a problem at the moment...

The only problem could be down to different versions of the file:
Bobby opens file at: 10am, modifies and saves at 10:50am
Jimmy opens file at 10:15am modifies and saves at 10:30am[/QUOTE]

---

### Post by Face1 on 2006-04-19
Well, you're clearly better informed than I am, so I'll stay out of this ;P.

---

