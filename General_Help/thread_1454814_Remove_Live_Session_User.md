---
title: "Remove Live Session User"
date: 2010-04-15
forum: General Help
---

### Post by XCougar on 2010-04-15
Hi all,

Before I start, I have searched everywhere I can for help with this, tried everything suggested and still cant do this.
The annoying thing is ive done it before but cant replicate it.

I have ubuntu installed on my usb stick using lili usb creator.

I want to remove live session user (username ubuntu).

Ive created my own account with privileges etc.

Ubuntu is 9.10.

Any help would be great.

Thanks,

Tom

---

### Post by C.S.Cameron on 2010-04-15
I seem to recall that you can go to System/Admin/Login Screen and set yourself up to log in automatically. Not sure if this still works with 9.10.
Of course you can always do a full install to Flash drive.

---

### Post by XCougar on 2010-04-19
Hi,

Thanks for replying.

I've tried that and it doesn't "stay" that way, next login it reverts back.

Any other ideas please?

Thanks,

Tom,

---

### Post by demangler on 2010-04-20
> **XCougar said:**
> Hi,

Thanks for replying.

I've tried that and it doesn't "stay" that way, next login it reverts back.

Any other ideas please?

Thanks,

Tom,

I am having exactly the same problem. It is very frustrating  - lots of searching only seems to find others with the problem but no solution. 

Perhaps there is some way to prevent the ubuntu live-session user from being generated anew each reboot, or some way of  persisting the changes to the login screen across reboots to make it more secure???.
Somebody help.
Thanks in advance.
dM

perhaps I should add that my usb install is a Ubuntu  9.10 casper persistent one, and apart from this configuration issue I am starting to think I may migrate from slax. At least for a portable office anyway.  :)

Edit... It seems that this user is also automatically logged into all the tty's as well... I can understand this for a live cd, but there must be some way of changing this behaviour for a persistant usb install.

---

### Post by demangler on 2010-04-21
> **demangler said:**
> I am having exactly the same problem. It is very frustrating  - lots of searching only seems to find others with the problem but no solution. 

Perhaps there is some way to prevent the ubuntu live-session user from being generated anew each reboot, or some way of  persisting the changes to the login screen across reboots to make it more secure???.
Somebody help.
Thanks in advance.
dM

perhaps I should add that my usb install is a Ubuntu  9.10 casper persistent one, and apart from this configuration issue I am starting to think I may migrate from slax. At least for a portable office anyway.  :)

Edit... It seems that this user is also automatically logged into all the tty's as well... I can understand this for a live cd, but there must be some way of changing this behaviour for a persistant usb install.

Well, I looked into it for a few hours. Looks like getting rid of the automatic Ubuntu user would fix this, but configuring ubuntu is new to me and it is a bit strange. I think I will stick with slax for now which is perfect apart from the non-cutting-edge-kernel. I guess I'll just have to go through recompiling the kernel and modules for the newer hardware.
This is a shame as I grew to like ubuntu while I was trying to get this working.
I will keep an eye on this thread in case anyone finds a solution.
:)

---

### Post by XCougar on 2010-04-22
> **demangler said:**
> Well, I looked into it for a few hours. Looks like getting rid of the automatic Ubuntu user would fix this, but configuring ubuntu is new to me and it is a bit strange. I think I will stick with slax for now which is perfect apart from the non-cutting-edge-kernel. I guess I'll just have to go through recompiling the kernel and modules for the newer hardware.
This is a shame as I grew to like ubuntu while I was trying to get this working.
I will keep an eye on this thread in case anyone finds a solution.
:)

The really annoying thing is ive done it before, perhaps the older version will allow you to, I think I was doing it on version 8.xx.

---

### Post by steveh_131 on 2010-07-16
I know this thread is a little old, but I thought I would update with my progress on this same problem.

I'm running a persistent USB with Ubuntu 10.04 live, setup with the Universal USB Installer program.

I wanted a little more security than what the live system offered so I needed to get rid of that ubuntu user.

Here's what I did:

- Let the system login, then added a new user and gave it administrator rights.
- Went to System - Administration - Login Screen and set it up to show the screen for choosing who will log in
- Rebooted, logged in as the new user I just created
- Open a terminal, and edit /etc/init/tty1.conf
- I simply commented out the last line (the line starting with exec)
- Repeat for tty2-tty6.conf
- Reboot the system

Now the user ubuntu is no longer logged in or running any processes, so you can open a terminal and sudo deluser ubuntu.

The problem with this method is that now all of my virtual consoles are unusable, they just show an authentication failure.  I would like to have them work as normal.   So far I have tried changing the exec line from 

exec /bin/login -f ubuntu </dev/tty1 > /dev/tty1 2>&1

to 


exec /bin/login </dev/tty1 > /dev/tty1 2>&1

in the hopes that it would allow me to login as normal, but every time I reboot the tty1.conf just gets changed back to the original and it attempts and fails to login as ubuntu.

I hope my progress can help someone, and would love to hear if anybody has a solution to finish the last step of this process.

---

### Post by ItsPerryXD on 2012-05-24
old topic but anyways...

first you useradd a new user
add a passwd to the user
log off the live user and into the user you created

move up to the root by su root
then userdel liveuser

---

