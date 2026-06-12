---
title: "Software Center won't let me install or update unautenticated sources."
date: 2010-12-11
forum: General Help
---

### Post by ninjaaron on 2010-12-11
It's weird. I have to do all my unauthenticated stuff with synaptic or apt-get.

It is especially infuriating because all the programs still appear in the the lists, updates still appear in the updated manager. Can I set my software center and update manager to allow unauthenticated sources?

One of the updates was for firefox, and another was for empathy. It was weird. I think I even see the authentication codes for these sources in my thing, but...

Just what is going on here?

---

### Post by sikander3786 on 2010-12-11
Go to Applications > Accessories > Terminal and post the output of this command.

```
sudo apt-get update
```

While posting, click the # icon in post menu and paste your text in between teh generated code tags.

---

### Post by ninjaaron on 2010-12-15
```
Get:1 http://il.archive.ubuntu.com maverick Release.gpg [198B]
Ign http://il.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://il.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Ign http://il.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en 
Ign http://il.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://il.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://il.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://il.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Get:2 http://extras.ubuntu.com maverick Release.gpg [65B]                      
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://il.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US
Get:3 http://il.archive.ubuntu.com maverick-updates Release.gpg [198B]
Ign http://il.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://il.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://il.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://il.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://il.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://il.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Get:4 http://security.ubuntu.com maverick-security Release.gpg [198B]
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en  
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_US 
Hit http://extras.ubuntu.com maverick Release                        
Ign http://il.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://il.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://il.archive.ubuntu.com maverick Release
Get:5 http://il.archive.ubuntu.com maverick-updates Release [31.4kB]           
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release                     
Hit http://extras.ubuntu.com maverick/main Sources                           
Hit http://extras.ubuntu.com maverick/main i386 Packages                     
Hit http://il.archive.ubuntu.com maverick/main Sources                       
Hit http://il.archive.ubuntu.com maverick/restricted Sources
Hit http://il.archive.ubuntu.com maverick/universe Sources
Hit http://il.archive.ubuntu.com maverick/multiverse Sources
Hit http://il.archive.ubuntu.com maverick/main i386 Packages
Hit http://il.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://il.archive.ubuntu.com maverick/universe i386 Packages
Hit http://il.archive.ubuntu.com maverick/multiverse i386 Packages
Get:6 http://il.archive.ubuntu.com maverick-updates/main Sources [49.2kB]
Hit http://security.ubuntu.com maverick-security/main Sources
Hit http://security.ubuntu.com maverick-security/restricted Sources            
Hit http://security.ubuntu.com maverick-security/universe Sources              
Hit http://security.ubuntu.com maverick-security/multiverse Sources            
Hit http://security.ubuntu.com maverick-security/main i386 Packages            
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages      
Hit http://security.ubuntu.com maverick-security/universe i386 Packages        
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages      
Get:7 http://il.archive.ubuntu.com maverick-updates/restricted Sources [14B]   
Get:8 http://il.archive.ubuntu.com maverick-updates/universe Sources [19.7kB]  
Get:9 http://il.archive.ubuntu.com maverick-updates/multiverse Sources [1,068B]
Get:10 http://il.archive.ubuntu.com maverick-updates/main i386 Packages [132kB]
Get:11 http://il.archive.ubuntu.com maverick-updates/restricted i386 Packages [14B]
Get:12 http://il.archive.ubuntu.com maverick-updates/universe i386 Packages [66.3kB]
Get:13 http://il.archive.ubuntu.com maverick-updates/multiverse i386 Packages [2,522B]
Fetched 302kB in 16s (18.2kB/s)                                                
Reading package lists... Done

```

---

### Post by sikander3786 on 2010-12-16
There are no errors whatsoever in your output.

Can you tell us which software are you trying to install and getting that error so we can find from which repository it is coming from?

---

### Post by ninjaaron on 2010-12-16
> **sikander3786 said:**
> There are no errors whatsoever in your output.

Can you tell us which software are you trying to install and getting that error so we can find from which repository it is coming from?

Today it was tff-linux-libertine, a font pack.

---

### Post by sikander3786 on 2010-12-16
I think that package is not in the official repositories for Ubuntu. Not sure though.

Anyhow, go to Software Center > Edit > Software Sources and change your download server to Main server. Then try from the terminal and post the output of this command.

```
sudo apt-get install tff-linux-libertine
```

---

### Post by ninjaaron on 2010-12-17
> **sikander3786 said:**
> I think that package is not in the official repositories for Ubuntu. Not sure though.

Anyhow, go to Software Center > Edit > Software Sources and change your download server to Main server. Then try from the terminal and post the output of this command.

```
sudo apt-get install tff-linux-libertine
```

Pretty sure it will tell me that it's already installed... since it is... via that very command.

However when I did install it (not having added the main server to my sources), I had to push "y" because it was unauthenticated.

---

### Post by sikander3786 on 2010-12-18
> **ninjaaron said:**
> Pretty sure it will tell me that it's already installed... since it is... via that very command.

However when I did install it (not having added the main server to my sources), I had to push "y" because it was unauthenticated.
So you mean even after changing your Server to 'Main', the error message is still there?

---

### Post by Gr3ghammett on 2011-04-30
Recently I've started having this issue when it comes to installing anything from ubuntu software center. i checked everything, and have done sudo apt-get update && sudo apt-get upgrade several times, and still have this issue. my server is still set for Main Server. Any guidance further guidance is appreciated.

---

### Post by lonniehenry on 2011-04-30
If you go to synaptic and remove lintian, then the software center will let you install any package from non-ubuntu or non-debian sources.  Lintian is a debian package checker and is installed by default to prevent unauthorized or unverified packages from being installed.  You don't need this program if you are sure of the source of the package that you install is reliable.

---

### Post by sikander3786 on 2011-05-01
> **Gr3ghammett said:**
> Recently I've started having this issue when it comes to installing anything from ubuntu software center. i checked everything, and have done sudo apt-get update && sudo apt-get upgrade several times, and still have this issue. my server is still set for Main Server. Any guidance further guidance is appreciated.
Can you please post the complete output of 'sudo apt-get update && sudo apt-get upgrade' for us to take a look.

---

### Post by oldos2er on 2011-05-01
aptitude, apt-get, or Synaptic will allow you to install packages from an unauthenticated source. But the best long-term solution is to authenticate repositories, see [https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

---

