---
title: "Username and password help for ubuntu 9.04upgrade"
date: 2009-08-24
forum: General Help
---

### Post by 6bernese on 2009-08-24
I'm new to Linux and recently upgraded ubuntu from 8.10 to 9.04, Since upgrading i cannot get past the page requesting username/password as it says they are incorrect, I havnt changed the username/password from the default, thanks for any help.

---

### Post by P4man on 2009-08-24
there is no default username or password.. 
If you forgot yours, try this:

[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

if you also forgot you username, in that root shell type 

```
ls /home
```

---

### Post by 6bernese on 2009-08-25
After pc loads up small box saying gnome desktop manager comes up asking for username and password, hasnt come up before upgrading to 9.04 wont accept the username and password we had, definatley trying the right password, not really sure about taking your advice as we've only had linux short of a week

---

### Post by P4man on 2009-08-25
when you installed 8.10 for the first time, you probaby checked the option "log in automatically". Thats why you where never prompted for username and password. Apparently doing an upgrade, that setting is not copied over.

There really are no 10 ways to solve this. You username/password is obviously incorrect for whatever reason, so you'll have to reset the password with the link I gave you. As long as you stick to the commands written in there, its quite safe. just dont start experimenting in the root shell :)

---

### Post by 6bernese on 2009-08-25
Ok thanks alot for the help, and just to make sure to get the username I replace 
passwd <username>

with[FONT=Verdana]
[/FONT]
ls /home

[FONT=Verdana]Right?
 
And sorry if i sounded rude when i said not sure about taking your advice, just re-read it and realised
it mightve sounded that way.
[/FONT]

---

### Post by P4man on 2009-08-25
> nd just to make sure to get the username I replace
passwd <username>

with

ls /home

Right?


Not sure how you mean that. But to be clear, at the root terminal, you could optionally type ```
ls /home
``` to see your username(s). What it does actually, is just list the folders in the /home folder, and every user has a folder there with his username (unless you did something you probably wouldnt know how :) ). Im sure there are other (/better) ways to retrieve a list of users from a terminal, but that one does it for me :)

After you verified the username, indeed you proceed with typing 

```
passwd <username>
```

be aware both username AND password are case sensitive in linux! 
"John" is not the same as "john" !


> 
And sorry if i sounded rude when i said not sure about taking your advice, just re-read it and realised
it mightve sounded that way.

No worries, I didn't read it as rude. more like someone looking at a flat tire and saying: I am sure that tire is good, its brand new, so there has to be a solution other than changing it :D

---

### Post by 6bernese on 2009-08-25
After pressing esc at grub point  it arrives at a screen showing recovery mode option, is this the same as rescue mode? When I select recovery mode new screen options are:
Resume
Clean
dpkg
fsck
grub
netroot
root
fix
I tried selecting root, and root@Ubunto appeared at the bottom of the screen, but im unable to type as letters  just change root@ubuntu.
Again thanks for help.

---

### Post by P4man on 2009-08-25
you selected the right one "root" which gives you a root shell. A terminal. A command prompt, whatever you want to call it. the 

> **root@computername~#**

you see is the prompt (if you ever used DOS, it would the **C:\>** thing). You can enter those commands now. For instance if you want to clear the screen, type

```
clear
```

Or type in "ls /home". If I do that, I get:
> 
root@bob-desktop:~# ls /home
bob  ingrid
root@bob-desktop:~#

bob and ingrid are 2 user accounts on this machine.

---

### Post by 6bernese on 2009-08-25
Thanks again for reply, when i hit enter it comes up with **"root@computername~#"**. But when i type anything,  it changes **"****root@computername~#" **Into something else, no idea why, eg. when i type "s" it changes it to (arg: 3) and "l" changes it back to "root@computername~#"

---

### Post by P4man on 2009-08-25
?
aha.

Can i suggest something really silly: are you having trouble with the keyboard ? a key that is stuck or something ? cable not inserted properly ?

It would also explain why you cant log in with your username/pw that you are so certain is correct.

Can you boot a live cd, or windows, and verify the keyboard works correctly?
perhaps connect another one?

---

### Post by 6bernese on 2009-08-25
Plugged in a wired keyboard which im using to type this (On other computer) And still no good, It also works fine going though the boot menues so dont think thats the problem, Thanks for all the help though.

If i cant work it out I'll just reinstall 8.10, I'm fine with re-installing windows so im guessing its basically same with Ubuntu? Boot from disk and just follow it through?

---

### Post by P4man on 2009-08-25
if you're prepared to reinstall, you may as well troubleshoot a bit first. This is a weird problem if I've ever seen one!

When you boot a normal boot, where you are asked to enter your username, does whatever you type,  show up correctly there ? Can you type your password in the username box (so its visible) ?

---

### Post by 6bernese on 2009-08-25
Ok, I think I've found the problem, the resolution made the text in the username/password box unreadable, But the Drop down menues were just about readable ( Session, Theme, Language etc) So i presumed it was all ok. Just now I swapped to a different moniter and can now read it, and it looks like its in Arabic or something, Which is strange... Like  I said all the drop down menues are in english, I've tried changing the language to english but doesnt make any difference.

---

### Post by P4man on 2009-08-25
The language you choose is for the session, it will only change after logging in, and only if that language is actually installed. I guess you still cant log in? Is it actually a different language or not ? Not that it should matter actually.. unless your keyboard is wrongly defined as well.

Anyway, try this: at the login screen press control + alt + F1. you should get a full screen terminal now, with clear readable text (its not graphical). Spot any strange languages ? can you log in there ? Does the text you enter correspond with what you are typing?

im kinda confused as to whats going on lol.

---

### Post by 6bernese on 2009-08-25
Same problem, All the text is readable and in English, yet when i type, it types in a different language, and im sure it it a differnet language such as Arabic as on the login screen it types from right to left.

---

### Post by P4man on 2009-08-25
LOL.. I guess that explains a lot.

Ok, lets try fixing it
.
Boot from the live CD. (at the initial screen make sure to select the correct keyboard layout with F3 :D )

Once it has booted, go to "places' and then select your ubuntu harddrive in the list, so it gets mounted (eg "300GB disk"). BTW, you can open firefox and get back to this forum for reference or more help.

<snip>
Edit: crap. I tried this myself and it didnt work. let me look in to it.

---

### Post by P4man on 2009-08-25
Meh. I did some more googling, and I think what you are seeing is this bug:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=515734](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=515734)


Now it also seems GDM (the login manager) no longer uses that xorg.org file I wanted you to edit, and Im not exactly familiar with the new way. There is an example in that thread how to possible solve it.. but.

An interesting thing is that these ppl say only GDM is affected, not xdm, not consoles. So can you try logging in after pressing control alt F1 at the login window?

A word of warning if you consider doing a reinstall: its not like with windows (depending how you do it in windows)... You will lose all your apps and settings and documents.  You can make a backup of your documents at least through the livecd.

---

### Post by 6bernese on 2009-08-25
Just says log in incorrect, And I'm 100% Sure that is the right password as It was pre-set when we bought the computer and hasnt been altered. 

So do you reccomend we just re-install, I know i will lose all files etc, just meant is the install process the same with linux as i havnt installed it before as the computer came with it installed. But I'll be able to find a guide for it so should be ok.

---

### Post by P4man on 2009-08-25
Installation is pretty straightforward. Just mind the partitioning, I dont know if you intend to have dual boot with windows, or dont mind formatting the entire drive. In the latter case, its entirely easy.

If you want dual boot, if there is no free space, Ubuntu will suggest making space by shrinking existing partitions.. you want it to replace the existing ubuntu partitions, so either delete the ubuntu partitions before installing, or use the manual partitioning option and make one partition that you format as ext3 and select "/" or "root" as mount point, and one small partition for swap (or keep the existing one). Thats all really. 

And select the correct keyboard :p

---

### Post by 6bernese on 2009-08-25
Ok thanks alot for help, Should be fine with re-installation. Sending a bottle of virtual wine to you, Many thanks ;)

---

