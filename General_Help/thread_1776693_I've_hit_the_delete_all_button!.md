---
title: "I've hit the delete all button!"
date: 2011-06-06
forum: General Help
---

### Post by Son Of Nova on 2011-06-06
Right, I've deleted everything from my ubuntu 10.10 os. Well done me!
I'd changed my home folder name, thinking there would be no major consequences. 
I got to a window asking to copy all files to the new folder, and in the window I read a checkbox labeled 'delete old folder'. Then I read somewhere in the same window that if you are copying your files across its safe to delete them, so I did. Bad move I guess.

Ubuntu is booting up to the point of loading the default wallpaper, but only the mouse is operational and my keyboards standby hotkey (locked out, if theres anything there to be locked out of!). Theres no right click options. So no access to this 'new folder' if it exists. Im guessing as all of my system files are being bypassed by a registry that is looking for files that arent there. 

If I can restore it to the old files system, that would be rather nice. If not any other ways of getting ubuntu operational again without re-installing, and maybe restoring as much as possible would be appreciated. 

In fact, any help at all would be heroic!

---

### Post by linuxinstalledfromhdd on 2011-06-06
> **Son Of Nova said:**
> Right, I've deleted everything from my ubuntu 10.10 os. Well done me!
I'd changed my home folder name, thinking there would be no major consequences. 
I got to a window asking to copy all files to the new folder, and in the window I read a checkbox labeled 'delete old folder'. Then I read somewhere in the same window that if you are copying your files across its safe to delete them, so I did. Bad move I guess.

Ubuntu is booting up to the point of loading the default wallpaper, but only the mouse is operational and my keyboards standby hotkey (locked out, if theres anything there to be locked out of!). Theres no right click options. So no access to this 'new folder' if it exists. Im guessing as all of my system files are being bypassed by a registry that is looking for files that arent there. 

If I can restore it to the old files system, that would be rather nice. If not any other ways of getting ubuntu operational again without re-installing, and maybe restoring as much as possible would be appreciated. 

In fact, any help at all would be heroic!

None that I know of.  Your best bet is this:

Removed Dead link ~ CharlesA

---

### Post by matt_symes on 2011-06-06
Hi

This may be fixable if you want to give it a go.

If not you can follow Linuxinstalledfromthehdd suposedly one and only suggestion of reinstalling.

Kind regards

---

### Post by Son Of Nova on 2011-06-06
Thanks linux, I'll check it out. 

Just had a thought though, if I install a separate Ubuntu OS onto another partition on the same HDD, might there be some way to access the files from there? At this point I just want to get my documents back, as they contain projects I have completed for college. It's a bugger!

Just out of curiosity, I have Ubuntu and windows installed on this drive, having another partition with a separate ubuntu OS running shouldnt be a problem should it?

> **matt_symes said:**
> Hi

This may be fixable if you want to give it a go.

If not you can follow Linuxinstalledfromthehdd suposedly one and only suggestion of reinstalling.

Kind regards

At this point i'm willing to give anything a go. Im good to go as far as reinstalling goes, I've got my bootable ubuntu installation disk right next to me, beckoning me to whack it in. Thought I'd give damage limitation a go first though.

---

### Post by linuxinstalledfromhdd on 2011-06-06
> **matt_symes said:**
> Hi

This may be fixable if you want to give it a go.

If not you can follow Linuxinstalledfromthehdd suposedly one and only suggestion of reinstalling.

Kind regards

I guess I should have asked how urgent the situation is..  :)   Reinstalling is usually the quickest way to fix something when the user has no idea what they have changed to their system to cause this specific kind of issue --- From my own experience.

---

### Post by seawolf167 on 2011-06-06
If you decide to reinstall, but you do so you can always hit the "Try Ubuntu Before Installing" button on your installation disk to boot into a live environment. From here you can browse folders, copy, move, etc. just like in a "real" installed Ubuntu OS. If you can find your /home folder or any remaining documents you can then copy these to an external hard drive for safe keeping while you reinstall. Note that if you do find your /home folder, ensure that you move it to an ext3/4 formatted drive (not NTFS) to preserve things like permissions.

---

### Post by Son Of Nova on 2011-06-06
> **linuxinstalledfromhdd said:**
> I guess I should have asked how urgent the situation is..  :)   Reinstalling is usually the quickest way to fix something when the user has no idea what they have changed to their system to cause this specific kind of issue --- From my own experience.

Its not urgent really, I did change another setting, but I suspect it was the change I mentioned in the first post that did the deed. I changed the group name of the user to another name (as it was the same name that the home folder was... it had a spelling error in it which was annoying me!) I changed 'the user' setting from 'custom' to 'Administrator' and clicked 'no' to 'password login window on load'.

---

### Post by tgm4883 on 2011-06-06
Not really sure about the rest of what you did, but why did you rename your home folder? And why not just boot into recovery mode and rename it back?

---

### Post by dFlyer on 2011-06-06
Just a note of caution and advice for the future. Before making any major changes to your OS, backup, backup, backup. It's always easier to restore a backup than to have to start over.

---

### Post by Son Of Nova on 2011-06-06
> **dFlyer said:**
> Just a note of caution and advice for the future. Before making any major changes to your OS, backup, backup, backup. It's always easier to restore a backup than to have to start over.

Yes Sir! I've learned my lesson!

I changed the name because I was compulsively correcting a spelling error in the name. No other reason!

I probably should have posted these earlier but hey, its not the first mistake I've made today!

These are the error messages on login, that appear in succession before the default background I mentioned above loads;

Could not update ICEauthority file / home/cimmerian/.ICEauthority

Then;

There is a problem with the configuration server (/usr/lib/libconf2-4/gcon-sanity-check-2 exited with status 256)

Then;

Nautilus could not create the following required folders :/home/cimmerian/Desktop, /home/cimmerian .nautilus

cimmerian is the name of the old home folder before I'd changed it (and ubuntu deleted it). 
I tried recovery mode (failsafe option) but it wouldn't boot. It just kept reverting to the recovery options screen. I might try some of the other options, but I don't really know what they mean.

---

### Post by Son Of Nova on 2011-06-06
> **tgm4883 said:**
> Not really sure about the rest of what you did, but why did you rename your home folder? And why not just boot into recovery mode and rename it back?

That sounds like a plan. Could you run me through the steps to go about doing that? I don't know how to use recovery mode, when I 'boot as normal' through recovery mode, it asks for my login and password, which I supply but I can't hack! I dont know any commands or how to run things from a terminal.

---

### Post by matt_symes on 2011-06-06
Hi

Sorry for the delay. I just had to eat.

> **Son Of Nova said:**
> Yes Sir! I've learned my lesson!

I changed the name because I was compulsively correcting a spelling error in the name. No other reason!

I probably should have posted these earlier but hey, its not the first mistake I've made today!

These are the error messages on login, that appear in succession before the default background I mentioned above loads;

Could not update ICEauthority file / home/cimmerian/.ICEauthority

Then;

There is a problem with the configuration server (/usr/lib/libconf2-4/gconf-sanity-check-2 exited with status 256)

Then;

Nautilus could not create the following required folders :/home/cimmerian/Desktop, /home/cimmerian .nautilus

cimmerian is the name of the old home folder before I'd changed it (and ubuntu deleted it). 
I tried recovery mode (failsafe option) but it wouldn't boot. It just kept reverting to the recovery options screen. I might try some of the other options, but I don't really know what they mean.

All the errors you are getting above are due to the fact you renamed your home folder. Your home folder contains a number of hidden files and folders that specify details about your user session.

When you login, the system looks for your home folder and reads the information in these hidden files and folders to initialise the programs running in your session.
 
gconf-sanity-check-2 is the check gnome makes of its settings to enure they are correct. Gnome is (amongst other things) your desktop and the services and applications your desktop runs.

Nautilus is your file browser and also performs some other functions in gnome.

ICEauthority handles some security functions as far as i'm aware.

You renamed your home folder and now Ubuntu does not know where to look to get these setting; hence your error.

What you need to do to fix this is to rename your folder back to your old user name and, provided you have not changed any of the files in that folder in any major way, you should be able to reboot into your old user.

There are a couple of ways of doing this. You can either do it from the recovery shell as tgm4883 suggested or from a live CD. Which method would you like to do ?

Kind regards

---

### Post by matt_symes on 2011-06-06
Hi

> **Son Of Nova said:**
> That sounds like a plan. Could you run me  through the steps to go about doing that? I don't know how to use  recovery mode, when I 'boot as normal' through recovery mode, it asks  for my login and password, which I supply but I can't hack! I dont know  any commands or how to run things from a terminal.

Looks like i was cross posting with you.

To enter recovery mode what you need to do is reboot your PC. When you  see the Grub menu you need to select the 'recovery mode' option (Or something with the word recovery in it). If  will be under the kernel you normally choose to boot from.

If you see no option to choose a kernel then, just after rebooting,  press and hold the shift key. You will then get the grub menu and you  can select the 'recovery menu' option.

This will boot into a text menu. Hit the down arrow button until you  hightlight the 'root console' option (or something with the word root in it <on 10.04 it is the last option in the list>). Hit enter and it will boot you  into a root text console. There will be no graphical display. Do not let  that worry you. That is normal.

You will then need to enter some terminal commands to rename the folder you changed.

The first thing i would type is

```
ls /home
```That is a small LS above.

This will display all the folders in the home directory. One of the  folders will be the folder name you changed your old folder to. Then  type

mv /home/<folder_name> /home/<folder_folder_name>

where <folder_name> is the name of the folder you changed it to  and can see using the ls command and <old_folder_name> is the  original name of the folder. Folder names are case sensitive and you  must rename back to exactly the same name it had before.

Double check before hitting enter..

Then you need to reboot

```
shutdown -r now
```If you have typed it correctly you should be good to go. If it does not work post back and we will dig deeper.

Kind regards

---

### Post by Son Of Nova on 2011-06-06
> **matt_symes said:**
> Hi



Looks like i was cross posting with you.

To enter recovery mode what you need to do is reboot your PC. When you  see the Grub menu you need to select the 'recovery mode' option (Or something with the word recovery in it). If  will be under the kernel you normally choose to boot from.

If you see no option to choose a kernel then, just after rebooting,  press and hold the shift key. You will then get the grub menu and you  can select the 'recovery menu' option.

This will boot into a text menu. Hit the down arrow button until you  hightlight the 'root console' option (or something with the word root in it <on 10.04 it is the last option in the list>). Hit enter and it will boot you  into a root text console. There will be no graphical display. Do not let  that worry you. That is normal.

You will then need to enter some terminal commands to rename the folder you changed.

The first thing i would type is

```
ls /home
```That is a small LS above.

This will display all the folders in the home directory. One of the  folders will be the folder name you changed your old folder to. Then  type

mv /home/<folder_name> /home/<folder_folder_name>

where <folder_name> is the name of the folder you changed it to  and can see using the ls command and <old_folder_name> is the  original name of the folder. Folder names are case sensitive and you  must rename back to exactly the same name it had before.

Double check before hitting enter..

Then you need to reboot

```
shutdown -r now
```If you have typed it correctly you should be good to go. If it does not work post back and we will dig deeper.

Kind regards

And that is how its done!

+100 hero points to you sir!!

I honestly cannot thank you enough for your time and concise help. And thanks for every one else who took the time to help. I'll be leaving that folder alone from now on!

Cheers buddy!

---

### Post by seawolf167 on 2011-06-06
Now that you have everything back to normal thanks to matt_symes help, I suggest making a disk image with [Clonezilla ]("http://www.clonezilla.org")so if something happens in the future you can easily restore your entire disk to its pre-broken state.

---

### Post by Son Of Nova on 2011-06-06
> **seawolf167 said:**
> Now that you have everything back to normal thanks to matt_symes help, I suggest making a disk image with [Clonezilla ]("http://www.clonezilla.org")so if something happens in the future you can easily restore your entire disk to its pre-broken state.

Yeah I'll give that ago, especially before tinkering with system settings, thanks matey.

---

