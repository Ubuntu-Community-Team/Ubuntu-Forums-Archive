---
title: "I love Ubuntu, but...."
date: 2010-01-24
forum: General Help
---

### Post by tripower on 2010-01-24
I would love to dump most of my Windows boxes in favor of Ubuntu but I am a little weary.
My concerns are the following:

1. I can live without most of my Windoze software but there are a couple of programs that I may need to have. I looked at Wine but  I am not sure how this works or if it works with all Win installs. Do I actually run my win install and install the win app on my Ubuntu box?

2. I can see my Windows 7 workgroup along with the boxes but everytime I try to connect I get the following error "Unable to mount location" - "Failed to retrieve share list from server". I have tried everything including creating a share on the Windows box with full permissions. (Oh, the boxes that I cannot connect to are Win 7 64 bit, I can actually connect to my Win XP 32 bit box).

3. Will I be able to use all of my files that I have created on on my Windows machines whether 32bit or 64bit?

4. I am actually a MS developer. Is there any way to run SQL Server with Ubuntu?

---

### Post by ppirilla on 2010-01-24
Despite what many zealots here will say, Linux is not, in fact, the end-all, be-all answer to the operating system debate.

If you have particular pieces of proprietary software that you absolutely need in order to work, chances are you should stick with Windows.

If you need software to perform a specific function, but are willing to switch the particular program, tell us what you need (and what you currently use to do it) and someone may be able to point you to a Linux-friendly alternative.


Windows 7 tends not to get along well with anything that is not Windows 7 from my experience.  Someone else may have found a workaround, but I'm still looking.


You will certainly be able to transfer any files you create in Windows to an Ubuntu machine.  If you will be able to use them depends on the first question.


Finally, MySQL is open source and is quite happy to run in Ubuntu.

---

### Post by lykwydchykyn on 2010-01-24
> **tripower said:**
> I would love to dump most of my Windows boxes in favor of Ubuntu but I am a little weary.
My concerns are the following:

1. I can live without most of my Windoze software but there are a couple of programs that I may need to have. I looked at Wine but  I am not sure how this works or if it works with all Win installs. Do I actually run my win install and install the win app on my Ubuntu box?

In theory, you install the windows software in Ubuntu using wine; no Windows install involved.  In practice, Wine doesn't often work.  Emulating the entire Windows API is a bit tricky, and it's far from flawless.

Unless the software demands high performance, using a virtual machine running Windows is usually produces better results.
> 
2. I can see my Windows 7 workgroup along with the boxes but everytime I try to connect I get the following error "Unable to mount location" - "Failed to retrieve share list from server". I have tried everything including creating a share on the Windows box with full permissions. (Oh, the boxes that I cannot connect to are Win 7 64 bit, I can actually connect to my Win XP 32 bit box).

Can't help you there, I haven't messed with Windows 7.  I've heard of others having problems working with file sharing between win7 and ubuntu.
> 
3. Will I be able to use all of my files that I have created on on my Windows machines whether 32bit or 64bit?

What sort of files?  I don't think data is affected by architecture.  The question is whether or not you have an application that will open them.
> 
4. I am actually a MS developer. Is there any way to run SQL Server with Ubuntu?

No.  Microsoft don't play that.

You can connect to SQL Server using odbc, and there's a command-line shell called sqsh, but mostly the tools are very thin.

---

### Post by LoneWolfJack on 2010-01-24
1.
yes

2.
AFAIK, ubuntu doesn't yet have a driver for the new windows file format

3.
files don't care whether they are opened one a 32 or 64 bit system, it's the application that matters

4.
most likely not. also, if you are a MS developer I fail to see the point on why you would use linux on your development box

---

### Post by baddog144 on 2010-01-24
I'm somewhat confused as to why you would be running Linux on a development machine if you're an MS developer :/

Linux is not so fantastic that it is worthwhile jumping through all the hoops that you will inevitably face trying to get a usable MS dev system up and running :(

---

### Post by tripower on 2010-01-24
Also, Can I remote desktop from and to a Windows box via Ubuntu?

---

### Post by Saiko Berry on 2010-01-24
If you are an MS developer, the world just made sense to me.

---

### Post by lykwydchykyn on 2010-01-24
> **tripower said:**
> Also, Can I remote desktop from and to a Windows box via Ubuntu?

Yes.

rdesktop, or one of its graphical front-ends (tsclient or krdc,maybe others) will let you connect to Windows.

You can set up an RDP server on Ubuntu, xrdp.  I've never tried it personally, so I can't vouch for how well it works.  There are probably better methods to connect to Ubuntu, such as Nomachine NXserver, or if your LAN connection is reasonably fast VNC.

---

### Post by hemimaniac on 2010-01-24
> **Saiko Berry said:**
> If you are an MS developer, the world just made sense to me.

Well, im still a little confused? :-k

---

### Post by tripower on 2010-02-05
The apps that I periodically need to run but cannot are:
- Tax software (like TurboTax)
- OBDII software
- Ebay Turbo Lister

I also have been unable to connect to my Windows 7 boxes with either via my home network or remote desktop.

---

### Post by tripower on 2010-02-06
I want to convert more computers to Ubuntu but I just get the feeling that this OS is not ready for primetime. I need to be able to do basic networking tasks with my computers.

---

### Post by lykwydchykyn on 2010-02-06
> **tripower said:**
> I want to convert more computers to Ubuntu but I just get the feeling that this OS is not ready for primetime. I need to be able to do basic networking tasks with my computers.

What can you not do?  Rdesktop has always worked fine for me, though Windows 7 is probably the only version of Windows I haven't tried it with.

---

### Post by switch10 on 2010-02-06
> **tripower said:**
> The apps that I periodically need to run but cannot are:
- Tax software (like TurboTax)
- OBDII software
- Ebay Turbo Lister

I also have been unable to connect to my Windows 7 boxes with either via my home network or remote desktop.

you could always run these programs in a virtual machine with windows installed.

Wine may run them as well

---

### Post by dolphinaura on 2010-02-06
> **tripower said:**
> I would love to dump most of my Windows boxes in favor of Ubuntu but I am a little weary.
My concerns are the following:

1. I can live without most of my Windoze software but there are a couple of programs that I may need to have. I looked at Wine but  I am not sure how this works or if it works with all Win installs. Do I actually run my win install and install the win app on my Ubuntu box?

**2. I can see my Windows 7 workgroup along with the boxes but everytime I try to connect I get the following error "Unable to mount location" - "Failed to retrieve share list from server". I have tried everything including creating a share on the Windows box with full permissions. (Oh, the boxes that I cannot connect to are Win 7 64 bit, I can actually connect to my Win XP 32 bit box).**

[B]3. Will I be able to use all of my files that I have created on on my Windows machines whether 32bit or 64bit?

4. I am actually a MS developer. Is there any way to run SQL Server with Ubuntu[/B]?

2. [s]I just saw a thread a few minutes ago about this, let me see if I can dig it back up.
[/s]
[http://ubuntuforums.org/showthread.php?t=10841703](http://ubuntuforums.org/showthread.php?t=10841703)
3. No 64-bit, but 32 bit, fine.
4. [s]dont know what that is. ill ask carlee in a few seconds since shes MCITP certified.[/s]

you cant run MS SQL in WINE or ubuntu. you will either have to run it in a VM or dual boot (reccomended).
However, if you can take some time to convert to MYSQL, then it would work in ubuntu.
See this for more info: [http://dev.mysql.com/tech-resources/articles/migrating-from-microsoft.html](http://dev.mysql.com/tech-resources/articles/migrating-from-microsoft.html)

I actually advise you to dual boot instead of wiping out windows - it will save you some misery if you ever really need to use windows.

---

### Post by tripower on 2010-02-08
> **dolphinaura said:**
> 2. [s]I just saw a thread a few minutes ago about this, let me see if I can dig it back up.
[/s]
[http://ubuntuforums.org/showthread.php?t=10841703](http://ubuntuforums.org/showthread.php?t=10841703)
3. No 64-bit, but 32 bit, fine.
4. [s]dont know what that is. ill ask carlee in a few seconds since shes MCITP certified.[/s]

you cant run MS SQL in WINE or ubuntu. you will either have to run it in a VM or dual boot (reccomended).
However, if you can take some time to convert to MYSQL, then it would work in ubuntu.
See this for more info: [http://dev.mysql.com/tech-resources/articles/migrating-from-microsoft.html](http://dev.mysql.com/tech-resources/articles/migrating-from-microsoft.html)

I actually advise you to dual boot instead of wiping out windows - it will save you some misery if you ever really need to use windows.


I like the idea of porting my db over to mysql. What are my options for hosting a .NET web app with ubuntu? Apache/Mono?

---

### Post by lykwydchykyn on 2010-02-08
> **tripower said:**
> I like the idea of porting my db over to mysql. What are my options for hosting a .NET web app with ubuntu? Apache/Mono?

There's a mono module for apache that is supposed to support ASP.NET.  I haven't tried it, but from what I hear it works fine.  It's in the repository.

You might want to look at Postgresql also; it has a feature set more in line with what MS SQL offers, as far as embedded functions, procedural SQL, transactions, etc.  I started developing with it a few years ago and never looked back.

---

