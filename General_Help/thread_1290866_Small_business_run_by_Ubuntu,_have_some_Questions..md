---
title: "Small business run by Ubuntu, have some Questions.."
date: 2009-10-14
forum: General Help
---

### Post by StaticIp on 2009-10-14
Hello all, I am setting up my small business with Ubuntu. The server will act as a web host and file server. 

Specs:
     Hard Drives: 1.5tb partitioned as 500gb for / , 1gb for swap and the rest for /home (personal use)

                   1tb for customers data and websites(database, sites, etc)

                   1tb as a hot swap for on the go (we got this so when we went out to set up clients equipment we could take files and back up their previous systems)

     Processor: Intel Core 2 Quad Q9550 2.83ghz Socket 775 1333MHz

     Motherboard: GIGABYTE GA-EP45T-UD3LR LGA 775 Intel P45 ATX Intel Motherboard

     Power supply: OCZ StealthXStream OCZ700SXS-B 700W ATX12V

     RAM: G.SKILL 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) Dual Channel

     Case: COOLER MASTER COSMOS 1000 RC-1000-KSN1-GP Black/ Silver Steel ATX Full Tower Computer Case (Pics attached)

The parts will be here in about 5 days, it will be running Ubuntu Jaunty with LAMP for my web server and Citadel for my groupware. I have a domain name through godaddy and what I would like to know is if I could set up my mail server in a way to have my own personal email address eg. "something@godaddydomain.com". 
Any other suggestions would be very welcome. I have everything figures out for the most part, but not having another human here in person to toss ideas around is starting to take its toll. So if you would be so kind as to help me on my way through getting my small business up and running with ubuntu?

---

### Post by beastrace91 on 2009-10-14
Do you have a reason for having such a large / partition? Typically 20 gigs is over kill unless you plan on storing files here for some odd reason xD

~Jeff

---

### Post by StaticIp on 2009-10-14
Oh that, I plan to keep many small archived backups or misc information. I've had to repartion my / before and it sucked. I'd like to avoid that as much as possible lol.

---

### Post by hal10000 on 2009-10-14
> I plan to keep many small archived backups or misc information

I suggest to have a small root partition (~20-30GB) and a separate partition for your archives. Such a big root partition makes the system slow down.

Also, i would give swap a little bit more space (about as much as your installed RAM size), if you have a webserver or databases running they could benefit from that, especially if they have many users at the same time.

> what I would like to know is if I could set up my mail server in a way to have my own personal email address eg. "something@godaddydomain.com".

Yes, you can. Use postfix or sendmail and read their documentation.

btw., if you have many mails or other variable data like databases, dynamic web pages etc., you may create a separate partition for your /var directory (20 GB should be enough unless you have really big databases)

---

### Post by beastrace91 on 2009-10-14
> **hal10000 said:**
> I suggest to have a small root partition (~20-30GB) and a separate partition for your archives. Such a big root partition makes the system slow down.

Second that one - thats what storage partitions are for :)

~Jeff

---

### Post by StaticIp on 2009-10-14
I will definetly do that now, thanks for the advice.

---

### Post by kanikilu on 2009-10-14
> **hal10000 said:**
> Such a big root partition makes the system slow down. Sorry to the OP, I don't mean to hijack the thread, but do you have anything to substantiate that claim? I'm not challenging you on it, I've just never heard that before, and I'm genuinely curious.

---

### Post by StaticIp on 2009-10-14
I am also wondering, anything to make my system just that much faster.

---

### Post by Giblet5 on 2009-10-14
> **beastrace91 said:**
> Second that one - thats what storage partitions are for :)

~Jeff

Yeah, but some of us create massive /tmp files...

500GB is about right if you do a lot of CAD/Blender work, or run a medium-scale email server...or occasionally compile really crappy code that some pointy-headed dweeb named Josh wrote.

I've got 220GB used on / right now w/ a 6TB RAID 1/0 /home...

---

### Post by Lars Noodén on 2009-10-14
> **StaticIp said:**
> ... if I could set up my mail server in a way to have my own personal email address eg. "something@godaddydomain.com". ...

What mail server are you using?  I guess the default for citadel would be the package citadel-mta, so that is where the addressing could be changed.

The mail client can set the address on the way out.  That should be done anyway.  

Might want to check into setting proper MX records, maybe including using godaddy's mail as a reserver, so that if there is a hiccup in the net or your hardware, the mail just gets spooled.

---

### Post by hal10000 on 2009-10-14
> Yeah, but some of us create massive /tmp files...

500GB is about right if you do a lot of CAD/Blender work, or run a medium-scale email server...or occasionally compile really crappy code that some pointy-headed dweeb named Josh wrote

That's the reason why i would create a separate /var partition, because your mails usually reside in /var and depending on the apps and the purpose of the server also would create a /tmp and/or /usr partition. Generally you can say that your system has smaller seek and access time if you have a small root partition. The effect is not too big when using a desktop-system, but in a server environment it may get a significant speed-up.

The better you know the purpose of your server, the better you can customize your partitioning. As an example, if your server is planned to be an appplication server, you should create a /usr partition, if you mainly compile your own packages and don't use the package manager to install your apps, then you could create a /usr/local partition because such stuff goes usually to /usr/local. If you have a database with heavy load and/or many users you will create a big swap partition and /var.

---

