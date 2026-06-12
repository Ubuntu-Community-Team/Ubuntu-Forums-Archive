---
title: "How to become admisitrator again"
date: 2011-10-23
forum: General Help
---

### Post by moorhead98 on 2011-10-23
Well I was messing around with the user accounts and I noticed that my account was listed under "administrator"
I knew that wasn't right, since I had to use Sudo to install stuff and  get root privileges, so I unlocked user accounts and set my account from  "Administrator" to "standard"
Then I changed my mind and wanted to keep "Administrator", even if I had  to use sudo. So I unlocked it again (I stupidly went to sound settings  or something, then went back), but it didn't accept my password. So now  that is messed up. I also can not install software, and probably can't  do anything else root can.
So my question is this: Is there any way to get my account back to administrator?

---

### Post by cryptotheslow on 2011-10-23
Ooops! :)

Do you have a LiveCD or USB to hand?

I think the way to sort yourself out will be to boot to a live environment and take the Try Ubuntu option, mount your installed system filesystem, then edit /etc/group and possibly /etc/sudoers by hand.

I've never done it myself so wait for someone else to confirm :D

---

### Post by haqking on 2011-10-23
> **moorhead98 said:**
> Well I was messing around with the user accounts and I noticed that my account was listed under "administrator"
I knew that wasn't right, since I had to use Sudo to install stuff and  get root privileges, so I unlocked user accounts and set my account from  "Administrator" to "standard"
Then I changed my mind and wanted to keep "Administrator", even if I had  to use sudo. So I unlocked it again (I stupidly went to sound settings  or something, then went back), but it didn't accept my password. So now  that is messed up. I also can not install software, and probably can't  do anything else root can.
So my question is this: Is there any way to get my account back to administrator?

it was right in the first place, being in the admin group does not mean you dont have to use sudo, using sudo is how it should be, and as you installed the system you are put in the admin group.

So do you still have sudo privelege ?

if so you put yourself back into the admin group

sudo adduser username groupname

if not you might need to repair sudo

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

or do it by dropping to console

[edit : wrong link, i meant drop to recovery console, you dont need to reset your password ;-)

---

### Post by nothingspecial on 2011-10-23
Reboot and select recovery mode from the grub screen.

Boot to a root shell.

Type

```
adduser your_username admin
```

Change your_username for your actual username.

Then type exit and resume normal boot.

---

### Post by moorhead98 on 2011-10-23
> **haqking said:**
> it was right in the first place, being in the admin group does not mean you dont have to use sudo, using sudo is how it should be, and as you installed the system you are put in the admin group.

So do you still have sudo privelege ?

if so you put yourself back into the admin group

sudo adduser username groupname

if not you might need to repair sudo

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

I really don't know how to explain it. Apt-get and aptitude work, but ubuntu software center does not. It seems that i can use sudo and gksudo to open programs such as nautilus, but I havent tried much else than that. 
And i could use more clarification on the "adduser" commands.
What would I put for Groupname? And (sorry to sound like a noob) what would I put for username? At the login screen and edit users screen, it says that I am "Will", but in a terminal, it doesn't say will@UbuntuLaptop, it says jcm@UbuntuLaptop (jcm was a previous username, and I think I might have made my user, Will, off of jcm). SO yeah which would I use there.

---

### Post by haqking on 2011-10-23
> **moorhead98 said:**
> I really don't know how to explain it. Apt-get and aptitude work, but ubuntu software center does not. It seems that i can use sudo and gksudo to open programs such as nautilus, but I havent tried much else than that. 
And i could use more clarification on the "adduser" commands.
What would I put for Groupname? And (sorry to sound like a noob) what would I put for username? At the login screen and edit users screen, it says that I am "Will", but in a terminal, it doesn't say will@UbuntuLaptop, it says jcm@UbuntuLaptop (jcm was a previous username, and I think I might have made my user, Will, off of jcm). SO yeah which would I use there.

answer is above from nothingspecial

```
adduser your_username admin
```

replacing the your_username with your actual login username, what do you login with ? jcm or will ?

---

### Post by zero2xiii on 2011-10-23
An easy answer:

Go to terminal (while loged into your system the normal way) and type:

```
whoami
```

Reboot now and during grub select the recovery mode option.
Select root shell option
Now replace <USER> with the above response from whoami

```
adduser <USER> admin
```

Cherz

---

### Post by moorhead98 on 2011-10-23
> **zero2xiii said:**
> An easy answer:

Go to terminal and type:

```
whoami
```Now replace <USER> with the above response from whoami

```
adduser your_username admin
```Cherz

Thank you.

ok.. it says I am jcm, even though everything else says it is Will. Whatever, that doesn't matter.
Can I run adduser in a regular terminal on unity? Or the recovery console (available on login)?

---

### Post by zero2xiii on 2011-10-23
Non of the above,

You need to restart your computer, and during the grub menu, select recovery console and then drop to a ROOT shell.

That is the easiest and fastest (and probably the only way right now) to get you back to admin

Cherz again

---

### Post by moorhead98 on 2011-10-23
> **zero2xiii said:**
> Non of the above,

You need to restart your computer, and during the grub menu, select recovery console and then drop to a ROOT shell.

That is the easiest and fastest (and probably the only way right now) to get you back to admin

Cherz again

It didn't work. I ran ```
adduser jcm admin
``` in the shell, and this is what was returned:```

Adding user 'jcm' to group 'admin' ...
Adding user jcm to group admin
gpasswd: cannot lock /etc/group/; try again later.
adduser: 'usr/bin/gpasswd -a jcm admin' returned error code 1. Exiting.
```I did it twice and both times that happened. Any reason why that didn’t work? And are there any other solutions?

---

### Post by moorhead98 on 2011-10-23
Solved it! You need to remount the file system before running the code. Marking thread as solved

---

