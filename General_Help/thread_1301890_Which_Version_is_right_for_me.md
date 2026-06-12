---
title: "Which Version is right for me?"
date: 2009-10-26
forum: General Help
---

### Post by knwminus on 2009-10-26
Greetings All:

I am building a computer (for the first time) and I am trying to decided which OS to install. Let me give you some background about myself:

I am a Noc Tech, focused on studying networking, especially cisco certs (this machine is for GNS3 as well as a general desktop) and linux. I have some experience (very basic) in Ubuntu and I plan to dive deep into the *nix world (ubuntu, redhat/centos,and unix in particular). I would like to get my knowledge to admin level in a year or two. 


At any rate my specs for my new box
I7 processor
8 GB DDR3
a Few 500 gb hdds
Quadport Nic
etc...

As I stated above this machine will be used for gns3, remote access (I plan to use open vpn from my work machine to my house since I have a static ip) and general linux studies. I would like to know if I should go for the Desktop 9.04 or Server 8.10 LTS? Which would be better for new comers to cuts there teeth on? I know eventually (in a few weeks  or months) I want to move all of my machines to Linux but I will need Samba because as it stands now, my wife is using a Vista based laptop. Also does anyone here have any experience using gns3 on ubuntu? I am using it on several windows machines but I have not moved any of them over to ubuntu yet.


Thanks,

knwminus

---

### Post by rockstarrem on 2009-10-26
I'd wait until Thursday and get the 9.10 Desktop edition.

---

### Post by knwminus on 2009-10-26
> **rockstarrem said:**
> I'd wait until Thursday and get the 9.10 Desktop edition.

Is there a reason to use to the desktop edition over the server edition?

---

### Post by abyrne on 2009-10-26
Well the server edition is just a console, no GUI. I think that diving straight into a console is a bit much for a newcomer. I'd try Desktop 9.10 first, and then you can grow from there. Good luck!

---

### Post by Meskarune on 2009-10-26
Install arch linux. Its better than ubuntu.

---

### Post by marshmallow1304 on 2009-10-26
Make sure to get the 64-bit edition so you can utilize all that RAM.

---

### Post by knwminus on 2009-10-26
> **Meskarune said:**
> Install arch linux. Its better than ubuntu.

Care to explain what you mean my "better"? Easier to learn? Easier to work in? Easier for the needs I am going to have? Better system utilization?

---

### Post by knwminus on 2009-10-26
> **marshmallow1304 said:**
> Make sure to get the 64-bit edition so you can utilize all that RAM.

Oh yea mos def. I am not *that* big of a newb.;) 

But you do bring up another point. Hardware drivers maybe harder to come by for 64 bit Ubuntu.

---

### Post by zzzBrett on 2009-10-26
I would agree with the previous poster to start with either Ubuntu 9.10 or Kubuntu 9.10 and get a handle on the environment first.  From my experience, you will get a fair amount of terminal-exposure even with a gui like gnome or kde.  You should be able to run all of the server apps, and everything you would normally do with the server edition.

As far as the drivers, I run 64 bit and have experienced very few instances where a driver was not available.

Good luck.

---

### Post by Meskarune on 2009-10-26
> **knwminus said:**
> Care to explain what you mean my "better"? Easier to learn? Easier to work in? Easier for the needs I am going to have? Better system utilization?

All of the above?

---

### Post by ext3 on 2009-10-26
If your experience is limited you can start out with the Desktop version, but If you seriously want to be at and Admin level in a year or two then I would have to say go with the Server edition.

---

### Post by knwminus on 2009-10-27
> **ext3 said:**
> If your experience is limited you can start out with the Desktop version, but If you seriously want to be at and Admin level in a year or two then I would have to say go with the Server edition.

I might make to move to a gui less world at the end of the year.

---

### Post by mick55 on 2009-10-27
Hi knwminus

Ubuntu or Linux Mint are great choices for someone new to Linux.

As far as Desktop vs Server goes, you need a desktop
environment if you want to actually use your computer
and learn Linux.

But, if you have an old PC lying around, set it up as a server.
The requirements for a server are much lower since it doesn't need a GUI.
My Server runs fine on a PIII 600 with 192 MB RAM.

Arch is a lot of fun to set up and play around with, but you have 
to know what you're doing or it gets frustrating very quickly,
and if you want a REAL challenge try Gentoo.

Cheers
mick

---

### Post by marshmallow1304 on 2009-10-27
> **knwminus said:**
> Oh yea mos def. I am not *that* big of a newb.;) 

But you do bring up another point. Hardware drivers maybe harder to come by for 64 bit Ubuntu.

I guess I overestimated your newbness. :redface:

I can't think of any reason to not use a full GUI with those specs.  You can switch to tty1 and kill your DE to force yourself to learn CLI and you can go nuts trying out different distros (including server editions) in a VM.

Setting up Server Edition on an older machine is a good idea as well.

---

### Post by knwminus on 2009-10-27
> **mick55 said:**
> Hi knwminus

Ubuntu or Linux Mint are great choices for someone new to Linux.

As far as Desktop vs Server goes, you need a desktop
environment if you want to actually use your computer
and learn Linux.

But, if you have an old PC lying around, set it up as a server.
The requirements for a server are much lower since it doesn't need a GUI.
My Server runs fine on a PIII 600 with 192 MB RAM.

Arch is a lot of fun to set up and play around with, but you have 
to know what you're doing or it gets frustrating very quickly,
and if you want a REAL challenge try Gentoo.

Cheers
mick

Thanks for the suggestions. I think Ubuntu will be my choice for now. I have never heard of Mint but I have heard Gentoo can be a real pain. One of my professors told me he gave up one it at some point. 
  For the time being I want to focus on Ubuntu/RH/Cent/Solaros to help further my current job. As far as certs: L+/LPIC-1/RHCE/SCXXX are in my future along with some other non *nix certs (CCNA, CCNA:S, Security+,CCNP,CWNA) to help with my networking degree.

As far as Ubuntu Server, I have a box or 2 I can use for Ubuntu/CentOS servers hopefully to interact with my existing windows boxes but that is further down the road.

---

### Post by knwminus on 2009-10-27
deleted

---

### Post by knwminus on 2009-10-27
> **marshmallow1304 said:**
> I guess I overestimated your newbness. :redface:

I can't think of any reason to not use a full GUI with those specs.  You can switch to tty1 and kill your DE to force yourself to learn CLI and you can go nuts trying out different distros (including server editions) in a VM.

Setting up Server Edition on an older machine is a good idea as well.

The reason why they are so hard core is my machine is going to be used for GNS3 and I want to run CCIE level labs (10-15 routers plus) without my machine dying.  

VMs are going to be something I invest some time into more heavily. I use virtual box now for my work machine (XP host/Ubuntu Guest).

---

