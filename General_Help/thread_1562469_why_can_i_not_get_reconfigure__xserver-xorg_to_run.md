---
title: "why can i not get reconfigure  xserver-xorg to run"
date: 2010-08-27
forum: General Help
---

### Post by workshop1702 on 2010-08-27
hi when i put sudo dpkg-reconfigure xserver-xorg into terminal then hit the return key it asks for my password which i put in , it then seems to do nothing it doesnt open thexserver page to make any changes . can someone tell me what i am doing wrong please.

---

### Post by ajgreeny on 2010-08-27
> **workshop1702 said:**
> hi when i put sudo dpkg-reconfigure xserver-xorg into terminal then hit the return key it asks for my password which i put in , it then seems to do nothing it doesnt open thexserver page to make any changes . can someone tell me what i am doing wrong please.
You're doing nothing wrong;  that command was deprecated about 18 months ago in either 9.04 or 9.10, I think, and has not done anything at all since that time.

It can be annoying at moments when your graphics are not working properly, I agree, but the xserver is now expected to detect everything and set it up automatically.  If it doesn't, you are sometimes left with a difficult job of manually making an /etc/X11/xorg.conf file and populating it with the needed data.

Why do you think you need to run that command?  We may be able to help if you say what the problem is.

---

### Post by workshop1702 on 2010-08-27
that explains it thought i was an idiot or something , 
my problem is i have bought two new monitors and ubuntu fresh install of ubuntu 10.04 hasn't detected them they are running at 800x600 resolution , i need 1920x1080 i have spent days trying to install them afraid i am getting absolutely] nowhere.](*,) i disparately need some help please.

---

### Post by ajgreeny on 2010-08-28
Probably more related to your graphics card and the drivers being used.  What card have you got and what driver does it use?

Show the output of ```
sudo lshw -C display
```which will tell us both answers, but also make sure you try **System ->Administration ->Hardware Drivers** to see if anything is available for your card.

---

### Post by workshop1702 on 2010-08-28
this is what i get

 *-display               
       description: VGA compatible controller
       product: MGA G400/G450
       vendor: Matrox Graphics, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 85
       width: 32 bits
       clock: 33MHz
       capabilities: pm agp agp-2.0 bus_master cap_list rom
       configuration: driver=matrox_w1 latency=32 maxlatency=32 mingnt=16
       resources: irq:16 memory:d8000000-d9ffffff(prefetchable) memory:da000000-da003fff memory:db000000-db7fffff memory:da020000-da03ffff(prefetchable)

---

### Post by ajgreeny on 2010-08-28
Any drivers available in Hardware Drivers?  I assume this is an old card, and I wonder if a change of driver might help, but I am really now out of my depth, I'm afraid, as I have no knowledge of that card at all.

I see that [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsMatrox](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsMatrox) talks about the card working in 5.04 (5 years ago!) but does not help much more than that.

---

### Post by Steelkilt on 2010-08-28
I have the same Matrox G450 Card.  It has dual heads but my system only sees one head.  The advice I found in another thread was to edit the file:  etc/X11/xorg.conf.  That file does not appear to exist any more.   The forum member was Deathshadow - he had the edits and his advisees were thrilled.

---

### Post by workshop1702 on 2010-08-29
i had this card running two monitors  about two years ago on i think 7.04 ubuntu . 
 seems that everything has changed on ubuntu know for monitor screen resolution set up , nothing i already know works anymore .
I don't seem to be able to even get a foot in the door so to speak on the new versions . 
i just cannot even find where to start. if this is supposed to bee better on the new versions i don't see it , it doesn't work and i have spent about 50 hrs trying to sort it and am no further ahead than when i started . 
this is what makes ubuntu and other linux distributions unusable for many people. i could set this up in 5 minutes on windows . its ridiculous how hard it is to get two monitors working on ubuntu. 
please can anyone help , i would even buy a new graphics card if it gets it going , any suggestions please.](*,)](*,)](*,)](*,)](*,)](*,)](*,)](*,)

---

### Post by Steelkilt on 2010-08-29
Well said.  The current Linux driver on the Matrox website appears to be incompatible with the current version of Ubuntu.  My suspicion is that we do not need the Matrox download - the driver is already installed.  We do need to know how to edit the config file, and that begins with knowing the name of the config file and where it is located.  I hope that makes sense.  Of course, I won't be surprised if it doesn't.

---

### Post by workshop1702 on 2010-08-29
thanks i agree with what you say, the problem is getting someone to help us find it and modify it. i am beginning to think no one knows how to do this apart from the real experts and it seems they have better things to do than help us.
suppose its another evening banging ones head against a brick wall again on google hopping to find a clue on what to do .

Please someone help there must be someone out there that knows how to do this , even getting one monitor going would be a major step.

---

### Post by ajgreeny on 2010-08-29
I can not help with the contents of the xorg.conf file, but I can tell you that if you produce one manually and populate it with the correct information, in the correct format, it will be read by the system at start of your x session.

I have to make one manually for my ATI 9200SE card in order to get the best performance from it.  Unfortunately that does not help with your own make of card, but keep searching in this and other forums and you may find appropriate data to enter into that file.

---

### Post by Steelkilt on 2010-08-29
Where I am stumped is that I do not have an xorg.conf file in my etc/X11 directory.  Everything I have read says it should be there. That file appears to be the key.  That leaves a few possibilities:  (i) Ubuntu 10.04 moved it or no longer uses it, (ii) I deleted it somehow (unlikely) or (iii) the OSS audio package that I installed deleted it.  I can't think of anything else.  Of the three possibilities, I am thinking that the most likely one is that the xorg.conf got re-shuffled in Ubuntu 10.04.  I think I know how to edit the file.  You have to "declare" the second monitor and tell the system that it is on the left, or the right, as the case may be.  My problem now is creating an xorg.conf file.

Thanks.

---

### Post by ajgreeny on 2010-08-30
> **Steelkilt said:**
> Where I am stumped is that I do not have an xorg.conf file in my etc/X11 directory.  Everything I have read says it should be there. That file appears to be the key.  That leaves a few possibilities:  (i) Ubuntu 10.04 moved it or no longer uses it, (ii) I deleted it somehow (unlikely) or (iii) the OSS audio package that I installed deleted it.  I can't think of anything else.  Of the three possibilities, I am thinking that the most likely one is that the xorg.conf got re-shuffled in Ubuntu 10.04.  I think I know how to edit the file.  You have to "declare" the second monitor and tell the system that it is on the left, or the right, as the case may be.  My problem now is creating an xorg.conf file.

Thanks.
Just use gedit to make a text file in your home folder and call it **xorg.conf**, then using terminal command ```
sudo cp xorg.conf /etc/X11/xorg.conf
``` copy it to /etc/X11.

Done!  The difficult bit may be getting the contents correct.

---

### Post by Steelkilt on 2010-08-30
Thank you.

Do you know if there is a command for generating an x session dump?  I have posted this question elsewhere.  I think that would give me the contents of the xorg.conf file.

Thanks again.

---

### Post by ajgreeny on 2010-08-31
> **Steelkilt said:**
> Thank you.

Do you know if there is a command for generating an x session dump?  I have posted this question elsewhere.  I think that would give me the contents of the xorg.conf file.

Thanks again.
Sorry, but I haven't got the faintest idea about that.

---

### Post by Steelkilt on 2010-09-02
The answer was provided on another thread.  Here are instructions for generated an Xorg.conf file *de novo*.

[http://www.osguides.net/operation-sy...buntu-910.html]("http://www.osguides.net/operation-systems/217-how-to-create-xorgconf-in-ubuntu-910.html")

Having done it, I am still in "mirror" mode and am experimenting with edits to my new Xorg.conf file.  So far, I have not screwed anything up.  It just does not come out of mirror mode.  

Do you know if I have to start "xinerama" of use some other command?  My impression is that once both monitors are declared in the Xorg.conf file, there is another step to configuring the system.

Thanks.

JG

---

