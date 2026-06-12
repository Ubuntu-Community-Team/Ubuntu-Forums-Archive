---
title: "Unable to load updates..please help!"
date: 2012-03-18
forum: General Help
---

### Post by oxf on 2012-03-18
Please can someone help me!

I am trying to run Update Manager and load the updates. 
I get an error message saying "unable to load updates" and "check your internet connection"
which is silly because I am connected and am posting this question right now!

When I look at the details it seem it's unable to find the web site and there are a lot of 404 errors. I don't understand this since I've updated before without problem. 
Maybe something has got changed in the Software Sources settings?
It looks alright to me but I may well have missed something and am not an expert!

So can someone advise me what I should check to get the updates working again.

Thanks
Katya

---

### Post by matt_symes on 2012-03-19
Hi

Open a terminal (press ctrl + alt + t) and type

```
sudo apt-get update
```

Enter your password. It will not be echoed to the screen.

Post the output back here by copying from the terminal (highlight text->right click->copy) and paste it into your next post between code tags like this

[noparse]```
output
```[/noparse]

to get output like this

```
output
```

Kind regards

---

### Post by oxf on 2012-03-19
Ok thanks!
Heres what I got:

```

mbdb@Acer:~$ sudo apt-get update
[sudo] password for mbdb: 
Get:1 http://security.ubuntu.com maverick-security Release.gpg [198B]
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
Get:2 http://archive.canonical.com maverick Release.gpg [198B]                 
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick Release.gpg                          
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
Get:3 http://archive.canonical.com maverick Release [5,925B]                   
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_GB 
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB 
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Hit http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB   
Get:4 http://gb.archive.ubuntu.com maverick-updates Release.gpg [198B]         
Get:5 http://security.ubuntu.com maverick-security Release [39.8kB]            
Get:6 http://extras.ubuntu.com maverick Release.gpg [72B]                      
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en              
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick Release                            
Ign http://extras.ubuntu.com/ubuntu/ maverick/main Translation-en_GB           
Hit http://extras.ubuntu.com maverick Release                                  
Get:7 http://gb.archive.ubuntu.com maverick-updates Release [39.8kB]           
Get:8 http://archive.canonical.com maverick/partner Sources [3,865B]         
Get:9 http://archive.canonical.com maverick/partner i386 Packages [6,416B]     
Hit http://gb.archive.ubuntu.com maverick/main Sources                         
Hit http://gb.archive.ubuntu.com maverick/restricted Sources                   
Hit http://gb.archive.ubuntu.com maverick/universe Sources                     
Hit http://gb.archive.ubuntu.com maverick/multiverse Sources                   
Hit http://gb.archive.ubuntu.com maverick/main i386 Packages                   
Hit http://gb.archive.ubuntu.com maverick/restricted i386 Packages             
Get:10 http://security.ubuntu.com maverick-security/main Sources [105kB]       
Hit http://gb.archive.ubuntu.com maverick/universe i386 Packages            
Hit http://gb.archive.ubuntu.com maverick/multiverse i386 Packages          
Hit http://extras.ubuntu.com maverick/main Sources     
Get:11 http://gb.archive.ubuntu.com maverick-updates/main Sources [178kB]
Hit http://extras.ubuntu.com maverick/main i386 Packages                       
Get:12 http://security.ubuntu.com maverick-security/restricted Sources [14B]   
Get:13 http://security.ubuntu.com maverick-security/universe Sources [33.3kB]  
Get:14 http://gb.archive.ubuntu.com maverick-updates/restricted Sources [778B] 
Get:15 http://gb.archive.ubuntu.com maverick-updates/universe Sources [64.0kB] 
Get:16 http://security.ubuntu.com maverick-security/multiverse Sources [1,755B]
Get:17 http://security.ubuntu.com maverick-security/main i386 Packages [328kB] 
Get:18 http://gb.archive.ubuntu.com maverick-updates/multiverse Sources [2,513B]
Get:19 http://gb.archive.ubuntu.com maverick-updates/main i386 Packages [465kB]
Get:20 http://security.ubuntu.com maverick-security/restricted i386 Packages [14B]
Get:21 http://security.ubuntu.com maverick-security/universe i386 Packages [114kB]
Get:22 http://security.ubuntu.com maverick-security/multiverse i386 Packages [4,026B]
Get:23 http://gb.archive.ubuntu.com maverick-updates/restricted i386 Packages [1,797B]
Get:24 http://gb.archive.ubuntu.com maverick-updates/universe i386 Packages [201kB]
Get:25 http://gb.archive.ubuntu.com maverick-updates/multiverse i386 Packages [5,475B]
Fetched 1,602kB in 4s (337kB/s)                         
Reading package lists... Done
mbdb@Acer:~$ 


```

---

### Post by plucky on 2012-03-19
No errors,now run ```
sudo apt-get upgrade
``` and post output.

Good luck

---

### Post by oxf on 2012-03-19
Well I think I've fixed it...

I compared my laptop with someone elses also running Ubuntu, i.e the "Software Sources" in the Upadate Manager.

I added the "deb.. Maverick free-non free source  and tried again and then it  updated.
The only thing I don't understand is how I managed to update before or how that line got removed? I didn't do it!

Anyway thanks for the ideas.

Katya

---

