---
title: "I never want to enter my password again"
date: 2009-07-23
forum: General Help
---

### Post by MikeonTV on 2009-07-23
Hi there. I use ubuntu 9.04 on my eeepc. This machine is third on the list of systems I use the most. I take it when I am traveling and use it for the odd word processor, browsing and email.

I am comfortable in terminal and I often test out linux software on this machine. But one thing I dont do on it is store vital information about myself. I am not afraid of someone breaking into this machine. 

How can I disable ever having to prove I am the administrator to this computer? 

I dont want to be prompted in terminal when I write sudo and I dont want to confirm my password when I am installing/upgrading software in the UI. 

I never want to be asked again what my password is.

Thanks for your time.

---

### Post by wojox on 2009-07-23
Here:

[https://help.ubuntu.com/community/RootSudo#Remove%20Password%20Prompt%20For%20sudo](https://help.ubuntu.com/community/RootSudo#Remove%20Password%20Prompt%20For%20sudo)

---

### Post by MikeonTV on 2009-07-23
Also I would like it if I didn't have to enter my password to log into my Ubuntu user account at start up

how do I do that?

---

### Post by t4thfavor on 2009-07-23
Someone stole my eeepc, and Im very glad I had passwords on it. Since the normal theif type will have no idea how to A.) Use linux to find details of the PC's owner, and B.) remove the minipciE SSD, and fish for data on it.

Also they Probably thought they were stealing a portable dvd player and junked it when they found out it was an alien spaceship.

---

### Post by wojox on 2009-07-23
System > Administration > Login Window

Click Security Tab

Check Enable Automatic Login

Add user

---

### Post by uberdonkey5 on 2009-07-23
Administrative passwords are useful for preventing viruses from downloaded software. If you are only a casual user, do you really use admin passwords that much?

I have removed login passwords from all the computers I use since physical access to any computer allows it to be accessed. However this is a good point..

> **t4thfavor said:**
> Someone stole my eeepc, and Im very glad I had passwords on it. Since the normal theif type will have no idea how to A.) Use linux to find details of the PC's owner, and B.) remove the minipciE SSD, and fish for data on it.

Also they Probably thought they were stealing a portable dvd player and junked it when they found out it was an alien spaceship.

but is it real? I'm not a computer expert at all, but I have software to reset any windows password to whatever I want (and its just as easy in linux).

---

### Post by MikeonTV on 2009-07-23
> **wojox said:**
> Here:

[https://help.ubuntu.com/community/RootSudo#Remove%20Password%20Prompt%20For%20sudo](https://help.ubuntu.com/community/RootSudo#Remove%20Password%20Prompt%20For%20sudo)


This tut did not work. Thanks but could it be because of the version?

> **t4thfavor said:**
> Someone stole my eeepc, and Im very glad I had passwords on it. Since the normal theif type will have no idea how to A.) Use linux to find details of the PC's owner, and B.) remove the minipciE SSD, and fish for data on it.

Also they Probably thought they were stealing a portable dvd player and junked it when they found out it was an alien spaceship.

I really am not worried about that. Like I said there is nothing on this machine that is of any value to me.

---

### Post by Johnny B on 2009-07-23
can't you just login as root?
im sure theres a way to do that.

---

### Post by sisco311 on 2009-07-23
> **MikeonTV said:**
> This tut did not work. Thanks but could it be because of the version?



I really am not worried about that. Like I said there is nothing on this machine that is of any value to me.

Just uncomment the *%sudo ALL=NOPASSWD: ALL* line in the sudoers file and add your user to the sudo group. Always edit the file with *sudo visudo*.

---

### Post by wojox on 2009-07-23
What didn't work when you edited sudoers?

<username> ALL=NOPASSWD: ALL

Reboot maybe?

---

### Post by doas777 on 2009-07-23
it sounds like you will be interested in Windows 98!

---

### Post by Anzan on 2009-07-23
My first thought:

This makes your machine an attack vector for other machines. It affects the security of everyone else.

But of course, it is up to you.

---

### Post by xebian on 2009-07-23
> **MikeonTV said:**
> This tut did not work. Thanks but could it be because of the version?



I really am not worried about that. Like I said there is nothing on this machine that is of any value to me.

sudo -i

---

### Post by doas777 on 2009-07-23
> **MikeonTV said:**
> This tut did not work. Thanks but could it be because of the version?



I really am not worried about that. Like I said there is nothing on this machine that is of any value to me.

theres one thing that is always on your PC, that you shoudl care about: your reputation. if the FBI shows up at your door, asking why your PC was sending abnormal traffic to the Nuclear Regulatory Control network, then you are in trouble. even if 3 years later you are vindicated, your finances, social life, and job future are all ruined.

---

