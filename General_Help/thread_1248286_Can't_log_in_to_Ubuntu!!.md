---
title: "Can't log in to Ubuntu!!"
date: 2009-08-24
forum: General Help
---

### Post by | Gnome | on 2009-08-24
First Hello to all! I am new here.
I got a problem. I am new to Ubuntu. (Ubuntu 9.04)
I dual boot my system with Windows XP and Ubuntu. 
Yesterday when I tried to log in to Ubuntu it showed following message. 

**Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix the problem**

I tried cleaning up the disk also. I don't know what to do next. I can't log in. Please help!
Thanks in advance.

---

### Post by Appiah on 2009-08-24
Log into console check the permission of your .ICEauthority .

---

### Post by zkriesse on 2009-08-24
You could either do a failsafe login mode or try booting from the Live Cd and doing the repair system option. Go here first though. [Ubuntu Documentation and Help!]("https://help.ubuntu.com/")

---

### Post by | Gnome | on 2009-08-24
> **Zachk18 said:**
> You could either do a failsafe login mode or try booting from the Live Cd and doing the repair system option. Go here first though. [Ubuntu Documentation and Help!]("https://help.ubuntu.com/")

I tried to log onto Failsafe login mode also. But I was not allowed, same message appears.
Will repairing system from Live CD  delete all the updates I had done??
Isn't there any other solutions??

---

### Post by P4man on 2009-08-24
is it possible you deleted your homefolder? 
Boot from the live cd. Then open your harddisk (places > name of hd).

Browse to:

/media/disk-whatever-its-name/home

Do you see a folder with your username as name?

If so, right click it, chose properties, permissions and check who is the owner (should be you) and if you have read/write permissions on it.

If it doesnt exist, report back;

---

### Post by | Gnome | on 2009-08-24
Sorry to say there is not any folder named  home. I have installed ubuntu inside windows (c-drive). Inside c-drive there is only one folder named ubuntu, except other windows folders.

---

### Post by P4man on 2009-08-24
oh.. a wubi install. I got no idea how to recover from that :s

Its probably possible to mount it from a live cd, and then start troubleshooting, but it may be more hassle then its worth. Do you got a lot of documents in there that needs saving?

I think you got to the point where  you are now, by accidentally deleting your homefolder, or by running "sudo nautilus" (instead of gksudo nautilus") or another graphical program ruining your permissions. The issue is probably solvable, but a reinstall on a dedicated partition might be something to consider...

---

### Post by wojox on 2009-08-24
You may want to open the control panel and click Programs and see if you can repair or change the wubi install.

---

### Post by | Gnome | on 2009-08-24
^P4man
I am quite sure, I didn't delete that folder. So, how did it got deleted? I wanna know.
BTW, there's no any necessary data.
You said "a reinstall on a dedicated partition might be something to consider". Does that mean, a "wubi install" shows frequent problems than that one. After installing on a dedicated partition, I don't have to suffer through such problems or what??
Actually, I had just installed Ubuntu and just updated waiting for a long time in my dial up net. I don't want to lose it. 
If there's any other option, please let me know! Thanks for the responses.

^wojox
There's no any option like that, other than just to uninstall.

---

### Post by P4man on 2009-08-24
> **| Gnome | said:**
> ^P4man
I am quite sure, I didn't delete that folder. So, how did it got deleted? I wanna know.

I didnt say it got deleted, but when you google the error you got, most ppl either seemed to have lost their homefolder, or no longer had permissions to access it. Since you said you where "cleaning up", I guessed you might have been a bit over enthusiastic in deleting stuff.

A common cause for being unable to access or no longer have write access to your homefolder, is running nautilus or other graphical programs as root, using "sudo nautilus" instead of "**gk**sudo nautilus". That can cause a permission mess. Be very warry you never run sudo nautilus, even though people may tell you here sometimes!

> You said "a reinstall on a dedicated partition might be something to consider". Does that mean, a "wubi install" shows frequent problems than that one. After installing on a dedicated partition, I don't have to suffer through such problems or what??

Well, I wouldn't go that far, but at least a regular install is easier to troubleshoot. And if your windows setup and/or drive get messed up, it can't take the ubuntu install along with it. Whatever it was that happened to you now, I doubt it had anything to do with a wubi install, but if it had been regular install, it would have been quite a lot easier to repair it without reinstalling.

> Actually, I had just installed Ubuntu and just updated waiting for a long time in my dial up net. I don't want to lose it. 
If there's any other option, please let me know! Thanks for the responses.


I dont know how you can "transfer" a wubi install to a dedicated partition without problems. probably best you keep wubiing for now :)

---

### Post by | Gnome | on 2009-08-24
> **P4man said:**
> I didnt say it got deleted, but when you google the error you got, most ppl either seemed to have lost their homefolder, or no longer had permissions to access it. Since you said you where "cleaning up", I guessed you might have been a bit over enthusiastic in deleting stuff.

No, no, I did that(cleaning up) after that problem occured. 


> **P4man said:**
> probably best you keep wubiing for now :)

how to keep wubiing if ubuntu is not letting me log in??:confused:

BTW, Why aren't others responding?

So, reinstalling is my last resort then???
So sad!!

---

### Post by P4man on 2009-08-24
sorry, I misread. I understood you had already reinstalled.

Ok, so you say recovery mode doesnt work. But when you choose recovery mode, do you get a menu at least ? In that menu, can you select "root shell" ? It shouldnt require logging in. If that works, we can try a few things. Let me know. If that doesn't work, Ill need to find out how you mount a wubi install from a live cd.

---

### Post by | Gnome | on 2009-08-24
yah I can access to root shell.

---

### Post by P4man on 2009-08-24
ok, in that root shell try this:
```

sudo chown -R user_name /home/user_name
sudo chmod 755 /home/user_name
sudo rm -rf /home/user_name/.dmrc 
```


replace username with your username.
Make sure you dont make any typo's, and beware these things are CaSe SenSiTiVE!

---

### Post by | Gnome | on 2009-08-24
Ok, I did it, but nothing seemed to happen. Now what next??

---

### Post by Don1500 on 2009-08-24
Did you say you just installed and don't have anything of substance on the Ubuntu system (other than Ubuntu.)

If yes, why use wubi? Ubuntu is much more stabel on it's own. Then try wine to get the windows programs you would like. I have two HD's so I have onewith windows and one with linux(Ubuntu 9.04 and Kubuntu Alpha (9.10)) if I lose one I don't lose everything.

---

### Post by P4man on 2009-08-24
> **| Gnome | said:**
> Ok, I did it, but nothing seemed to happen. Now what next??

reboot, cross finger, and let me know what happens.

---

### Post by zkriesse on 2009-08-24
> **P4man said:**
> reboot, cross finger, and let me know what happens.

I definitely agree with P4man....re-install and then let us know.

---

### Post by | Gnome | on 2009-08-25
[QUOTE Zachk18;7840252]I definitely agree with P4man....re-install and then let us know.[/QUOTE]

p4man is not talking about reinstall.

^p4man
i did as u said and rebooted also. But the problem persists.
When i used the commands u gave, nothing seemed to happen.  After completing the commands there ought to be something isnt it?

---

### Post by P4man on 2009-08-25
> 
i did as u said and rebooted also. But the problem persists.
When i used the commands u gave, nothing seemed to happen.  After completing the commands there ought to be something isnt it?

These commands dont give feedback unless there is a problem, so what you saw (nothing) is normal.

Ok, time to check a few other things then. do you have any free space? Type:

```
[COLOR="Red"]df[/COLOR] -h
```

and report the available space for the drives (/dev/sdsomething, the rest doesn't matter).

 also if you can give me the output of :

```
ls -l /home
```

---

### Post by | Gnome | on 2009-08-25
Sorry for the late response.
Here's the result:
              
a)df -h
              
**/dev/sd7 **
size    2.3G     
used   2.1G          
available      148 M    
use%     94%  
Mounted on      /


b) ls -l /home

total4
drwxr-xr-x 39 rosun rosun 4096 Aug 25 23:02 rosun

where rosun is my username.

---

### Post by P4man on 2009-08-25
Is sd7 the drive on which you installed ubuntu?? 2.3 GB ? Wow, I didnt even know it would let you install on such a small partition. 

Its too small mate, you really need more space than that.  How big (small) is your harddisk? Or are you installing on CF card or something?

---

### Post by | Gnome | on 2009-08-25
I don't know that. My HDD is 80GB. I have three partitions and C-drive has 20GB. I had installed Ubuntu inside WIndows. I don't know how it got hold of only 2.3 GB!!

---

### Post by P4man on 2009-08-25
I just googled to see how you can resize a wubi virtual partition, and guess what I found :)

[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

Not only does it let you resize (see bottom) it also lets you move the install to a new disk or partition.

---

### Post by | Gnome | on 2009-08-25
First I need to make sure that my ubuntu install (wubi install) is secure and not broken. What do you say?? How to find out that. If it's useless then there's no point of using that.

---

### Post by P4man on 2009-08-25
you could try making some more space perhaps.

boot in to the root shell again, and type:

```
sudo apt-get clean
sudo apt-get autoremove
```

If you downloaded any packages, it will delete the cached versions of them.
perhaps you can delete some large (well, not really lol) files in your home folder ? 

```
cd /home/yourusername
ls -l
```

to delete a file then type
```
rm nameoffile
```

---

### Post by | Gnome | on 2009-08-26
Ok, seems like there is no other option for me than to reinstall Ubuntu. 
If is it so, then I am going to install it on another dedicated partition. I have a limited HDD space, so I can only give maximum 10-15 GB space to it. Is it sufficient?? My data will be on another partition and windows on yet another. 
Also please tell me the easiest and safest way to install it. I don't want to suffer from same problem again.

Thanks!!

---

### Post by Don1500 on 2009-08-26
> **| Gnome | said:**
> Ok, seems like there is no other option for me than to reinstall Ubuntu. 
If is it so, then I am going to install it on another dedicated partition. I have a limited HDD space, so I can only give maximum 10-15 GB space to it. Is it sufficient?? My data will be on another partition and windows on yet another. 
Also please tell me the easiest and safest way to install it. I don't want to suffer from same problem again.

Thanks!!

Please, Where do you live? Hard drives are relitivly cheap in the US $50 can get you 100Gig (Imagine that 10 years ago!), I got .5 tbite for under $150. Just get another drive and hook 'er up.

---

### Post by P4man on 2009-08-26
> **| Gnome | said:**
>  I can only give maximum 10-15 GB space to it. Is it sufficient?? 

Depends how much you will use it and install on it obviously, but for the OS and a reasonable amount of apps, yeah it should do.
> 
My data will be on another partition and windows on yet another. 
Also please tell me the easiest and safest way to install it. I don't want to suffer from same problem again.

So many how-to's out there :)
Short version: in windows, defrag your drive. Boot the live CD, run installer. When you get to the partitioning stuff, the installer will probably suggest to resize the windows partition to make room. If so, do that. If that fails because you have several partitions, then do the manual partitioning. Resize the windows partition. Create an Ext3 (or 4) partition that you assign "/" as mount point, and create a swap partition that is a few GB in size (bit bigger than the size of your ram if you want to use hibernate, at least 1GB if you have less than 1 GB Ram)

If you got any question, from the live cd, you can connect to the web and post here, perhaps include screenshots or output of "sudo fdisk -l" if needed.

---

### Post by P4man on 2009-08-26
> **Don1500 said:**
> Please, Where do you live? Hard drives are relitivly cheap in the US $50 can get you 100Gig (Imagine that 10 years ago!), I got .5 tbite for under $150. Just get another drive and hook 'er up.

$150 isnt cheap everywhere in the world. Some places thats close to a month salary, keep that in mind :)

---

### Post by | Gnome | on 2009-08-27
> **Don1500 said:**
> Please, Where do you live? Hard drives are relitivly cheap in the US $50 can get you 100Gig (Imagine that 10 years ago!), I got .5 tbite for under $150. Just get another drive and hook 'er up.

i dont live in the US like u and dont have such resources as u do. And i agree wid P4MAN.

---

### Post by Tsega on 2009-09-08
I have the same problem, but my I believe mine is a little bit complicated. I was trying to set my $JAVA_HOME enviornment variable and I think, I might have messed up my bash settings. Here is what I get after entering in my user name and password:

"Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem."

The details of the ~/.xsession-errors

/etc/gdm/xsession Beginning session setup...
/etc/profile: 26: id: not found
[: 26: Illegal number
/etc/gdm/xsession: 179: grep: not found
/etc/gdm/xsession: 192: ls: not found
/etc/gdm/xsession: Executing default failed, will try to run x-terminal-emulator
exec: 205: x-terminal-emulator: not found

I have tried every suggestion in this thread but I can't even log in using the failsafe sessions. I did manage to delete the extra entries from my /etc/profile, ~/.bashrc, /etc/bash.bashrc, but nothing seems to happen. I even had(meaning I removed it) this shell script in /etc/profile.d/javahome.sh that contained the following:

export JAVA_HOME="path yo my java directory" 

Well anyways that where I am right now, so can someone please help.

---

### Post by Tsega on 2009-09-09
Help someone, anyone! :(

---

