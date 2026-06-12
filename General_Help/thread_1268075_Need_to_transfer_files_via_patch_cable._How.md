---
title: "Need to transfer files via patch cable. How?"
date: 2009-09-16
forum: General Help
---

### Post by Roasted on 2009-09-16
I have two imaging laptops I use at work, both with static IPs.

192.168.1.100
192.168.1.101

There's an image on 100 I need to transfer to 101, however I have NO external hard drive space whatsoever and the image is pushing 40gb.

How can I kick it over through a patch cable?

---

### Post by StuartN on 2009-09-16
> **Roasted said:**
> I have two imaging laptops I use at work, both with static IPs.

Do you mean a) these laptops are connected by ethernet / wireless to a network with these IP addresses, or b) these laptops have no network connection?

If a) then simply share a folder on one of them (install Samba if necessary) and transfer the file into that shared folder.

If b) then get a crossover (gaming) cable and connect the two ethernet ports together. Actually, most ethernet ports detect crossed cables and a regular ethernet cable will probably work. As before, simply share and copy.

Unshare after you have finished if you are security conscious.

---

### Post by Roasted on 2009-09-16
So I just share out a folder? How do I find it then? Places - Computer? Or what?

And yes - just a patch cable. No switch.

---

### Post by cranecreek on 2009-09-16
Not 100% sure what you need but here is another option us scp which copies files over ssh try [this]("http://www.go2linux.org/scp-linux-command-line-copy-files-over-ssh") for some reading on how scp works. 
Good luck to you

---

### Post by skatinjj on 2009-09-16
> **Roasted said:**
> So I just share out a folder? How do I find it then? Places - Computer? Or what?

And yes - just a patch cable. No switch.

A patch cable is just a straight through cable and when connected between just two computers will not work.

A switch would do the cross-over for you and that is why we use patch cables when connecting to a switch/router.

You will need a cross-over cable to connect the two computers together to be able to share files.

---

### Post by Roasted on 2009-09-16
That's fine, I can make a crossover cable. I just need to know what to do in Ubuntu to see the other machine.

---

### Post by Vaphell on 2009-09-16
not that i have done anything like it, but i think that connecting and configuring ethernet adapters (addresses, network mask) is enough.

---

### Post by unutbu on 2009-09-17
With a cross-over cable, perhaps try this:
[http://ubuntuforums.org/showpost.php?p=7083429&postcount=16](http://ubuntuforums.org/showpost.php?p=7083429&postcount=16)

---

### Post by Roasted on 2009-09-17
Okay, I can see how that would get the machines to talk to each other, but where do I go to actually open up a window of the other computer's hard drive contents so I can copy/paste stuff there to initiate the file transfer?

---

### Post by scouser73 on 2009-09-17
Hi, I've Googled this for you: [[COLOR="Red"]**Share Files & Folders On Ubuntu**[/COLOR]]("http://www.simplehelp.net/2007/05/19/how-to-share-files-and-folders-in-ubuntu/").

I hope this does the trick for you.

---

