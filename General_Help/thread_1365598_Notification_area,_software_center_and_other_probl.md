---
title: "Notification area, software center and other problems after up-date"
date: 2009-12-27
forum: General Help
---

### Post by Ticatla on 2009-12-27
Hi! I am a happy new ubuntu user. Everything went just perfect until some days ago. I have a Dell XPS M1330 with Ubuntu 9.10 karmic koala, kernel linux 2.6.31-16 generic GNOME 2.28.1

I have noticed some nasty problems, I think they appeared after I updated with update manager like 2 weeks ago, but I noticed them until now (was in a place with no internet and rarely use the computer). So here they are:

1) Notification area.

No icon appears and there is no menu after clicking in the area. No volume, battery icon, network manager or anything. This seems to specially affect the network manager because my wireless doesn't connect automatically. I have to use nm-applet on the terminal so it reacts and I can connect, if I close the terminal it goes offline. It is useless to turn on and off my wifi card. If I connect the Ethernet cable the icon do appears. 
The volume control is also affected, it won't play any sound unless I manually (with the keyboard function) turn up the volume. If I restart it gets back to zero. 

Restarting doesn't work, neither adding again or moving the notification area. 

I read a similar thread here: [http://ubuntuforums.org/showthread.php?t=1316676&page=3](http://ubuntuforums.org/showthread.php?t=1316676&page=3) and even a bug report but seems to be a different problem because my icons aren't invisible; they just aren't there.

2) Can't change Visual Effects preferences

In the thread I mentioned someone resolved the problem by changing the Visual Effects to normal. I'm sure I use to have that configuration, but when I looked up it was on "none". I tried to change it to "normal" it starts "searching for drivers", after some seconds a dialog box props saying "Desktop effects could not be enabled".

I have a Nvidia card, and I remember that when I changed the effects to normal or to extra some months ago it searched for the drivers and everything went nice. So I tried to search for the drivers by my self and.....

3) The Software Center will not install anything

I'm quite new at this, you can notice, so I decided to try EnvyNG to install the Nvidia drivers. I went to the Software Center and searched for it. When I clic "install" just nothing happens... nothing. I tried with other software and it is also not working. 

I was going to manually download the drivers but I though that this was strange enough. 

Ah, by the way, I already updated again. I did it manually because the update manager didn't prompt. Nothing changed.

PLEASE HELP and sorry if here wasn't the place to put this thread. 

;_;

---

### Post by Ticatla on 2009-12-28
Hey guys... seriously I need help!

---

### Post by Sef on 2009-12-29
1. For number 3: 

Applications > Accessories  > Terminal 

then copy and paste this command

```
sudo --configure -a
```Not sure if it will help, but it did with me when i had a similar problem.

2. This is a good place to put the thread, but it is best to stick to one problem in a thread.

---

### Post by Ticatla on 2009-12-29
Thanks! 

I tried what you said, but it says it is an invalid option: 


```
sudo: invalid option -- '-'
usage: sudo [-n] -h | -K | -k | -L | -V | -v
usage: sudo -l[l] [-AnS] [-g groupname|#gid] [-U username] [-u username|#uid]
            [-g groupname|#gid] [command]
usage: sudo [-AbEHnPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AnS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...

```How do I stick this thread to another?

---

### Post by avtolle on 2009-12-29
I think Sef meant ```
sudo dpkg --configure -a
```

---

### Post by Ticatla on 2009-12-29
Thanks avtolle... it asked for my password, but then did nothing and the software center still isn't working. 

Any clues in the other problems I mentioned? 

Thank you very much.

---

### Post by Ticatla on 2010-01-01
People HELP PLEASE. Is there any other place where I can ask for help? Should I open a thread for each specific problem? 

Really, I need help.  I can't see the battery icon so I have no idea of how much time I have left on battery power, I can't install the Nvidia drivers and so on... 

Help, please.

---

### Post by wjamoore on 2010-01-15
Join the club..  I had a DDR RAM  die on me whilst the computer was running.  After mucho problems to  boot (mostly caused by compiz which i have removed) i finally got going, but now I am missing all icons in the notification area and if I open applications i cannot switch between them in the bottom panel because there is nothing there.  no trash, no desktop switcher... nothing.

i re-installed all gnome packages to no avail.

I would appreciate any advice

Aaron

---

### Post by chr0n0 on 2010-01-21
I posted what I did to fix "the other problem" with two volume icons at the link that you put in your original posting. Though I never had the "blank" problem, maybe this will help.

[http://ubuntuforums.org/showthread.php?t=1316676&page=3](http://ubuntuforums.org/showthread.php?t=1316676&page=3)

It seems that both of these threads have gotten a little stale, considering the multitude of people on the forums.
I would probably try to fix your Software Center issue first...As an alternative to Software Center, have you tried apt-get or Synaptic Package Manager?

---

### Post by m4tic on 2010-01-21
for the sound icon, try going to your home folder, press Ctrl+H, this will show hidden folders. delete a folder named .pulse

---

### Post by vikingr on 2010-01-23
Upon upgrading to Karmic I found that I had NO Ubuntu Software Center and my icons in the system tray do not appear with each session.  

I went into synaptic and found that "Ubuntu Software Center" *was not* installed; I checked it for installation and now it works fine.

Still working on the icons...

---

### Post by vikingr on 2010-01-23
Right-click on the panel and open the panel properties; click 'show hide buttons' and the notification icons will show up.

---

### Post by rudhra on 2010-02-01
hii friends....i need u help...i m unable to download softwares!!!.....and even cant install updates...i m encountering problems stating that 324mb frees space must be provided in '\' but i have 29.13gb free space in my drive....what should i do??

---

