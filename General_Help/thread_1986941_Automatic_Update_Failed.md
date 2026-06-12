---
title: "Automatic Update Failed"
date: 2012-05-25
forum: General Help
---

### Post by chenxinghao on 2012-05-25
After being off line for about week and turned on Ubuntu early afternoon today and there was 72 some updates; clicked on Install All and a few seconds later, it says something to the tone of package download failed and asked to check the Internet connection. This never happened before since I installed Ubuntu 11.10 in January. Tried a couple more times, all failed with the same.

But the connection is fine, showing online videos with no problem.  What is going on?

---

### Post by matt_symes on 2012-05-25
Hi

Open a terminal and type

```
sudo apt-get update
```

Post the output back here (select text in terminal->right click->copy) and paste into your next post between code tags like this

[noparse]```
output
```[/noparse]

to get output like this

```
output
```

Kind regards

---

### Post by chenxinghao on 2012-05-25
Here is the output in Terminal:

~$ sudo apt-get update
[sudo] password for chenxinghao: 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports InRelease
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg [198 B]
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                      
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg [198 B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release [40.8 kB]         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                 
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]       
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release.gpg [198 B]       
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release [40.8 kB]            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                    
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources [37.8 kB]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release [40.8 kB]           
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports Release [40.8 kB]        
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources [1,959 B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources [17.3 kB]  
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources [877 kB]              
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources [1,644 B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages [121 kB] 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US                    
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages [3,939 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages [37.3 kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages [3,371 B]
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex [73 B]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex [72 B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex [71 B]
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex [73 B]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en [57.5 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en [26.0 kB]
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources [5,351 B] 
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources [4,677 kB]
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources [149 kB]        
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages [1,226 kB]      
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages [8,216 B] 
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages [4,468 kB]  
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages [119 kB]  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex             
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources [141 kB]      
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources [3,347 B]
Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources [54.5 kB] 
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources [3,660 B]
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages [353 kB]
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages [6,631 B]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages [116 kB]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [6,363 B]
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex [74 B]
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [72 B]
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [72 B]
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex [73 B]
Get:44 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Sources [2,742 B]   
Get:45 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Sources [14 B]
Get:46 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Sources [9,019 B]
Get:47 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Sources [14 B]
Get:48 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main i386 Packages [3,296 B]
Get:49 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted i386 Packages [14 B]
Get:50 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe i386 Packages [13.4 kB]
Get:51 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages [14 B]
Get:52 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main TranslationIndex [72 B]
Get:53 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex [70 B]
Get:54 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex [70 B]
Get:55 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe TranslationIndex [73 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en               
Get:56 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en [160 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Get:57 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en [1,547 B]
Get:58 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en [69.9 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/main Translation-en         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/multiverse Translation-en   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/restricted Translation-en   
Get:59 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-backports/universe Translation-en [11.8 kB]
Fetched 13.0 MB in 36s (357 kB/s)                                              
Reading package lists... Done
~$

---

### Post by matt_symes on 2012-05-25
Hi

That looks fine. From the terminal type

```
sudo apt-get install htop
```

Post back the output.

Kind regards

---

### Post by chenxinghao on 2012-05-25
I used the Software Up to Date in the system tools place and the update went through complete.

What am I missing in the early failure?

Do I need to run any clean-up in the Terminal (so to remove the manual downloads)?

Thanks.

---

### Post by matt_symes on 2012-05-25
Hi

> **chenxinghao said:**
> I used the Software Up to Date in the system tools place and the update went through complete.

What am I missing in the early failure?

Do I need to run any clean-up in the Terminal (so to remove the manual downloads)?

Thanks.

Not quite sure what happened to be honest. Not enough information as the update worked correctly and there were no error messages.

It could be a whole number of things that caused the problem but if it's working now i would not worry.

You do not need to run any commands to delete the manual downloads as that was just updating your system.

Kind regards

---

### Post by chenxinghao on 2012-05-25
Sorry for newbie's question - I am not used to manual commands.

How do I clean up the manual downloads?

---

### Post by matt_symes on 2012-05-25
Hi

> **chenxinghao said:**
> Sorry for newbie's question - I am not used to manual commands.

How do I clean up the manual downloads?

Don't worry about the command

```
sudo apt-get update
```

as that would have been run in the background by update manager. That's how it knows you had updates.

To remove htop (if you installed it) type

```
sudo apt-get remove htop
```

Kind regards

---

### Post by chenxinghao on 2012-05-25
Thanks.

---

