---
title: "Can I create a list, from LiveCD, Of what programs are installed on HDD?"
date: 2011-01-04
forum: General Help
---

### Post by Rasa1111 on 2011-01-04
Hey all, 

I made this thread last night~
[http://ubuntuforums.org/showthread.php?t=1659239](http://ubuntuforums.org/showthread.php?t=1659239)

Because my Ubuntu failed, and i have no idea why. 
I hadnt done anything different or risky.. 
and Ive no idea what to do. 

So,
 It appears Im going to have to do a re-install. 

Which, I really dont mind too much... (especially with Ubuntu)
But It will stink if i *again* lose all my bookmarks , and lose track of all my installed programs. 
The programs, not as much of an issue as the bookmarks in my browser.. 

But,

 **_I would like to know,_**
 If I can somehow access the HDD from the LiveCD, So that I can create just a simple text list of all programs installed on the hdd? 

 I cannot access my HDD except through the LiveCD ..
So is there a way I can do this? 

Some kind of simple command I can toss into terminal, and have it output me a text file of all programs installed? or something? 

 I really am totally clueless on how I would be able to save my chromium bookmarks. 
(if even possible). 

Any help/info/insight you can provide...
would not go unappreciated. 

 Thanks for your time. <3

---

### Post by bodhi.zazen on 2011-01-04
> **Rasa1111 said:**
> Hey all, 

I made this thread last night~
[http://ubuntuforums.org/showthread.php?t=1659239](http://ubuntuforums.org/showthread.php?t=1659239)

Because my Ubuntu failed, and i have no idea why. 
I hadnt done anything different or risky.. 
and Ive no idea what to do. 

So,
 It appears Im going to have to do a re-install. 

Which, I really dont mind too much... (especially with Ubuntu)
But It will stink if i *again* lose all my bookmarks , and lose track of all my installed programs. 
The programs, not as much of an issue as the bookmarks in my browser.. 

But,

 **_I would like to know,_**
 If I can somehow access the HDD from the LiveCD, So that I can create just a simple text list of all programs installed on the hdd? 

 I cannot access my HDD except through the LiveCD ..
So is there a way I can do this? 

Some kind of simple command I can toss into terminal, and have it output me a text file of all programs installed? or something? 

 I really am totally clueless on how I would be able to save my chromium bookmarks. 
(if even possible). 

Any help/info/insight you can provide...
would not go unappreciated. 

 Thanks for your time. <3

You can do this in many ways.

Easiest is with a chroot. 

Mount your old root partition in say /mnt, chroot into it, and run

```
sudo dpkg -l
```

Assuming you are running as root you can run

```
dpkg -l > package.list
```

You can also do this:

[http://www.ubuntu-unleashed.com/2008/04/howto-restore-all-installed-packages-in.html](http://www.ubuntu-unleashed.com/2008/04/howto-restore-all-installed-packages-in.html)

Note: On that blog you can not re-direct output with sudo that easily, so run dpkg as root

```
sudo -i
dpkg --get-selections > /etc/package.selections
```

Or use tee or sudo -c bash "command with quotes > and redirect"

---

### Post by lithopsian on 2011-01-04
What you ask is not trivial.  You can create a list of installed packages, which will cover most of what you want.  Of course most of them will be from the standard installation so finding the ten extra ones you added might be tricky.

Then there is other stuff you might have installed manually.  They could be anything and anywhere, no obvious way to find them all.  Convention says you should have installed them under /opt, so by all means have a look there.

Another thing you can consider since you are about to do a new install is to put .opt on a separate partition.  That way you won't blow it away next time you install Ubuntu from scratch.  You can do the same with /home and you won't lose all your bookmarks, email, desktop settings, music, etc.

---

### Post by Rasa1111 on 2011-01-04
Thanks guys,
 I appreciate it. <3

Sad to have to admit..
 I do not understand what most of this means. 

> Easiest is with a chroot. 

Mount your old root partition in say /mnt, chroot into it, and run
> 
You can also do this:

[http://www.ubuntu-unleashed.com/2008...ckages-in.html]("http://www.ubuntu-unleashed.com/2008/04/howto-restore-all-installed-packages-in.html")

Note: On that blog you can not re-direct output with sudo that easily, so run dpkg as root
> Or use tee or sudo -c bash "command with quotes > and redirect" I really dislike seeming soo simple, and being so confused.. 
I know Ive been using Ubuntu for almost a year now.. 
but I still do not understand most of this stuff. 
I need to be spoken to, with stuff..
like you speak to a small child with a learning disability.  lol

 Im sorry for wasting your guys time, 
as I am still pretty much just as clueless as before....

( I have tried some of the commands, but get nothing in return for any of them, except for negativity.) lol

I dunno..
Guess i just cut my losses and try to figure it out from memory. :(

---

### Post by bodhi.zazen on 2011-01-04
Assuming your root partition was sda1

boot a live CD

```
sudo mount /dev/sda1 /mnt
sudo chroot /mnt
dpkg --get-selections > /root/package.list
exit
cp /mnt/root/package.list /wherever_you_want_to_save_it
```

Reinstall, enable your repos

```
sudo -i
apt-get update
apt-get dist-upgrade
```

Reboot (new kernel)

```
sudo -i
sudo dpkg --set-selections < /root/package.list && apt-get dselect-upgrade
```

---

### Post by bodhi.zazen on 2011-01-04
System rescue is never fun.

In the future:

1. Make a separate data partition so you can re-install your OS without data loss.

2. Back up your data.

3. Learn to use the terminal. Part of the reason you are stuck is that you never bothered to learn to use the terminal. Sure the graphical interface is nice, but the command line is there when the graphical tools fail and the time to learn the command line is NOT when you are having a crisis.

---

### Post by Rasa1111 on 2011-01-04
Thanks Bodhi, I will try that shortly. 

> Re:

In the future:

1. Make a separate data partition so you can re-install your OS without data loss.

2. Back up your data.

3. Learn to use the terminal. Part of the reason you are stuck is that  you never bothered to learn to use the terminal. Sure the graphical  interface is nice, but the command line is there when the graphical  tools fail and the time to learn the command line is NOT when you are  having a crisis.


1.  Ive thought about that the last 2 installs Ive done, but always end up not doing it. doh! 

2. I usually do make, and keep backups... but the last one was a few months ago. .. DOH! again. 

3. I actually do try to learn the terminal,
and do use it for most things that don't confuse the hell out of me.. 
But I do "take it slow", as Id rather not get too playful and really break something. 

 But I do understand how crucial the terminal is, and I do like to use it.. 
it still just feels like a foreign language, when people who are well versed in it, ..
try to explain to those who are not so well versed. 

I really do like terminal though, and use it as often as I can,
though I know I still have *tons *to learn. 

 Thanks again, 
 I appreciate your help.

---

### Post by Rasa1111 on 2011-01-04
> **bodhi.zazen said:**
> Assuming your root partition was sda1

boot a live CD

```
sudo mount /dev/sda1 /mnt
sudo chroot /mnt
dpkg --get-selections > /root/package.list
exit
cp /mnt/root/package.list /wherever_you_want_to_save_it
```



Bodhi~
 I got the list! 
Thank you soo much! <3

---

### Post by bodhi.zazen on 2011-01-04
> **Rasa1111 said:**
> Bodhi~
 I got the list! 
Thank you soo much! <3

You are most welcome.

I am sorry if I came across a bit harsh, my point is keep learning and asking questions.

---

### Post by Rasa1111 on 2011-01-04
> **bodhi.zazen said:**
> You are most welcome.

I am sorry if I came across a bit harsh, my point is keep learning and asking questions.

No worries mate, 
I completely understand.

 Now I feel  better about doing a re-install, if indeed I have to.   lol 

 Many thanks <3

---

### Post by Rasa1111 on 2011-01-17
Bodhi~

Can you tell me how to do this same thing,
 But from a folder on my desktop? lol

I am a little confused on what to put in the command. 

I have a folder on my desktop, Named "Books2Sort"
That contains Python, Java, and Android books/PDF's.. 

and I need to create a list of all the books/files in that folder for someone. 

Can you help me again mate? lol  

 Thanks in advance. <3

---

### Post by Rasa1111 on 2011-01-17
Oops!
Nevermind, 
 I got it! lol

 Thanks. <3

---

### Post by bodhi.zazen on 2011-01-17
> **Rasa1111 said:**
> Oops!
Nevermind, 
 I got it! lol

 Thanks. <3

Nice =)

---

### Post by Rasa1111 on 2011-01-17
:)

The "embedded terminal" in nautilus elementary is awesome! 
Helped soo much! 
<3 :D

---

