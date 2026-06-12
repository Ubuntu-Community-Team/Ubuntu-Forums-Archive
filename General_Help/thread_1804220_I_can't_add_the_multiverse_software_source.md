---
title: "I can't add the multiverse software source"
date: 2011-07-14
forum: General Help
---

### Post by Thelinuxgeek on 2011-07-14
There's lots of programs I want to install via the Ubuntu software center (for example, Glest.) However when i go to install it, it says it's available from the Multiverse source, so I click on ''use this source'' and every time I do that I get this error:

W:Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_binary-i386_Packages  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.

I tried to add the Multiverse source through Synaptic but it says it's already being used. What should I do? Thanks in advance.

---

### Post by matt_symes on 2011-07-14
Hi

Open a terminal and type 

```
sudo apt-get update
```

Enter your password. It will not be echoed to the screen.

Please copy and paste the results back here.

Kind regards

---

### Post by Thelinuxgeek on 2011-07-14
> **matt_symes said:**
> Hi

Open a terminal and type 

```
sudo apt-get update
```Enter your password. It will not be echoed to the screen.

Please copy and paste the results back here.

Kind regards

Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg            
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                      
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release                           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                   
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages [238 kB]     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
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
Fetched 1 B in 14s (0 B/s)                                                     
W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.


Odd, the same error. o.0

---

### Post by matt_symes on 2011-07-14
Hi

Hmmm. You have just blown a theory i had out of the water.

Anyways; to fix the issue, at the terminal copy and paste these commands.

```
sudo rm -rf /var/lib/apt/lists/*
```

and then

```
sudo apt-get update
```

Kind regards

---

### Post by Thelinuxgeek on 2011-07-14
> **matt_symes said:**
> Hi

Hmmm. You have just blown a theory i had out of the water.

Anyways; to fix the issue, at the terminal copy and paste these commands.

```
sudo rm -rf /var/lib/apt/lists/*
```and then

```
sudo apt-get update
```Kind regards

Ok it downloaded 13 MB out of i think 202 MB of updates (it's a recent install I haven't dpwnloaded any updates until now) and now I get this very interesting error:

brainstorm@Flappy:~$ sudo apt-get update
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease             
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]              
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]            
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg [316 B]                       
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg [198 B]                   
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [27.2 kB]              
Get:6 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release [9,753 B]                         
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg [316 B]                       
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg [198 B]           
Get:9 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release [9,762 B]                         
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release [39.8 kB]                    
Get:11 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release [9,730 B]                        
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [59.2 kB]        
Get:13 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources [14 B]                      
Get:14 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources [1,601 B]                   
Get:15 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages [3,200 B]             
Get:16 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages [14 B]                
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Get:17 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Sources [1,430 B]                   
Get:18 [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main i386 Packages [1,646 B]             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main TranslationIndex                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release [27.2 kB]            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en_US          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) natty/main Translation-en              
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources [862 kB]                
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]     
Get:22 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [7,103 B]    
Get:23 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [658 B]    
Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages [153 kB]   
Get:25 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages [14 B]
Get:26 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages [22.0 kB]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages [2,074 B]
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
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources [4,104 B]         
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources [4,380 kB]          
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources [155 kB]          
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages [1,550 kB]        
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages [1,550 kB]        
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages [8,986 B]   
99% [32 Packages bzip2 0 B] [33 Packages 3,969 B/8,986 B 44%]      6,715 B/s 0s
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Get:34 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages [6,021 kB]    
Get:35 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages [183 kB]    
99% [35 Packages bzip2 0 B] [Waiting for headers]                  6,405 B/s 0s
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Get:36 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages [275 kB]  
Get:37 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages [14 B]
Get:38 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages [68.4 kB]
Get:39 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages [4,267 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex       
Get:40 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources [117 kB]        
Get:41 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources [20 B]    
Get:42 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources [19.6 kB]   
Get:43 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources [1,719 B] 
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
Fetched 13.7 MB in 43min 10s (5,293 B/s)
W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty_multiverse_binary-i386_Packages  Hash Sum mismatch

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by matt_symes on 2011-07-14
Hi

I must say i did not expect that output. Can i have a look at your sources.list file.

Please post the output of 

```
cat /etc/apt/sources.list
```Also try another mirror while waiting for my reply.

What i don't like about these errors...
> 
W: Failed to fetch  gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty_main_bina   ry-i386_Packages  Hash Sum mismatch

W: Failed to fetch  gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_natty_multivers   e_binary-i386_Packages  Hash Sum mismatch....is the spaces in the two of them (bina ry, mulltivers e). That may be an artifact but i want to check. Your post above shows them better.

Kind regards

---

### Post by wildmanne39 on 2011-07-14
Hi, try this 
```
sudo rm  /var/lib/apt/lists/partial/*
```
```
sudo apt-get update
```

---

### Post by Thelinuxgeek on 2011-07-15
> **wildmanne39 said:**
> Hi, try this 
```
sudo rm  /var/lib/apt/lists/partial/*
``````
sudo apt-get update
```

Wow, THANKS! It's working now! what does that do anyway?

---

### Post by wildmanne39 on 2011-07-16
> **Thelinuxgeek said:**
> Wow, THANKS! It's working now! what does that do anyway?Hi, it deletes the partial list that is causing the problem. The only time that list is created is when you have an update that was only partly successful,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by matt_symes on 2011-07-16
Hi

@wildmanne39. That was an excellent call and good judgment :P

I am confused though. Do you have any idea why 

```
sudo rm -rf /var/lib/apt/lists/*
```did not work and 

```
sudo rm  /var/lib/apt/lists/partial/*
```did ?

The first rm command is a traversal of the file system under /var/lib/apt/lists and should have deleted partial/ and it contents as well as the contents of lists/ and so should have achieved what the second command also achieved :confused:

Any idea's why it did not work ?

Kind regards

---

### Post by wildmanne39 on 2011-07-16
Hi, I know it should remove it from the way it looks but it does not I can not explain it. I do know that the partial list is only created when you have an updates that are only partly successful and I have used this command to get rid of it several times.

---

