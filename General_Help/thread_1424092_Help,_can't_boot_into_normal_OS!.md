---
title: "Help, can't boot into normal OS!"
date: 2010-03-07
forum: General Help
---

### Post by gerbilconsultant on 2010-03-07
After installing some  updates to ubuntu 9.10 my laptop will no longer let me boot into the normal OS environment. 
 It takes me to the GNU GRUB version 1.97~beta4 command prompt. I think I  am supposed to execute the following commands in order to get it to boot  normally:

[SIZE=2]set root=(hdX,Y)
linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdXY ro
intrid /boot/intrid.img-2.6.31-14generic 
boot[/SIZE]

To find the correct partition I entered 'ls' and it gave me back:
(loop0) (hd0) (hd0,4) (hd0,3) (hd0,2) (hd0,1)

So my question is if I can only find the boot files in the (loop0) how do I go about setting this up so I can boot into my OS as it normally should?

Any help would be great!

---

### Post by bcbc on 2010-03-07
> **gerbilconsultant said:**
> After installing some  updates to ubuntu 9.10 my laptop will no longer let me boot into the normal OS environment. 

More info needed: what do you mean by normal OS environment? Are you running a dual boot? Wubi? If you mean the latest kernel, can you boot older kernel versions? (etc.)

Posting the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") will make it easier for someone to help.

---

### Post by firearbete on 2010-03-08
First post ever. I'm a total newb, but I manage to find out that I've got the same problem than gerbil consultant.. It's the second time it happens to ubuntu and always happens after I install Ubuntu suggested updates. 

I'm running it from a dual boot on a asus 1005HA. It's installed in windows XP (that came with the computer). 

After I choose Ubuntu in the startup GNU ( I figure out the black screen with a choice between Ubuntu and windows is called something like that ) it brings me to that same GNU GRUB version 1.97~beta4 menu. And from there I have no idea what to do.

I'll try the boot process explained in the later post. I'll keep you updated. Hopefully running from Ubuntu.

---

### Post by bcbc on 2010-03-08
> **firearbete said:**
> First post ever. I'm a total newb, but I manage to find out that I've got the same problem than gerbil consultant.. It's the second time it happens to ubuntu and always happens after I install Ubuntu suggested updates. 

I'm running it from a dual boot on a asus 1005HA. It's installed in windows XP (that came with the computer). 

After I choose Ubuntu in the startup GNU ( I figure out the black screen with a choice between Ubuntu and windows is called something like that ) it brings me to that same GNU GRUB version 1.97~beta4 menu. And from there I have no idea what to do.

I'll try the boot process explained in the later post. I'll keep you updated. Hopefully running from Ubuntu.

You installed within windows i.e. used wubi. So see this [link]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10") for a fix. 
Don't bother running the bootinfoscript (if you're using wubi the above link should fix your problem).

---

### Post by firearbete on 2010-03-08
I just figured that WUBI was within window. Thank for the link ! As soon as I get back in Ubuntu I reading more about it. I'm gonna stop depending on other people and start helping people :)

---

### Post by firearbete on 2010-03-08
5 min and it was settle. Incredible. Thanks so much.

---

### Post by bcbc on 2010-03-08
> **firearbete said:**
> 5 min and it was settle. Incredible. Thanks so much.

You're welcome (I'm just passing on the solution provided by others). Enjoy.

---

### Post by Rasa1111 on 2010-03-08
very cool! :) glad you got it settled. 

 Now, what would one do if this were to happen, but on a fully installed system? 
 
Say, if one had an Ubuntu only ' machine, and this same thing happened? :?

---

### Post by bcbc on 2010-03-08
> **Rasa1111 said:**
> very cool! :) glad you got it settled. 

 Now, what would one do if this were to happen, but on a fully installed system? 
 
Say, if one had an Ubuntu only ' machine, and this same thing happened? :?

It's less likely to occur when you're running a single OS machine. This particular problem is unique to wubi, but anytime you're running multiple os's there is a possibility to mess things up if you're not careful. Which is why you should take regular backups, and keep a live CD/recovery disc around.

---

### Post by Rasa1111 on 2010-03-08
> **bcbc said:**
> It's less likely to occur when you're running a single OS machine. This particular problem is unique to wubi, but anytime you're running multiple os's there is a possibility to mess things up if you're not careful. Which is why you should take regular backups, and keep a live CD/recovery disc around.

 thank you bcbc:KS

---

