---
title: "How to change default boot?"
date: 2010-02-21
forum: General Help
---

### Post by Tsun on 2010-02-21
I love everything in ubuntu...
...except the fact that installing something which would take 5 seconds in windows takes 15minutes in ubuntu. Assuming i get it installed at all.

Anyway, i want to change it so that the GRUB opens Vista by default.
I don't want to uninstall ubuntu because i still prefer it over vista when i don't need to get any programs installed.

I know there's a thousand guides, but the problem is that none of them work for me for two reasons:
-i don't have the permission to change the /etc/default/grub file ('sudo su' command doesnt help anything)
-menu.lst does not exist


ps.
i have less than 24hours of experience with linux so please speak in non-linux-nerd-english :D

---

### Post by dcstar on 2010-02-21
> **Tsun said:**
> I love everything in ubuntu...
...except the fact that installing something which would take 5 seconds in windows takes 15minutes in ubuntu. Assuming i get it installed at all.

Anyway, i want to change it so that the GRUB opens Vista by default.
I don't want to uninstall ubuntu because i still prefer it over vista when i don't need to get any programs installed.

I know there's a thousand guides, but the problem is that none of them work for me for two reasons:
-i don't have the permission to change the /etc/default/grub file ('sudo su' command doesnt help anything)
-menu.lst does not exist


Firstly if things are taking along time to install you should ask for help with that problem, not just live with it.

Secondly you are using Grub2, so Grub information is useless to you. Search for the many Grub2 posts.

---

### Post by Tsun on 2010-02-22
Knowing the grub version does not help me to edit the /etc/default/grub fle :S
I just don't have the persmission to edit it and i cant find the answer why.
That's why i made this topic.

Similar problem with installing things. I cannot do what guides tell me for a similar reasons so i get sick of it. I don't want to make a topic for every install and wait for the answer, especially when i don't see any good reason why there is no installer/.exe type of solutions for linux.

ps. My grub is 1.97 beta or something like that as far as i can remember.

---

### Post by r_s on 2010-02-22
If you cannot run sudo, then there is some problem, without it you cannot do what you are looking for.
You will not be able to edit and change any file if you don't have the required permissions.
Secondly, There is always an installer present for installing applications in linux , its just that it isn't .exe

---

### Post by Tsun on 2010-02-22
I kind of made this topic to get some help in finding out how to edit this file... :S
-I am the only user in the computer
-The sudo command seems to work fine
-I'm supposed to edit the file as root but i can't seem to figure how to do that
-When i do the "sudo su" command, my name changes to "root", but it still says i do not have the permission to use the file

Why are these installers not used then?
I mean why should i need to type 3 sentences of text in some command line when i could just click the file?



Maybe there is some really, really basic command which is so basic that it is not included in any guides?

---

### Post by r_s on 2010-02-22
open the file as sudo vi *filename* , then you will be able to edit that file and save the changes you made.

---

### Post by skitter.rusty on 2010-02-22
Ok dude. This is a simple task. Let's not make it complicated. Chill Out.

First Step. Boot up your computer. _Count the number of options you have to boot from with Grub_, including all the memtest and recovery stuff. **Then with that number, subtract 1.**

Boot Ubuntu

Then go to the terminal and type this:
```
sudo gedit /etc/default/grub
```
*Then press the enter key.*

In the window that appears find the line that says:

GRUB_DEFAULT=0

**Change the number 0 to the number that you found earlier by subtracting 1.**

Save the file, close gedit. _Do Not close the Terminal._

In the terminal then type:
```
sudo update-grub
```
*Then press the enter key.*

Reboot and see if it worked. :)

--Jono

---

### Post by louieb on 2010-02-22
Welcome to Linux and Ubuntu forums. lol - Gee it  took less than 24 hours to find out it ain't windows. Stick around and you'll get it figured out. 

The file grub.conf is read only - even for its owner (root), do it the right way - change the setup files - even if you edit grub.conf  next time grub-update is run your changes will be replace.  

Any Guide you look at make sure it is for GRUB2 - Ubuntu switch to it with the last release. Most of the guides out there are for GRUB legacy and only apply to earlier releases.  Here is a decent one [Grub 2 Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1195275") 

As for installing software - **System>Administration>Synaptic **is your friend.

---

### Post by Tsun on 2010-02-22
> **skitter.rusty said:**
> ```
sudo gedit /etc/default/grub
```
that was all i needed :D
Thanks so much.

I think i finally understand what the command means too lol.


On an unrelated note i managed to half-uninstall network manager when i tried to install a new version :S
I cant re-install because i already have it installed, but i can't use because i cant find it.
And i cant download from the application center/whatever because i dont have internet without it lol
But i dont need to fix that really.

---

### Post by NCLI on 2010-02-22
I would think you should fix that, though I'd recommend starting a new thread about it.

All software should, if possible, be installed from the Ubuntu Software Center or the Synaptic Package Manager. Doing it any other way is not something you'd want to do as a new user.

---

### Post by skitter.rusty on 2010-02-22
That's cool. :) But as Louieb said, it's no windows, you will find yourself often using a terminal for something that could be as simple as clicking a button under windows. Even macs have to have some things done through the terminal. And remember that .deb files are the simplest way to install things and so is the synaptic package manager. Most terminal commands will require sudo in front of them.

Btw, upgrade to Windows 7. It's great! (it will overwrite grub though I think :-/ )

---

### Post by Tsun on 2010-02-22
300€ for a new operating system i don't really need? :o
Nahhh i think i'll stick with vista and ubuntu.

I still havent quite figured how the package manager thing works :D

I'll see if i need the internet to work in ubuntu, i'll make a new thread about it then :P
But for now i'll have a "vacation" and use vista :D

---

