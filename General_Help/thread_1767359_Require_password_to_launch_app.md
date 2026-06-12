---
title: "Require password to launch app"
date: 2011-05-25
forum: General Help
---

### Post by .psd on 2011-05-25
I installed a Rednotebook 1.1.6. Naturally it's personal, but for some reason after years in development it lacks password protection. I intend to launch it from the Unity dock.

How can I restrict access to rednotebook (specifically, the rednotebook.desktop file) via a simple password prompt?

---

### Post by .psd on 2011-05-25
Would this work?

Write 2 scripts, A, and B.

Script A tells the system not to allow rednotebook.desktop to open unless script B opens it. Script B prompts for a password and doesn't open rednotebook.desktop unless the answer is correct.

Then add script B to the launcher with rednotebook's icon.

Or else, is there a native method in ubuntu, or else a third party program that integrates with Ubuntu, which will let me password lock specific files or locations?

Looking for a password requirement a la .rar files, without having to compress, decompress, encrypt and decrypt every time.

---

### Post by LordNeo on 2011-05-25
in the launcher set your program to "gksudo PROGRAMNAMEHERE" then you will be asked to promt root password to open the program.

Also the data will be stored under root privileges, so others will not have access to it

---

### Post by .psd on 2011-05-25
> **LordNeo said:**
> in the launcher set your program to "gksudo PROGRAMNAMEHERE" then you will be asked to promt root password to open the program.

Also the data will be stored under root privileges, so others will not have access to it
Jackpot. Except:

1. Rednotebook.desktop can still be access without a password simply by avoiding the dock launcher.
2. Thus I need to lock the actual .desktop file, not the dock launcher.
3. How do I find/set the root password?

---

### Post by LordNeo on 2011-05-25
Open Rednotebook.desktop with gedit, then edit the command to use gksudo. (BTW .desktop = launcher)
Then remove the launcher from the panel and re-add the .desktop file.
If you need further security, you can change the owner of the file and only give execution access.

---

### Post by .psd on 2011-05-25
I thought I could give rednotebook.desktop no permissions except to root, then I could add it to the launcher, and use the root password (whatever that is) whenever i want to launch it. Perfect, except it's not possible.

Even with nautilus open as root, the dock won't accept rednotebook.

EDIT: LordNeo, trying your newest advice right now.

---

### Post by .psd on 2011-05-25
OMG IT WORKS!! EXCEPT (lol......):

It asks for *my* password, *not* root's. That doesn't work because everyone knows my password, that's the whole point. If it was my choice, I wouldn't even have a login password, and would just use root's whenever a prompt required one. Then only I would know the password because nobody would ever have to log in. This way my wife and I can do everything on one account.

How can I make it ask for roots password instead, or even better, define my own password?

---

### Post by LordNeo on 2011-05-25
Wow & LOL, i never tought it would matter to ask for your password...
By basic setting, if anyone knows your password, then anyone can use sudo and undo everything you have done right now (and therefore can access rednotebook as root).

I'm not really familiar with this, but you could define the root password using "sudo passwd root" but that will also enable the login as root, then you could remove yourself as sudoer and then you will be asked for root password everytime you need to change something (and you will be unable to use sudo with your own password).
All the above if far more complicated than you would posibly want...

Maybe just do a bash script that prompt for a custom password, that would be easier to do, but i'm lacking of time to get it done right now.

Good luck, i will try to come back when i get home to see if i can be more help


EDIT2:
Best option is to change your own password and then set the "autologin" feature, so noone will need to know your password to use the computer, the password will only be needed for administrative task (or restricted programs)

---

### Post by .psd on 2011-05-25
> **LordNeo said:**
> Wow & LOL, i never tought it would matter to ask for your password...
By basic setting, if anyone knows your password, then anyone can use sudo and undo everything you have done right now (and therefore can access rednotebook as root).

I'm not really familiar with this, but you could define the root password using "sudo passwd root" but that will also enable the login as root, then you could remove yourself as sudoer and then you will be asked for root password everytime you need to change something (and you will be unable to use sudo with your own password).
All the above if far more complicated than you would posibly want...

Maybe just do a bash script that prompt for a custom password, that would be easier to do, but i'm lacking of time to get it done right now.

Good luck, i will try to come back when i get home to see if i can be more help
That sounds like a way to do what I'd like. How, then, do I change root's password and remove myself as a sudoer? And how, then, can I set my account to auto-login without prompting for a password EVER (even after monitor timeouts etc etc)?

EDIT: your EDIT2 answer above will definitely work for now, and seems more secure for whatever that's worth given my situation. I'm gonna see if I can figure out how to change my password and set auto login. Does auto login eliminate ALL login prompts, for example the one after screen timeouts?

---

### Post by .psd on 2011-05-25
hurrrrrpp duuurrpppppp UBUNTU!!!!!!!

I changed my password, set auto-login and restart. It "logged me in" automatically then it asked for my keyring password, which was still my old password....... PLUS, the launcher doesn't ask for a password any more either. :( ubuntu fail.

I hope this isn't why n00bs give up. There has to be SOME simple way to password protect a file / location! It's 2011 guys, this question has been being asked for years, google it!

---

### Post by LordNeo on 2011-05-25
That's a know issue while using Wireless networks (the keyring stuff).
Just open the dash, then write "keyring" and you will find the application for it.
Right click on the Storage (a group of passwords) and select "change password".
Put your old password and then just let empty the other 2 spaces.
It will ask you if you want to use the "unsecure deposit", ok to that.
Check in the list if there is an entry for "Rednotebook" and delete it.

Reboot, check if it ask you for the password (it shouldn't) then wait a minute and check trying to open Rednotebook, it should ask for your password.

Best regards,

PD: If you need to contact me, i'm in irc.ubuntu.com, nick "LordNeo"

PD2: I just tought another way, first, create a new user, without "sudo" ability, then go to terminal, type "su USERNAME" and you will be logged as that user, then do "nautilus" browse to your application and change the rights so only that user owns the file, only that user can execute the file (i think is something like chmod 474 or something like that), then change your launcher to "gksu -u USERNAME PROGRAMHERE" on each execution it should prompt for the new user password.

---

