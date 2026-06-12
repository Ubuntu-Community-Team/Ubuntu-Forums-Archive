---
title: "Forced Password (How to remove it)"
date: 2009-12-15
forum: General Help
---

### Post by ic2 on 2009-12-15
[SIZE=5]Hello Everybody,[/SIZE]
 
[SIZE=5]I'm here to learn the working of Linux and other operating systems and to get away from Windows for a while. I have 3 primary partitions and a extended partition from D though T. Two primary are reserve for future use. (NetBSD and Ubuntu Server Edition.)[/SIZE]
 
[SIZE=5]Window-7 is on first primary. I install Ubuntu Desktop on T: but it force me to enter a PASSWORD doing installation. I did not want to enter no password but it would not install with-out it. Why would the developer of Ubuntu do such a thing and what would I have to do to eliminate this feature on my next install because I plan to try again for the 3rd time?[/SIZE]
 
[SIZE=5]Now this is strange. It seem like Ubuntu is doing the same thing like Windows-7, telling me "You are not Allow" ... I am not allow to open up my own darn Document Folders or whatever.[/SIZE]
 
[SIZE=5]Anyway, when I boot to Ubuntu and try to open any of my filesystem (partition) I get the "Authentication is required to mount the device" ... I type in my password and I get "Authentication Failure". I close the dialog box and I get another message "Unable to mount 25 GB Filesystem" Not Authorized.[/SIZE]
 
[SIZE=5]Than when I try to open up certain files and folders like lost+found i get "The folder contents could not be displayed." You don't have permissions necessary to view the contents of bla-bla-bla". Now I'm wondering, *Who do*? [/SIZE]
 
[SIZE=5]How do I by-pass all of this and get rid of password?  If I want to add a password, I will, but right now, I don't need it.[/SIZE]
 
 
[SIZE=5]Thanks in advance for any help[/SIZE]

---

### Post by 3rdalbum on 2009-12-15
One of the reasons why Windows is so insecure is that it makes it easy for users to run their systems without any security at all.

Also, there's a seperation between user and root, that you don't seem to be aware of. Your ordinary user account cannot perform systemwide tasks or modify files outside your home directory; instead you need to use the "sudo" or "gksudo" commands to elevate to root, which is the administrator.

This page explains more:  [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

If Ubuntu is not allowing you to access your document folders, then you've got big problems. This shouldn't happen ever, unless you've done something ill-considered to your file system. If you're trying to modify something that's not in your home directory and not in /media, then this is part of the Ubuntu security system; you need to run the command or run a file browser as root.

---

### Post by scouser73 on 2009-12-15
View this site for the security on Ubuntu: [[COLOR="Red"]**Security On Ubuntu**[/COLOR]]("http://www.psychocats.net/ubuntu/security")

---

### Post by ic2 on 2009-12-15
[SIZE=5]Thanks ***3rdalbum***,
I’ll be looking into this right now. But I don’t think any OS (especially Linux)should force you to enter a password just to install software because anyone trying to get into Linux will know to choose that option once he or she is ready, so Ubuntu should fix that and give the user the options to do so or not. Thanks again, now I got a clue.
 
Thanks ***scouser73***,
All of this should keep me busy for a minute :)
[/SIZE]

---

### Post by Grenage on 2009-12-15
> But I don’t think any OS (especially Linux)should force you to enter a password just to install software

That's exactly how it should be (note how Windows has come around to this way of thinking).

P.S: I will pay you many pies if you reduce your font.  I have to stand 10 metres away from the monitor to take it in. ;)

---

### Post by noway2 on 2009-12-15
You REALLY should read this document: [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm), which will put a lot of the linux / ubuntu nuances in perspective for you.

---

### Post by t.rei on 2009-12-15
As I am currently writing my Diplomarbeit on the Secuity Mechanisms and why they are not accepted as such I encountered the "I don't want to have to type in passwords" statement in almost every single Interview I have done. 

This is a problem to all forms of IT Security. I understand. And I am sad to not be able to provide a sensible solution. If you would like to elaborate on your dismay of a single password that you might have to input several times to increase security of you computer - and thus on the long run of everyone else in the net, by making it ALOT harder for malware, viruses, trojans, botnets - I would be really interested.

On the other hand, maybe you 'come around' once you have found a good password.

Some hints on choosing good passwords:
1) Easy to type - sounds weird as number one - but remember, you might have to type it several times. Breaking your fingers doing so is... a HUGHE drawback
2) Good length - 4 letters are short - 10 probably too much... choose something you are comfortable with
3) Charakter selection and safety. Now I know that 'good passwords' are:
- No word from the dictionary
- nothing as weird as "password" "my.username" "secret" "auth" or the like
- not just leetspeak
- no birthdays
- special charakters
- the longer the better
...
truth is: simply having a password at all gives the most "bang for the buck".  So pick a password. ANY password. It gives YOU that much more safety and will keep your system clean and alive alot longer, even if its "abcDEF123()" - actually even if its "abc" it will still be VASTLY superior to no authentication requirement.

Have fun with your system. 

------------------

As for the authentication failure: that sounds like Password wrong (caps lock active? Case Sensitive?)

---

### Post by 3rdalbum on 2009-12-15
> **ic2 said:**
> But I don&#8217;t think any OS (especially Linux)should force you to enter a password just to install software because anyone trying to get into Linux will know to choose that option once he or she is ready, so Ubuntu should fix that and give the user the options to do so or not. Thanks again, now I got a clue.

If you give the user the option to run insecurely, then many users will do so - to everybody's detriment. This is what Microsoft discovered with Windows XP - they let the user login every single day into an administrator account rather than into a limited user account, and as a result it became really really easy to root a Windows XP box. It's difficult to root Windows XP when the user runs as a limited user account*, but almost nobody runs this way.

That's why Microsoft enforced "limited user by default" and that's why modern Linux systems insist on this too; and insist on a password.

*There's another Windows XP insecurity-by-default problem that makes this untrue. If you run every day as a limited user account, and your administrator account password is blank, any virus or attacker can easily root the system.

---

### Post by ic2 on 2009-12-15
[SIZE=3]"The superuser can do anything and everything, and thus doing daily work as the superuser can be dangerous. *[COLOR=red]You could type a command incorrectly and destroy the system[/COLOR]*."[/SIZE]
 
[SIZE=3]I take back what I said about PASSWORD. This is my very first real lesson about Linux. It should be there by default but I still need to know how to manually turn it off from time to time. If that is not possible than it should not be there.[/SIZE]
 
[SIZE=3]Back to those great links.[/SIZE]
[SIZE=3][/SIZE] 
[SIZE=3]Thanks a lot guys[/SIZE]
[SIZE=3][/SIZE] 
[SIZE=3]PS: Grenage, Apple will do just fine :)[/SIZE]

---

### Post by ic2 on 2009-12-25
Same problem from day1 but even worse ...

[http://ubuntuforums.org/showthread.php?p=8559751#post8559751](http://ubuntuforums.org/showthread.php?p=8559751#post8559751)

---

