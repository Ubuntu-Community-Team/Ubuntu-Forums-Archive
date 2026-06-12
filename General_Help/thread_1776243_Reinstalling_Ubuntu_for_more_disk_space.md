---
title: "Reinstalling Ubuntu for more disk space"
date: 2011-06-05
forum: General Help
---

### Post by baronn on 2011-06-05
Hello, 

I want to format my HDD to give more space to Ubuntu (unfortunately some dbags won't change Windows, and I still have to use them). My HDD is 160GB and I'm thinking of spliting it in half. I'd like to know how I specify how much space I leave for each OS. 
Do I choose it while installing one of the two OS?

Thank you in advance :)

---

### Post by pqwoerituytrueiwoq on 2011-06-05
you can resize existing partitions using gparted
i can dual boot ubuntu/xp on a 40gb hdd a 160 is plenty (unless you down lots of vids to your hdd)
10 gb for system is reasonable for ubuntu you can decide how much you need for your files

---

### Post by papibe on 2011-06-05
> **pqwoerituytrueiwoq said:**
> you can resize existing partitions using gparted
i can dual boot ubuntu/xp on a 40gb hdd a 160 is plenty (unless you down lots of vids to your hdd)
10 gb for system is reasonable for ubuntu you can decide how much you need for your files

+1

Just remember to defrag your Windows partition before running gparted. I would even recommend defragmenting a couple of times.

Regards.

---

### Post by baronn on 2011-06-05
So there is no need to format y HDD?

Actually I did something stupid when I was trying to get Ubuntu on my PC. I must have mistyped my password because I couldn't get it right. So -stupid me- I cleard Ubuntu's partition and Windows now needs to be repaired via the install CD, which I don't have. So I can't defrag through Windows.

So, one of the reasons I wanted to format my disk is to clear it from the old installation of XP, and the install either 7 or XP, and ubuntu. Can I just clear Window's partition in order to reinstall?

Can I install Ubuntu to the whole disk, and then size it down to ~60GB leaving the rest for windows?

About my files, I store everything on an external HDD ;)

---

### Post by ivanovnegro on 2011-06-05
> **baronn said:**
> So there is no need to format y HDD?

Actually I did something stupid when I was trying to get Ubuntu on my PC. I must have mistyped my password because I couldn't get it right. So -stupid me- I cleard Ubuntu's partition and Windows now needs to be repaired via the install CD, which I don't have. So I can't defrag through Windows.

So, one of the reasons I wanted to format my disk is to clear it from the old installation of XP, and the install either 7 or XP, and ubuntu. Can I just clear Window's partition in order to reinstall?

Can I install Ubuntu to the whole disk, and then size it down to ~60GB leaving the rest for windows?

About my files, I store everything on an external HDD ;)

Ok, that wasnt so good now.
To achieve what you wanted to do you did not have to format your HDD.
Now, first repair your Windows and then install Ubuntu, not first Ubuntu.
Then you can decide how much space you want to give to Ubuntu when you install it alongside Windows. Defragment before intalling Ubuntu again and always backup your files in first place!!!

---

### Post by baronn on 2011-06-05
This is my problem. If I could repair XP everything would be fine (besides some extra space I need for Ubuntu.) BUT, I do not have the installation cd for XP. Can I just download any XP installer, and use it? I thought I had to use the CD with which my XP was installed.

I haven't done a formatting to my PC. My current state is:
XP needing repair, Ubuntu 11.04 up and running just fine.

---

### Post by dFlyer on 2011-06-05
> **baronn said:**
> Hello, 

I want to format my HDD to give more space to Ubuntu (unfortunately some dbags won't change Windows, and I still have to use them). My HDD is 160GB and I'm thinking of spliting it in half. I'd like to know how I specify how much space I leave for each OS. 
Do I choose it while installing one of the two OS?

Thank you in advance :)

Before you do anything clone your drive. Search google for free version of cloning software. It will make things much easier to repair should something go wrong.

---

### Post by pqwoerituytrueiwoq on 2011-06-05
i think any oem xp install disk will work the the key on the sticker you have
btw home is not the same thing as professional
what do you need to have xp for anyway?

---

### Post by baronn on 2011-06-05
> **dFlyer said:**
> Before you do anything clone your drive. Search google for free version of cloning software. It will make things much easier to repair should something go wrong.

clone it to where?

> **pqwoerituytrueiwoq said:**
> i think any oem xp install disk will work the the key on the sticker you have
btw home is not the same thing as professional
what do you need to have xp for anyway?

I'm sorry but I didn't get it. If I download an XP installer disk, I will be able to repair XP?

I need XP because some people with which I cooperate still use them, and there are some special programs....

...and the ocassional games ofc! :D

---

### Post by pqwoerituytrueiwoq on 2011-06-05
did you delete the windows partition?
if not all you need to do is install ubuntu next to it and grub will let you boot into it
if you did delete it there is no repair it is reinstall inthat case you need the right cd version for your license key (see the sticker on your computer case)

---

### Post by ivanovnegro on 2011-06-05
It seems more important now to find a solution how to get back with the XP install before anything else.
Im not a Windows user, so I have no idea why you need now the CD to repair it.
Could you did that from the console or do you really need a WinXP CD?
I know at least that there is an option to repair the Windows install by typing something like "R", but am really not sure, and of course not sure if the CD is really required.

Somebody with some more Win experience could please join us to get this guy finally on Ubuntu?

---

### Post by baronn on 2011-06-06
> **pqwoerituytrueiwoq said:**
> did you delete the windows partition?
if not all you need to do is install ubuntu next to it and grub will let you boot into it

NO, I haven't deleted XP. The partition is still there but damaged. 

I HAVE Ubuntu. I'm using it right now, because I can't boot my pc otherwise...

> **ivanovnegro said:**
> It seems more important now to find a solution how to get back with the XP install before anything else.
Im not a Windows user, so I have no idea why you need now the CD to repair it.
Could you did that from the console or do you really need a WinXP CD?
I know at least that there is an option to repair the Windows install by typing something like "R", but am really not sure, and of course not sure if the CD is really required.

Somebody with some more Win experience could please join us to get this guy finally on Ubuntu?

[http://www.youtube.com/watch?v=K95gKIX-BbI&feature=fvst](http://www.youtube.com/watch?v=K95gKIX-BbI&feature=fvst)

This is what I followed, untill I realised I didn't have the CD and banged my head on the desk! :P :D

As I said I already have Ubuntu, and I am running this OS. What I want to do, Is to get back Windows.

---

### Post by ivanovnegro on 2011-06-06
Then it seems you really need a CD, have you a friend with a Windows copy? You can still use your license key.

---

### Post by misterbiskits on 2011-06-06
If you have nothing of value on the computer (you said you store your stuff on a separate drive?) I recommend you format all partitions before resizing.  Resizing partitions that contain data takes a looong time.
Of course you will need the Windows install disk afterwards...

---

### Post by pqwoerituytrueiwoq on 2011-06-06
> **misterbiskits said:**
> If you have nothing of value on the computer (you said you store your stuff on a separate drive?) I recommend you format all partitions before resizing.  Resizing partitions that contain data takes a looong time.
Of course you will need the Windows install disk afterwards...
not if you shrink from the right  a xp install takes like 2 to 3 hours (including installing all the stuff it needs to be useful)

what does xp say when you try to boot it?

---

### Post by baronn on 2011-06-06
XP is honestly stupid... It repaired itself somehow... Now it seems to be running ok.

So, for giveng a bit more space to Linux now.... How do I do it?

---

### Post by pqwoerituytrueiwoq on 2011-06-07
fire up a live cd 
open gparted shrink windows 
then you can move ubuntu over in to the free space then grow ubuntu
post a gparted screen shot if you need more help than that

---

