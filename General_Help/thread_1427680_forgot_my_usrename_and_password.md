---
title: "forgot my usrename and password"
date: 2010-03-11
forum: General Help
---

### Post by mistert88 on 2010-03-11
forgot my usrename and password to get in what can I do

---

### Post by wojox on 2010-03-11
Try this: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by mistert88 on 2010-03-11
thanks wojax but that gives me an error that i need to load the kernel first.
Press any key to continue...._  which takes me back to the recovery mode box

---

### Post by satish_j on 2010-03-12
thanks wojax for that useful link..
But,i suppose this is only for Normal users and not for resetting root account??
pls confirm..

---

### Post by coffeecat on 2010-03-12
> **mistert88 said:**
> thanks wojax but that gives me an error that i need to load the kernel first.
Press any key to continue...._  which takes me back to the recovery mode box

How did you try to get into recovery mode? From the second choice in the grub menu? Because if you did that sounds as though something is wrong with the grub menu code for the recovery stanza. If that's what you're getting from the grub menu, post the exact error and we'll take it from there. But for the record this is what you need to do for both username and password recovery.

Boot into recovery mode. The Recovery Menu is a little different in Karmic from that shown in the link that wojox posted. You need "drop to root shell prompt", which is now the last choice in the menu. When you get to the # prompt, type:

```
ls /home
```That will give you your username. If you created more than one account, it will list them all. Now, to reset the password, simply follow the instructions in that link using the username you've recovered from the ls command.

> **satish_j said:**
> thanks wojax for that useful link..
But,i suppose this is only for Normal users and not for resetting root account??
pls confirm..

You are strongly advised not to reset or change the root account. That would subvert the Ubuntu security model. You do not need a root password. For more, read:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by satish_j on 2010-03-12
> **coffeecat said:**
> 
You are strongly advised not to reset or change the root account. That would subvert the Ubuntu security model. You do not need a root password. For more, read:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
But what if there is only one user account(one that was created at time of installation).Pwd for such account and root pwd are same.If i change the pwd of such account,then root account pwd is also changed or what??/

---

### Post by sisco311 on 2010-03-12
> **satish_j said:**
> But what if there is only one user account(one that was created at time of installation).Pwd for such account and root pwd are same.If i change the pwd of such account,then root account pwd is also changed or what??/

Nope, in Ubuntu, by default, the root account password is locked. 

sudo, gksu and policykit allows admin users to escalate privileges by authenticating themselves with their user passwords.

---

### Post by coffeecat on 2010-03-12
> **satish_j said:**
> Pwd for such account and root pwd are same.

Not so. There is a (randomly set) root password but, as sisco311 has pointed out, it is locked. And you don't need it - ever. I strongly urge you to read the link I posted. It is clearly written and gives a useful account of the Ubuntu security model.

---

### Post by satish_j on 2010-03-12
> **coffeecat said:**
> Not so. There is a (randomly set) root password but, as sisco311 has pointed out, it is locked. And you don't need it - ever. I strongly urge you to read the link I posted. It is clearly written and gives a useful account of the Ubuntu security model.
Thanks cofeecat for that link...till now,i was under assumption that the pwd we type after entering 'sudo' is root acc pwd.
Now,One query that arises out of this is:
Is 'sudo' applicable for specific type of users?The link answers this as 'Authorized users'.Does a user created with 'useradd' command and through GUI method of Add user becomes a 'Authorized user' by default??
And,is there any way to retrieve the actual root acc pwd??

---

### Post by coffeecat on 2010-03-12
> **satish_j said:**
> Is 'sudo' applicable for specific type of users?The link answers this as 'Authorized users'.Does a user created with 'useradd' command and through GUI method of Add user becomes a 'Authorized user' by default??

No - using the GUI Users and Groups utility you have to tick the "Administer the system" box in the "User privileges" tab. The default is to give admin privileges to the first created user, but not to subsequently created ones, unless the admin user gives them elevated privileges. It's virtually identical to the model used in MacOS, even down to being able to use sudo in the MacOS terminal. Which makes me feel very much at home when I switch between Ubuntu and MacOS. :)

> **satish_j said:**
>  And,is there any way to retrieve the actual root acc pwd??

First thing to say, of course, is that you don't need to. Second thing is that - as far as I understand it - the installer creates a root account (you have to have a root account) and then assigns a totally random password. It is irretrievable.

Just to add: If you're used to the su-to-root model of other distros such as Fedora, you need to rethink your way of working. It took me some time to get used to the Ubuntu way - I used Gentoo as my main distro for 18 months and you spend a lot of time in a root terminal in Gentoo, believe me. :wink: But now I'm used to the Ubuntu way, I have no desire or need to know the root password.

But we're getting off-topic, so I'll leave it there. The OP needs to know how to recover their username and password.

---

### Post by sdpiowa on 2010-03-12
Here's what I would do:
Backup all your files to an external hard drive using a Live Disk, then wipe the machine and start over.

---

### Post by satish_j on 2010-03-12
Yes,you are right..i should not be worried about the actual root acc pwd..Now,again slightly off-topic..dont you think the link provided by wojox is basically a security lapse.Anyone with physical access to my system can change the admin acc pwd using recovery mode..
Is there any way to block this???
I have also created a separate thread on this..
[http://ubuntuforums.org/showthread.php?t=1427921](http://ubuntuforums.org/showthread.php?t=1427921)

---

### Post by sisco311 on 2010-03-12
> **mistert88 said:**
> thanks wojax but that gives me an error that i need to load the kernel first.
Press any key to continue...._  which takes me back to the recovery mode box

That's weird. 

At the grub menu highlight the (normal) Ubuntu entry,

press e for edit, remove the *ro quiet splash* kernel parameters from the linux line,

append the line with *ro single* & press Ctrl+x to boot.

If that doesn't work, try to boot with the *rw init=/bin/bash* kernel parameters. If you do so you may have to remount the root partition before you reset the password:
```
mount -o remount,rw /
```

Or you can try to boot a Live CD/USB, chroot to Ubuntu & reset your password:
[list=i]
[*]Boot the Live media & open a terminal.
[*]type:
```
sudo fdisk -l
```to list the partitions & find out the device name of the Linux/Ubuntu root partition (i.e. /dev/sda1)
[*]mount it:
```
sudo mkdir /ubuntu
sudo mount /dev/sda1 /ubuntu
```
NOTE: replace /dev/sda1 with the actual device name of the partition.
[*]mount the virtual filesystems:
```
for i in dev proc sys; do sudo mount /$i /ubuntu/$i; done
```
[*]chroot into Ubuntu:
```
sudo chroot /ubuntu
```
[*]list the home directories to find your username:
```
ls /home
```
[*]reset your password:
```
passwd username
```
NOTE: replace username with your login name.
[*]exit from the chroot:
```
exit    #or press Ctrl+d
```
[*]reboot:
```
sudo reboot
```
[/list]

---

### Post by sisco311 on 2010-03-12
> **satish_j said:**
> Yes,you are right..i should not be worried about the actual root acc pwd..Now,again slightly off-topic..dont you think the link provided by wojox is basically a security lapse.Anyone with physical access to my system can change the admin acc pwd using recovery mode..
Is there any way to block this???
I have also created a separate thread on this..
[http://ubuntuforums.org/showthread.php?t=1427921](http://ubuntuforums.org/showthread.php?t=1427921)

 
[thread=989517]Physical access is root access[/thread]

---

