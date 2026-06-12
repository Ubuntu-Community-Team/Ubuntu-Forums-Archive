---
title: "Setting up a computer lab with Ubuntu 6.06"
date: 2006-06-01
forum: General Help
---

### Post by pclancy on 2006-06-01
I'm working in a computer science lab this summer, and it's about time to replace the computers.  Right now we're using 10 eMacs and a Power Mac server, and we're considering building 10 desktops using Ubuntu 6.06 and a server using OpenBSD.  The computers are mainly used by students in Introductory level CS classes.  Most of the programming in the lab will be either C++ or python with Eclipse as the IDE.  We're looking to move away from the Macs for a few reasons:
[LIST][*]Using the HFS has given everyone in the lab headaches
[*]NFS does not work as advertised
[*]The documentation for NFS doesn't seem to exist for OS X 10.4
[*]No one at Apple seems to care about these issues[/LIST]
Almost all of the software we want to use (Eclipse, tkgate, etc.) is in the Ubuntu repositories, so that makes installing and upgrading simple.  After that it gets a little bit more complicated ... since we're going to have 10 identical setups, we want to properly configure 1 computer, and then copy that configuration over to the other 9.  What is the best way to “clone” one computer 9 times?  What about after the initial setup, do we have to do administer updates to each computer individually, or can we automate that as well?  Has anyone had experience setting up a Linux lab, specifically an Ubuntu lab?

We'd appreciate any comments.

Thanks!

---

### Post by gatekeep on 2006-06-01
i run the portion of a computing center at the local college where i am, what i have done is have the machines replicate the necessary settings from the server using boot-time shell scripts

as far as updates go, usually i just have a cron that runs an apt-get update every month

---

### Post by pclancy on 2006-06-01
Did you install Ubuntu on each machine individually, or did you automate that as well?

---

### Post by gatekeep on 2006-06-01
No, installed one machine, then used DD to duplicate one hard drive to another, took about 3 hours to complete a lab of about 15 machines (considering the drives are about 20gig a piece)

---

### Post by pclancy on 2006-06-01
[QUOTE=gatekeep]No, installed one machine, then used DD to duplicate one hard drive to another, took about 3 hours to complete a lab of about 15 machines (considering the drives are about 20gig a piece)[/QUOTE]
I'm sort of new to this, could you provide more specifics on how you did that?

Thanks!

---

### Post by gatekeep on 2006-06-01
basically, i took a new/erased/blank drive from one of the machines popped it into the installed box and used the dd command like this: "dd if=/dev/hda of=/dev/hdb" went through all the 14 hard drives using that method and volia whole lab by installing one machine

by the way, i didn't BOOT from the hard drive being copied, i used a terminal from the ubuntu livecd. this was to make sure neither drive was being "used" by anything on the computer, except the dd command

the other alternative is to get a hard drive duplicator...though not many places have one

---

### Post by pclancy on 2006-06-01
That sounds easy enough, thanks for the help!  Do you have any other suggestions or comments about the setup?

---

### Post by gatekeep on 2006-06-01
No, that about covers it, but if you come up with a better system then to use SFTP, FTP or TFTP to replicate the configuration throw it my way, because I've been trying to figure out a easier way to do it.

---

### Post by pclancy on 2006-06-02
I found a few good references that I thought I would share.

More on dd: [http://www.rajeevnet.com/hacks_hints/os_clone/os_cloning.html]("http://www.rajeevnet.com/hacks_hints/os_clone/os_cloning.html")

an Ubuntu forums thread on backing up and restoring: [http://www.ubuntuforums.org/showthread.php?t=35087]("http://www.ubuntuforums.org/showthread.php?t=35087")

---

### Post by Heavy-G on 2006-06-02
How about PXE booting a kernel which mounts an NFS share as its root filesystem?
That way every student could have his/her own account and log in onto every workstation with his/her login.

Another advantage is that (security) updates are a breeze to install. Just install them on one client, and all the other clients are updated immediately too.

I just finished a setup (with Debian, but it's quite the same for Ubuntu). A great howto can be found at [https://wiki.ubuntu.com/DisklessUbuntuHowto](https://wiki.ubuntu.com/DisklessUbuntuHowto)

---

### Post by pclancy on 2006-06-02
That's a fantastic idea, thanks for the suggestion!

---

### Post by aysiu on 2006-06-02
[QUOTE=pclancy]After that it gets a little bit more complicated ... since we're going to have 10 identical setups, we want to properly configure 1 computer, and then copy that configuration over to the other 9.  What is the best way to “clone” one computer 9 times?[/QUOTE] Use PartImage:
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

---

### Post by t3rror on 2006-06-02
Try SystemImager.

[http://www.systemimager.org/](http://www.systemimager.org/)

---

### Post by auburn on 2006-06-05
or use clonezilla to multicast the image to all the machines over the network:
[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

---

### Post by nephesh on 2006-06-05
Haven't tried it myself but I read an article on [www.linuxtoday.com](www.linuxtoday.com) about it.

Here's the article..

[http://www.enterprisenetworkingplanet.com/netos/article.php/3609831](http://www.enterprisenetworkingplanet.com/netos/article.php/3609831)


The systemimager one looks great though, so you may want to go with that.

---

### Post by pclancy on 2006-06-12
Are there any disadvantages to using my drives with XFS rather than Ext 3.  My understanding is defintely not complete, but it seems like XFS is pretty stable and significantly faster than Ext 3.  Any comments/suggestions?

---

### Post by pclancy on 2006-06-22
[QUOTE=t3rror]Try SystemImager.

[http://www.systemimager.org/](http://www.systemimager.org/)[/QUOTE]

We've finally got all of the computers built, and ready to go (except for the monitors which should be in soon), so I'm ready to try out SystemImager.  Has anyone used this with Ubuntu yet?  How did it go?

Thanks again for all of the suggestions.

---

### Post by pclancy on 2006-07-17
I thought I should update anyone who is intersted in my progress.  I settled on using PartImage for cloning, system imager was more than we needed.  Partimage was easy to use, and much, much faster than dd.

We have everything we wanted working great, and I think Ubuntu is going to be a big success in the lab.

I documented my work thoroughly while I built and setup the lab.  It's written with the howto style in mind, and it's far from being completed.  I'd appreciate any feedback.  
I have the pdf posted here: [http://students.haverford.edu/pclancy/howto/howto.pdf](http://students.haverford.edu/pclancy/howto/howto.pdf)
And the poorly converted html here: [http://students.haverford.edu/pclancy/howto/howto.htm](http://students.haverford.edu/pclancy/howto/howto.htm)

I'm going to fix the links, which are showing up as text in the near future.

Thanks again for all of your help.

---

### Post by auburn on 2006-07-17
pclancy:

 I read through your hardware specs. Did newegg give you an educational or bulk discount? Did they come down on the set shipping pricess any? I'm just curious. Don't divulge any info you're not supposed to.

---

### Post by pclancy on 2006-07-17
> **auburn said:**
> pclancy:

 I read through your hardware specs. Did newegg give you an educational or bulk discount? Did they come down on the set shipping pricess any? I'm just curious. Don't divulge any info you're not supposed to.

No, they didn't give us any discounts, but all but 3 pieces for the server were shipped in 1 business day even though we paid for the cheapest shipping they offered.  They were also incredibly helpful when we had to RMA a video card, they sent a replacement card out before they recieved our card for no cost.  Overall I was very pleased with newegg.

---

### Post by auburn on 2006-07-18
I just finished reading your howto. Very cool. I set up the ntp daemon and appreciated your lspci -v trick. I also figured out how to sync my work's win2k server with ntp servers. 

I work in a cyber cafe and have spent a lot of time customizing firefox profiles if you're interested...

I'll bet those monitors are awesome.

I also found some typos and I'll email them to you at your email.

thx for the all the documentation!

---

### Post by pclancy on 2006-07-18
> **auburn said:**
> I just finished reading your howto. Very cool. I set up the ntp daemon and appreciated your lspci -v trick. I also figured out how to sync my work's win2k server with ntp servers. 

All of my tricks were just tricks I found somewhere on the forums, but I'm glad I can pass it along.
> **auburn said:**
> 
I work in a cyber cafe and have spent a lot of time customizing firefox profiles if you're interested...

I'm very interested.
> **auburn said:**
> 
I'll bet those monitors are awesome.

That's by far the coolest part of our new lab.
> **auburn said:**
> 
I also found some typos and I'll email them to you at your email.

That would be fantastic, thanks!  Now I just have to figure out a few more things with texmacs, links and spell-checking, it shouldn't be too hard though.

---

