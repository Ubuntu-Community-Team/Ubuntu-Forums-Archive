---
title: "User administrative password doesnt work"
date: 2010-06-23
forum: General Help
---

### Post by bakhona on 2010-06-23
Hi guys.

Im using an Mecer Expression PL5C laptop originally installed with Windows Vista Basic.

I've recently installed ubuntu 9.0.4 two months ago and its been running fine. 

Created a system/administrator password that I've been using to both log on to the system
 and perform administrative duties such as install software etc.
 
 
Last week after a long while I tried to install something on my laptop, as usual, but this time my password was denied.
I find it odd because I can log in and out of the system fine, its only when I have to perform administrative duties that the password doesn't work.

I cant:

-Install software (eg. Synaptic Package Manager) or reset my password, my user password is denied.
-Run sudo commands in the terminal, the password is denied.

I tried:

-To reset the password via the user account properties in the user groups.
-Booting the with recovery mode and using the root shell prompt to change the password. (It still denies the password)


Please help.

Bakhona

---

### Post by oneafrikan on 2010-06-23
This is weird - surely the password that you access your machine with will allow you to use sudo (with a vanilla install)?

Have you checked whether there are any other passwords in your keychain?

---

### Post by bakhona on 2010-06-23
Hi Gareth 

Yes I ran a tail etc/password. It showed that I only had one password/account.

It is rather weird, I was under the impression my administraive password should be the same as the one I use to log into the system.

Is there any other solutions to this problems besides re-installing Ubuntu?

---

### Post by dozdozez on 2010-06-23
look in /etc/sudoers file
there can be several options to configure the sudo behaviour (man sudoers)
in particular, the tags rootpw, targetpw or runaspw

---

### Post by bakhona on 2010-06-24
I cant access the sudoers file. I dont have access to that file because I dont have permissions. Is there no other solution that doesnt require administrative priviliiges?

---

### Post by Drenriza on 2010-06-24
how exactly are you trying to access the root user

by
```
sudo
```
or
```
su - root
```
???

---

### Post by bakhona on 2010-06-24
I've tried both sudo and su - root. Both permission is denied. Its weird because I can log onto my system, I've always thought its the same password.

---

### Post by Drenriza on 2010-06-24
if you want to use the 
```
su - root
```
command, you need to active the root user.

```
sudo passwd root
```

make a password, and then you can use 
```
su - root
```

---

### Post by bakhona on 2010-06-24
I've tried that thanx. The problem I have is that it rejectcs my password. It asks for my system password,  then when I puch it in it says its incorrect. The questions is, how can I use the same password to log onto my system, but when I have to perform admin funtions, it rejects it?

Unless there's a seperate password for admin stuff that I missed. But I ran tail /etc/passwd it came up with only one password/account.

Not quite sure whats going on, or maybe I missed something.

---

### Post by Rubi1200 on 2010-06-24
I apologize if this seems obvious, but I assume you checked to make sure you are a member of the admin group?

```
groups
```> From the man page su(1):
If group 0 (normally ``wheel'') has users listed then only those users
can su to ``root''. It is not sufficient to change a user's /etc/passwd
entry to add them to the ``wheel'' group; they must explicitly be listed
in /etc/group. If no one is in the ``wheel'' group, it is ignored, and
anyone who knows the root password is permitted to su to ``root''.

---

### Post by bakhona on 2010-06-25
Thanx Rubi. I seem to be on the list as part of the asdmin group.

---

### Post by thelugnut on 2010-06-25
I'm going to throw this out there. if it seems to silly or simple, my apologies.
About a month ago I had the same problem. My password was consistently refused. Eventually I found that I had inadvertently pressed "Numlk" key. Since I am using a laptop, this changed the right-side area of the  keyboard  and my password used characters from that section.
A shot in the dark, but there you have it.

---

### Post by stoneage on 2010-06-25
Is it possible the keyboard layout changes after logging in? Several keys are different between eg. a US and a UK layout. If you type your password into a terminal does it look correct?

---

### Post by Drenriza on 2010-06-25
> **stoneage said:**
> Is it possible the keyboard layout changes after logging in? Several keys are different between eg. a US and a UK layout. If you type your password into a terminal does it look correct?

thats a valid question.

typing without, numlock activated.

ty-5ng w5th, n4036c2 act5vated

---

### Post by bakhona on 2010-06-25
Thanx guys. Numlock wasnt the problem. Im starting to lose hope. I have alot of development work on my machine that I dont wanna lose. It would bummer if I had to re-install.

---

### Post by Drenriza on 2010-06-28
cant you just reset the password if you have physical access to the machine?

EDIT:
> If your memory or mistyping leaves you without the right password to get into an account on a Linux computer, there&#8217;s no need to reformat. You&#8217;ll just need to reboot into single user mode to reset it. Here&#8217;s how to do it on a typical Ubuntu machine with the GRUB bootloader:

Reboot the machine.
Press the ESC key while GRUB is loading to enter the menu.
If there is a &#8216;recovery mode&#8217; option, select it and press &#8216;b&#8217; to boot into single user mode.
Otherwise, the default boot configuration should be selected. Press &#8216;e&#8217; to edit it.
Highlight the line that begins with &#8216;kernel&#8217;. Press &#8216;e&#8217; again to edit this line.
At the end of the line, add an additional parameter: &#8216;single&#8217;. Hit return to make the change and press &#8216;b&#8217; to boot.
Change the admin password
The system should load into single user mode and you&#8217;ll be left at the command line automatically logged in as root. Type &#8216;passwd&#8217; to change the root password or &#8216;passwd someuser&#8217; to change the password for your &#8220;someuser&#8221; admin account.

Reboot

Once your done, give the three finger salute, or enter &#8216;reboot&#8217; to restart into your machine&#8217;s normal configuration.

That&#8217;s all there is to it. Now just make sure to write your password down on a post-it and shove it somewhere safe like under your keyboard.
[http://burnz.wordpress.com/2008/09/09/how-to-reset-ubuntu-root-password/](http://burnz.wordpress.com/2008/09/09/how-to-reset-ubuntu-root-password/)

---

### Post by Drenriza on 2010-07-05
solved ??? or

---

### Post by bakhona on 2010-07-06
Hey Drenriza....

I succesfully changed my password. Which means it worked. But its still the same.

It seems like it works for the password I use to log in.  But My sudo and synaptic still rejects the new password.

I get the error "Failed to run usr/sbin/synaptic as user root" Wrong password

Do u think my sudoers files could be corrupted?

This is what I get when I run the command "Groups" in the terminals: 

bakhona adm dialout cdrom plugdev lpadmin admin sambashare

So I can see that Im part of both the adm and admin group.

Please help..

Thanx for the reply....

---

### Post by Rubi1200 on 2010-07-06
Take a look here, but be careful if/when you make changes!

[http://ubuntuforums.org/showthread.php?t=1132821](http://ubuntuforums.org/showthread.php?t=1132821)

Don't forget to use "visudo" to open and make any changes too.

Please also read the pages that ibuclaw links to there.

Hope this helps.

---

### Post by lordskid on 2010-07-06
do you have a root password?
did you try to login as root?

---

