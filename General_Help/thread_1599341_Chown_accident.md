---
title: "Chown accident"
date: 2010-10-17
forum: General Help
---

### Post by Matthew459743 on 2010-10-17
*Ubuntu 10.04*
First off I changed my Ubuntu root password so I could use su.
I ran the commands:
su
chown -R matthewsedam /
chown -R root /
 
I cannot access files but can log on.

---

### Post by sgage on 2010-10-17
Why on Earth did you do that?

---

### Post by sisco311 on 2010-10-17
The quickest and easiest solution is to backup your data and reinstall Ubuntu.

---

### Post by Halfbrazilian on 2010-10-17
> **Matthew459743 said:**
> *Ubuntu 10.04*
First off I changed my Ubuntu root password so I could use su.
I ran the commands:
su
chown -R matthewsedam /
chown -R root /
 
I cannot access files but can log on.

I think your issue is that when you ran the last command you changed the ownership of your home directory (along with everything else) to root. You need to su into root and then run:

chown -R mathhewsedam:matthewsedam /home/matthewsedam/

I hope that helps.

*Edit*

I just realized that you still might run into with other folder problems. Some processes have folders owned by them and they wouldn't be able to edit their own data. You should probably just backup and reinstall.

---

### Post by Matthew459743 on 2010-10-17
I'll try that and see if it helps.

---

### Post by WorMzy on 2010-10-17
> **Matthew459743 said:**
> First off I changed my Ubuntu root password so I could use su.
Why? Use sudo.

> **Matthew459743 said:**
> I ran the commands:
su
chown -R matthewsedam /
chown -R root /
 
I cannot access files but can log on.

Yeah, don't do that.

Reinstall.

---

### Post by sisco311 on 2010-10-17
> **Halfbrazilian said:**
> 
*Edit*

I just realized that you still might run into with other folder problems. Some processes have folders owned by them and they wouldn't be able to edit their own data. You should probably just backup and reinstall.

Yep, and chown clears the setiud and setgid bits...

---

### Post by holiday on 2010-10-17
Your second line put everything under control of root so you won't be able to access anything that doesn't have world access. 

So I don't know how you're going to be able backup anything unless you log in as root. 

Once you do that, get all your precious data off and do like the guy said: start again. 

It looks like your first line was trying to make everything owned by you. 

This is a bad idea because there are many essential processes that require privileges that you don't have. Many processes assume that they own certain directories and files - 700 assumptions - and since they no longer own those directories they can't execute. 

It seemed like a good idea at the time. I can see, I think, what you were trying to do. A better solution - though not advisable - is to always log in as root. Then you will have access to everything.

The best solution is to accept standard practice. Use sudo. I don't like sudo so I will

$sudo su

type in my password and go into a root shell. 

But it's worth the time to read up on Unix permissions. You like to tinker so it's a good idea to know something about what you're tinkering with.

Nice try. No cigar.

---

### Post by blueridgedog on 2010-10-17
Fatal error...as others mention it is best to reinstall.  Wrap it up to a good learning experience and a great reason not to enable the root account.

---

### Post by Matthew459743 on 2010-10-18
Thank you all for your advice, I am just going to reinstall and think of it as a learning experience.

---

### Post by Diametric on 2010-10-18
> **holiday said:**
> Your second line put everything under control of root so you won't be able to access anything that doesn't have world access. 
 
So I don't know how you're going to be able backup anything unless you log in as root. 
 
Once you do that, get all your precious data off and do like the guy said: start again. 
 
It looks like your first line was trying to make everything owned by you. 
 
This is a bad idea because there are many essential processes that require privileges that you don't have. Many processes assume that they own certain directories and files - 700 assumptions - and since they no longer own those directories they can't execute. 
 
It seemed like a good idea at the time. I can see, I think, what you were trying to do. A better solution - though not advisable - is to always log in as root. Then you will have access to everything.
 
The best solution is to accept standard practice. Use sudo. I don't like sudo so I will
 
$sudo su
 
type in my password and go into a root shell. 
 
But it's worth the time to read up on Unix permissions. You like to tinker so it's a good idea to know something about what you're tinkering with.
 
Nice try. No cigar.
 
 
^^Best reply.  Instead of "why would you do that" - you gave an explanation and feedback.  Very helpful.

---

