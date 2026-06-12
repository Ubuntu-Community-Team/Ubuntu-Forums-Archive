---
title: "Virus Question"
date: 2011-02-21
forum: General Help
---

### Post by Kocrachon on 2011-02-21
So right now I am dual booting Windows 7 and Ubuntu.

Today, my landlord asked me for help because his machine is filled with virues. So first thing I did was throw it onto one of my spare sata drives and tried to clean it in windows. Got a torjan that for some reason, MS essentials wasnt able to remove. So I am now in Ubuntu trying to remove it with KlamAV, however, KlamAV doesn't seem to spot the same file right now.

So my question is, is there another good virus scanner that works? I tried AVG but it seems they don't support linux anymore, just linux server.

---

### Post by whatthefunk on 2011-02-21
Have you tried running hijackthis in windows?

---

### Post by CHRSB on 2011-02-21
> **Kocrachon said:**
> So right now I am dual booting Windows 7 and Ubuntu.

Today, my landlord asked me for help because his machine is filled with virues. So first thing I did was throw it onto one of my spare sata drives and tried to clean it in windows. Got a torjan that for some reason, MS essentials wasnt able to remove. So I am now in Ubuntu trying to remove it with KlamAV, however, KlamAV doesn't seem to spot the same file right now.

So my question is, is there another good virus scanner that works? I tried AVG but it seems they don't support linux anymore, just linux server.

I will never understand why people will waste countless hours trying to remove a virus when I can reformat and reinstall  Windows 7 in about an hour.

But no, you will not find a Linux AV suite that will do much for a Windows Trojan. What I do for my clients who live to get these Internet sex diseases is install an Ubuntu partition and tell them if they want to surf for pron, use Ubuntu.

Besides, if he has that many viruses you can gaurntee that there are some that MSE did not even find. I bet he is on a botnet sending us all spam.

---

### Post by Kocrachon on 2011-02-21
No, he had one trojan that I cannot remember what MSE named it, and then Klam also found a exploit.pdf and thats about it.

The reason he doesn't want me to format it, is because him and his wife both have research on it because they also both work for the local univeristy. And theres no porn on it, I already ensured that they weren't abusing it for that purpose.

Its one single trojan that I was not able to remove, and one other thing, thats it, not as bad as most other people

---

### Post by gerowen on 2011-02-21
Avast Home Edition has a Linux version that's pretty good, although mine stopped working after an update and gave me some funky error message.  I looked up the solution, something about a soft cap on some kernel setting, too much for me to worry about since all of my computers run Ubuntu.  ANYWAY, it is out there and they update it at least a couple of times a week.  If it comes down to it just back up their stuff before you format their hard drive.

---

### Post by asmoore82 on 2011-02-21
If he's got 1, he's got a lot more that no scanner can yet find and identify.

The Nuclear Option is always the best way to deal with Windows.

---

### Post by dstudio101 on 2011-02-21
Before you do anything drastic with their computer -- make a back up of it -- I usually use System Rescue CD for this.  It works great for backup of Windows XP -- not sure about the other version of Windows though.

It is time consuming for a beginner but very effective for this kind of problems.  You could always return to the 'original' if something goes wrong with killing the virus.

Better yet, do a clean install and back up that system so they could always return to a clean install if a virus visits their computer.

That's my usual answer to this kinds of problems -- and I face these kinds of problems for many years -- those windows XP desktop users -- never learns...and it's a living for me.

This is not much help for a quick fix though.

---

### Post by gerowen on 2011-02-21
> **dstudio101 said:**
> Better yet, do a clean install and back up that system so they could always return to a clean install if a virus visits their computer.

This is kind of close to what I do for my little business.  After I've re-baselined a machine I use Clonezilla and make an image of the machine after everything has been done (drivers, software, updates, everything).  I keep that image in a folder that I create per customer and keep it on file for 30 days.  If within those 30 days the user screws their computer up again they can bring it back and have that image restored for a fraction of the full price of a reimage.

---

### Post by CHRSB on 2011-02-21
> **Kocrachon said:**
> No, he had one trojan that I cannot remember what MSE named it, and then Klam also found a exploit.pdf and thats about it.

The reason he doesn't want me to format it, is because him and his wife both have research on it because they also both work for the local univeristy. And theres no porn on it, I already ensured that they weren't abusing it for that purpose.

Its one single trojan that I was not able to remove, and one other thing, thats it, not as bad as most other people

You said in your original post 

> Today, my landlord asked me for help because his machine is filled with virues.

Now you say he has two? Filled = two?

Knowing the name of a trojan is KEY to removing it.

If it is a university computer, have them taket to the university. If they are dumb enough to think that they will lose their research by you backing up and reformatting their they should not be using a computer or be doing research. And if you do not know you can back up their computer before you reformat it then you should not be helping them.

---

### Post by rvchari on 2011-02-21
> **Kocrachon said:**
> So right now I am dual booting Windows 7 and Ubuntu.

Today, my landlord asked me for help because his machine is filled with virues. So first thing I did was throw it onto one of my spare sata drives and tried to clean it in windows. Got a torjan that for some reason, MS essentials wasnt able to remove. So I am now in Ubuntu trying to remove it with KlamAV, however, KlamAV doesn't seem to spot the same file right now.

So my question is, is there another good virus scanner that works? I tried AVG but it seems they don't support linux anymore, just linux server.

if windows identified a particular trojan, it must ve put it on quarantine so Klam is not able to locate or identify (may be coz thats my gutt feeling)

secondary, there is avast for linux. you can go their site and download the linux version. you may have to register so they will email you the key.
each virus scanner has to be updated with the latest virus definitions (otherwise it is a useless software !!!)

third....
suggest your landlord to use ubuntu to surf the net and secure himself from the headaches of viruses.... without using any AV !!!

---

### Post by mastablasta on 2011-02-21
> **CHRSB said:**
>  
Knowing the name of a trojan is KEY to removing it.

 
that's true. i once got a nasty one on 98. it was a rootkit. luckilly soem guy made a special tool for removing it. he stopped the porject after some time. too bad as he was the only one fighting it. other AV programmes could not remove it. 
 
anyway as it was said back up data and do reformat.
 
and tell them they need to use some virus scanner and also a firewall. oh and if oyu can close them the default open ports after you solve it.

---

### Post by ephmanjmm on 2011-02-21
My .02

Clone the drive using Clonezilla as a safeguard against a big mistake.
Run Spybot Search and Destroy.
Run Malwarebytes (free version)
Run Hitman Pro 3.x  (free version)

As others have said, make note of the name of the malware and people might be able to provide more help.

---

### Post by Spyderkid on 2011-02-21
You may not want to make a back up CD trojans are clever and generally add themselves to the CD by complicated ways I have no time to explain. 

try getting a Free Trial of Virus software get Titanium/Norton

or prefrebably if you can ***_BitDefender_*** or ***_ADWARE PRO INTERNET SECURITY_***

then with the free-trail remove the software.

---

