---
title: "Problem with Ubuntu Software Center"
date: 2011-11-06
forum: General Help
---

### Post by saichand on 2011-11-06
I am facing problem with "Ubuntu Software Center", it doesn't show any results when I searched for any software, it keeps on searching for hours together. Any solution to overcome this

---

### Post by Rubi1200 on 2011-11-06
Hi and welcome to the forums :)

Since this does not appear to be a Wubi-specific issue, moved to own thread.

Try and be more specific about the problem and what you have done to try and solve it.

---

### Post by saichand on 2011-11-06
Hi Rubi1200,

When I click on "Ubuntu Software Center" it opens and displays the category's, till here it is fine & normal. When I try to search for any software or when I click on any category like Games or Utilities it simply keeps on searching for hours together and displays nothing. I tried restarting and I am using Ubuntu installed inside windows(Wubi).

Please help me as I am starter in Ubuntu and fell in love with it just after using it for few hours.

---

### Post by saichand on 2011-11-06
I have also assured that my internet is working fine and I am able to open all other website in Firefox.

---

### Post by cllewis91592 on 2011-11-06
hello, i would recommend doing a full install of ubuntu and not use wubi as a full time thing. wubi is meant to be used to test different things about ubuntu. 

sorry i cant help any more then this :(

---

### Post by cllewis91592 on 2011-11-06
if you need help there are plenty of guides on how to duel boot on the net

[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony) here is the way i did it and works fine with 11.10 or any other distro of ubuntu(or any other linux distro)

---

### Post by saichand on 2011-11-06
Hi cllewis91592,

At  this point I can't think of installing ubuntu on full I need some time for that.

Is this the only reason I am facing this problem? Is anyone in this forum successfully able to run Ubuntu on Wubi

Regards
SaiChand T

---

### Post by cllewis91592 on 2011-11-06
> **saichand said:**
> Hi cllewis91592,

At  this point I can't think of installing ubuntu on full I need some time for that.

Is this the only reason I am facing this problem? Is anyone in this forum successfully able to run Ubuntu on Wubi

Regards
SaiChand T
well if you ever warm up to the idea then you can always remove it very easy if you dont like it. i currently have windows 7 and ubuntu 11.10 dual booted on my hard drive. i currently only use ubuntu for all my needs now, havnt needed windows for about a month now :guitar: 

but i keep it there just in case.

---

### Post by vasa1 on 2011-11-06
> **saichand said:**
> Hi cllewis91592,

At  this point I can't think of installing ubuntu on full I need some time for that.

Is this the only reason I am facing this problem? Is anyone in this forum successfully able to run Ubuntu on Wubi

Regards
SaiChand T

I feel that this an important aspect and needs to be clarified. I never went the Wubi way, but if not being able to use the USC is a limitation of Wubi, it should be made clear in a Readme or even more prominently.

So far, I haven't come across mention of this limitation in casual reading.

---

### Post by Rubi1200 on 2011-11-06
I don't believe this is a problem because of Wubi.

Open a terminal using Ctrl+Alt+T and run the following commands:

```
sudo dpkg --configure -a

sudo apt-get update
```

When asked for your password, type as normal even though the output won't be echoed.

If these commands produce error messages, post them here so we can try and figure out what is going on.

---

### Post by saichand on 2011-11-06
Hi Rubi1200,

I have done the same way below is the error message.

------------------------------------------------------------------------------------------------------------------------------
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

saichand@ubuntu:~$ sudo dpkg --configure -a
[sudo] password for saichand: 
Sorry, try again.
[sudo] password for saichand: 
saichand@ubuntu:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg [198 B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [31.4 kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg [198 B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release [39.8 kB]          
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [75.4 kB]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release [31.4 kB]             
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources [862 kB]     
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [13.3 kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [661 B]    
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages [210 kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages [14 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages [52.1 kB]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages [2,064 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en          
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources [4,104 B]         
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources [4,380 kB]          
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources [155 kB]          
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages [1,550 kB]        
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages [8,986 B]   
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages [6,021 kB]    
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages [183 kB]    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources [138 kB]        
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources [753 B]   
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources [30.4 kB]   
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources [2,317 B] 
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages [404 kB]  
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages [839 B]
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages [117 kB]
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages [5,081 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en         
Fetched 14.3 MB in 3min 57s (60.2 kB/s)                                        
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
saichand@ubuntu:~$

------------------------------------------------------------------------------------------------------------------------------

:sad: :sad: :sad: :sad: :sad:

---

### Post by Rubi1200 on 2011-11-07
Open a terminal and try these commands:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

The first command removes corrupted package lists so please type carefully or better still copy and paste. The second command refreshes the lists.

Hopefully, this should solve the issue.

---

### Post by saichand on 2011-11-07
Hi Rubi1200,

Thanks for the help the problem was solved. I have un-installed the old version which I was using and installed "ubuntu-11.10-desktop-i386" version this is working for fine for me.

Now I have got a new problem, track pad on my laptop is not working but external USB mouse is working any idea on how to make track pad work.

I am using "Lenovo Ideapad" I tried to adjust the track pad settings in **system settings** but it is still not working.

---

