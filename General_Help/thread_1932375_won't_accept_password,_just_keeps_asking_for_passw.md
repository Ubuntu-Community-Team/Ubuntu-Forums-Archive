---
title: "won't accept password, just keeps asking for password"
date: 2012-02-27
forum: General Help
---

### Post by goodbye-windows(tm) on 2012-02-27
Hi All. 

Once again, I have a technical problem and I hope someone in the ubuntu community can point me in the right direction...........

This morning, I turned on my system, and found it wouldn't allow me to log in. It keeps asking for my password, after the password is typed in, it just reverts back to an empty password dialog box and asks me for the password again. Nothing I can type in helps. I thought of a password reset, but my home folder is encrypted-so I don't think password reset will help me.

I have no idea what might have happened.

This morning it did reset itself without warning during the initial boot up.....and, yesterday I used windows to repair a usb memory stick that wouldn't allow deleting of trash. Plugging the memory module into the windows machine allowed windows to delete the trash and after the same module was plugged into my xubuntu system, it worked normally. I have no idea what windows might have done or if the two problems are related.

I can log into the guest account, but not my password protected primary administrators account.

My system is an old MSI motherboard I put together years ago. It has a 3.2 GHz P4 processor, 1.5 GB of ram and a new-ish 250 GB hard drive. It runs xubuntu (11.10) well. The home folder is encrypted. I have other user accounts on the system, but they are almost completely unused and could be deleted if necessary. The drive has linux only, no windows.

Any suggestions?

TIA.

Art

---

### Post by Gremlinzzz on 2012-02-27
Works with Ubuntu no reason not to work with Xubuntu :popcorn:

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by mbuell on 2012-02-27
> **goodbye-windows(tm) said:**
> Hi All. 

- - -
I can log into the guest account, but not my password protected primary administrators account.

My system is an old  . . .

Art

You are probably already past this - but jic - hardware? Caps lock off? Perhaps a stuck key on the keyboard? Log in to the guest account and make sure when you type your admin pw in gedit it types ok. 

This is tickling something else in my memory - but it doesn't come to the front at the moment. Good luck!

---

### Post by goodbye-windows(tm) on 2012-02-27
Hi All,

I did read the replies, but I'm very concerned..........

I found a web reference and a post on this forum that indicate my encrypted home folder will be gone if I try to reset the password, see links:

[http://ubuntuforums.org/showthread.php?t=1787218](http://ubuntuforums.org/showthread.php?t=1787218)

and 

[http://forums.linuxmint.com/viewtopic.php?f=42&t=84256](http://forums.linuxmint.com/viewtopic.php?f=42&t=84256)

------------------------------------------

I also discovered that I can use the guest account to install software via the software center if I use my administrators password. So, why can't I use the same password to login to my administrators account????

In other words, when I login to my administrators account, I use xxx  for the password. The same password is needed when I do a sudo command in the terminal. 

Is it possible that my password has already been reset (covertly) by someone with physical access to my computer....which is why I can't log in now??

Regards,

Art

---

### Post by mbuell on 2012-03-10
> I also discovered that I can use the guest account to install software via the software center if I use my administrators password. So, why can't I use the same password to login to my administrators account????

In other words, when I login to my administrators account, I use xxx for the password. The same password is needed when I do a sudo command in the terminal.

Is it possible that my password has already been reset (covertly) by someone with physical access to my computer....which is why I can't log in now??

If it works with sudo, I don't see how it could have been reset for the gnome login. I don't think you can have two different pw for the two uses. 

If you can login as guest - or with a live-cd - or some other way - can you get the home drive unencrypted? I would unencrypt it if possible - back it up somewhere for now, and go back to the pw reset direction.

---

### Post by sroske on 2012-06-07
I have the same problem. i can login to my son's account that has no password. I can even launch synaptic and do an update using my superuser's password. i can't understand this. i am so disappointed with this expression of instability. :(

---

### Post by steeldriver on 2012-06-07
hi sroske, same symptoms don't necessarily mean the same problem - in your case since your password works in sudo it's possible that something just got corrupted in your X session startup

you can either use another account and then open a terminal or login at one of the virtual terminals (Ctrl-Alt-F1 / Ctrl-Alt-F2 etc.) and type

```
sudo ls -l /home/yourusername/.*authority
```and make sure both files are owned/writable by you (not root) - it's often easier to simply delete them rather than chmod/chown them i.e.

```
sudo rm  /home/yourusername/.Xauthority
```let us know how it goes

---

### Post by sroske on 2012-06-07
> **steeldriver said:**
> hi sroske, same symptoms don't necessarily mean the same problem - in your case since your password works in sudo it's possible that something just got corrupted in your X session startup

you can either use another account and then open a terminal or login at one of the virtual terminals (Ctrl-Alt-F1 / Ctrl-Alt-F2 etc.) and type

```
sudo ls -l /home/yourusername/.*authority
```and make sure both files are owned/writable by you (not root) - it's often easier to simply delete them rather than chmod/chown them i.e.

```
sudo rm  /home/yourusername/.Xauthority
```let us know how it goes

thanks for helping!

i tried this using ctrl-alt-F1 and am able to login to my admin account. i have RW priviledges just fine and rm the directory.

nothing happens. i ctrl-alt-F7 back in and logout to try to login to my admin account. it usually just hangs for a minute then the login screen appears with only GUEST and OTHER available. i can login to GUEST. the .Xauthority for my admin is still gone.

it simply appears there again when i reboot. when i try to login to my admin account it asks me for the PW again, then on second reentry the computer hangs at the default wallpaper

the OS is currently fully updated. no new software was installed at last successful login yesterday. the only thing that might be strange was i was attempting to wake the PC from suspend. there had been no previous problems with this. although hibernation remains broken.

EDIT!!

SUCCESS!! Thanks for your tip. I checked one more time this morning and found 2 files in .authority. After reviewing the .sessions.xfce-errors (or whatever)I noticed there were errors in the XFCEauthority file as well. I deleted them both, since both were at zero bits.

This allowed me to login to my admin account. thanks again. i wonder what caused the glitch in the first place?

---

