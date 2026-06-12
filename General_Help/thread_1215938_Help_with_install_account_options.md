---
title: "Help with install account options"
date: 2009-07-17
forum: General Help
---

### Post by stalkee on 2009-07-17
Hello, new to Ubuntu and Linux, just need a little noob help with something... 

So I installed Ubuntu 9.04 on my PS3, and everything went fine except that when it was all finished and I tried to install Opera, I found that I had no admin rights and could not install anything or even access any of the administrative menu options including Synaptic, even after entering my password. After searching I found that most people say to use the su or sudo commands, but that wouldn't work either. So I just decided to use Firefox, but then I couldn't install the flash player. After a little while I couldn't get anything to work so I gave up and got rid of it. I just didn't 'get' the point of having an OS that doesn't allow the user to do anything other than use the pre-packaged programs.

Anyway, now I am going to give it another try, and I am wondering if I should just choose the root account choice when installing Ubuntu this time, and then install the programs that I want in that account and from there I would then create the regular user account and use that from then on. Would the programs like Opera still be there? 

Everyone makes it seem so scary and unsafe to use the root account, but how else could I install anything without the admin rights needed to use the sudo commands and administrative things like Synaptic? All the user guides and topics I found with the same problems say to simply sudo-this and sudo-that or to just use Synaptic dummy, but all of these things would result in error messages saying "permission denied"...:confused:

---

### Post by michy99 on 2009-07-17
There is no way to "choose" the root account when installing. The user created when installing is part of the admin group and as such has administrative powers, which includes the ability to use 'sudo' to run commands as root. If your user cannot use 'sudo', then something is wrong and needs to be fixed.

---

### Post by cariboo on 2009-07-17
Have a look at the [RootSudo]("https://help.ubuntu.com/community/RootSudo") wiki page, it will explain how things are done the **Ubuntu** way

---

### Post by sisco311 on 2009-07-17
> **michy99 said:**
> There is no way to "choose" the root account when installing. The user created when installing is part of the admin group and as such has administrative powers, which includes the ability to use 'sudo' to run commands as root. If your user cannot use 'sudo', then something is wrong and needs to be fixed.

+1

@OP: Just follow this guide and you should be fine:
[http://psubuntu.com/wiki/InstallationInstructions]("http://psubuntu.com/wiki/InstallationInstructions")


If for some reason you can't use [sudo/gksudo]("https://help.ubuntu.com/community/RootSudo") then

[list=i]
[*]
at the kboot screen type:
```
sudo -i
```
this will start a root shell.(it will NOT prompt for a password)


[*]
remount the root ("/") partition as read/write:
```
mount -o remount,rw /
```


[*]
add your user to the admin group
```
adduser username admin
```
(replace username with your log in name)

[*]
and reboot:
```
reboot
```[/list]

---

### Post by stalkee on 2009-07-17
> Have a look at the RootSudo wiki page, it will explain how things are done the Ubuntu way

I have read that before, and again it says to just use sudo, but it would give error messages saying that "this user does not have sudo rights", or something to that effect. 

It was installed on a PS3 so it is an alternate install CD. During the installation there was an option about the accounts and I picked the choice that was suggested, which had me input a name and then a user name, and a password for it, which I would enter after using a sudo command or trying to install something, and then it always brought up the same message. I guess I will try the other option this time.

..thanks Sisco, I did follow the instructions but I wasn't sure about that one option that I mentioned. I googled it at the time and found someone that said to choose the choice that I did(I believe it was a "yes"). But thanks again, I will give that a try if this happens again. Would that be secure to use once I log in again, I assume it would just give me permission to use root commands and not be logged in as root?

---

### Post by sisco311 on 2009-07-17
> **stalkee said:**
> 
..thanks Sisco, I did follow the instructions but I wasn't sure about that one option that I mentioned. I googled it at the time and found someone that said to choose the choice that I did(I believe it was a "yes"). But thanks again, I will give that a try if this happens again.

Good luck!

Oh, and welcome to the forums!

---

### Post by sisco311 on 2009-07-17
> **stalkee said:**
> I assume it would just give me permission to use root commands and not be logged in as root?

Yep, that's correct. For more info please read the wiki page posted by [cariboo907]("http://ubuntuforums.org/member.php?u=77104")

---

### Post by stalkee on 2009-07-18
> **sisco311 said:**
> Good luck!

Oh, and welcome to the forums!

Thanks,  and for taking the time to help out. 

I have just installed again and have ran into the same problem, so am about to try your solution. When I try to open Synaptic, I enter my pass and am greeted with:

"Failed to run as user root. The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator." 

I am just wondering, if this is how it is supposed to be set up at first run and everybody has to do this trick in order to install programs? Or if it was an error that I made at some point during the installation. From what I understand, I should be able to open Synaptic after entering the password, so I'm not sure what is causing this to happen. 

The only option during install that I was unsure of was the encrypting of the home directory to which I chose "yes", if that has anything to do with it? I did not change any settings at all, this is right after the install completed.

---

### Post by stalkee on 2009-07-18
> **sisco311 said:**
> +1

@OP: Just follow this guide and you should be fine:
[http://psubuntu.com/wiki/InstallationInstructions](http://psubuntu.com/wiki/InstallationInstructions)


If for some reason you can't use [sudo/gksudo]("https://help.ubuntu.com/community/RootSudo") then

[LIST=i]
[*]
at the kboot screen type:
```
sudo -i
```this will start a root shell.(it will NOT prompt for a password)
[*]
remount the root ("/") partition as read/write:
```
mount -o remount,rw /
```
[*]
add your user to the admin group
```
adduser username admin
```(replace username with your log in name)
[*]
and reboot:
```
reboot
```
[/LIST]


Ok I tried this and it seemed to be working until I got to the reboot part, when I tried the reboot code it said "connection denied" or something, so I had to reset the system but when I logged in again it is still the same.

---

### Post by sisco311 on 2009-07-18
> **stalkee said:**
> Thanks,  and for taking the time to help out. 

I have just installed again and have ran into the same problem, so am about to try your solution. When I try to open Synaptic, I enter my pass and am greeted with:

"Failed to run as user root. The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator." 

I am just wondering, if this is how it is supposed to be set up at first run and everybody has to do this trick in order to install programs? Or if it was an error that I made at some point during the installation. From what I understand, I should be able to open Synaptic after entering the password, so I'm not sure what is causing this to happen. 

The only option during install that I was unsure of was the encrypting of the home directory to which I chose "yes", if that has anything to do with it? I did not change any settings at all, this is right after the install completed.

Which version did you installed? 8.04(Hardy), 8.10(Intrepid) or 9.04(Jaunty)?

After a quick google search i found this BUGs:
[https://bugs.launchpad.net/ubuntu/+source/user-setup/+bug/158952]("https://bugs.launchpad.net/ubuntu/+source/user-setup/+bug/158952")  
[https://bugs.launchpad.net/ubuntu/+source/user-setup/+bug/321430]("https://bugs.launchpad.net/ubuntu/+source/user-setup/+bug/321430")

In order to gain admin rights you will have to follow my instruction and after step iii.) edit the sudoers file and make sure it looks like this:
```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL
**%admin ALL=(ALL) ALL**
```

you will have to add the **bold** line (if it's missing).

to edit the file type:
```
EDITOR=nano sudo -E visudo
```
to save the file and exit press Ctrl+x, y, Enter.

Here is more detailed guide: [http://www.psychocats.net/ubuntu/fixsudo]("http://www.psychocats.net/ubuntu/fixsudo")

Of course, instead of booting in Recovery Mode(as suggested in the guide), you need to type *sudo -i* at the kboot screen and remount the root partition as read/write(step i.) and ii.)).

HTH.

---

### Post by sisco311 on 2009-07-18
> **stalkee said:**
> Ok I tried this and it seemed to be working until I got to the reboot part, when I tried the reboot code it said "connection denied" or something, so I had to reset the system but when I logged in again it is still the same.

Instead of a hard reboot try to log out (Ctrl+d) or a soft reboot(Ctrl+Alt+DEL).

EDIT: i think i know why you get the "connection denied" error. try to set the hostname before rebooting:

```
hostname **type-the-hostname-here**
``` 
if you don't remember the hostname you set during installation, then the:
```
cat /etc/hostname
```
command should print it.

---

### Post by stalkee on 2009-07-18
Ok I tried the first instructions again and it said "this user is already an admin" and then pressed ctrl-d to log out, then enter to start ubuntu. But again when I logged back in, same error message. After that popped up something I haven't seen before, a box that says software updates are available, I tried this thinking it could be the problem but again, it won't let me install them, same error message. It is version 9.04 Jaunty Jackalope. 

When I try the command id <user>I get:

uid=1000(user) gid=1000(user) groups=1000(user),118(admin)

---

### Post by sisco311 on 2009-07-18
Did you try to edit the sudoers file? (post #10)

---

### Post by stalkee on 2009-07-18
> **sisco311 said:**
> Did you try to edit the sudoers file? (post #10)

No not yet, I will try it now. Thanks for the help and fast replies!

---

### Post by stalkee on 2009-07-18
Ok I have edited the file and no more error messages! I can open Synaptic and am now downloading all the software updates. 


Thanks very much for your help, it is much appreciated!

---

### Post by sisco311 on 2009-07-18
> **stalkee said:**
> Ok I have edited the file and no more error messages! I can open Synaptic and am now downloading all the software updates. 

Cool!

> **stalkee said:**
> 
Thanks very much for your help, it is much appreciated!

You're welcome!

---

### Post by 3rdalbum on 2009-07-18
I think I might be able to shed some light on the reason why you had this problem; it's amazing but I was first stung by the problem back in Ubuntu 5.10!

The key: You used the alternate CD. And I bet you chose the "Advanced" option, or whatever it's called (been years since I've used the Alternate CD). If you start the alternate CD installer as "Advanced" mode, then it will prompt you to set a root password, and your main account will not have sudoer privileges. And, as usual, Ubuntu doesn't let you log in as root at the login screen.

It's very unusual for Ubuntu users to install with the Alternate CD *and* choose to start the installer in Advanced mode *and* not realise that something's wrong when asked to set a root password *and* not be able to recognise and fix the problem with visudo.

I'm glad you successfully edited the sudoers file; I was a newbie who had never used Vim and didn't know how to get it to use Nano as the editor for the sudoers file. I just reinstalled Ubuntu, but using the normal beginner mode.

---

