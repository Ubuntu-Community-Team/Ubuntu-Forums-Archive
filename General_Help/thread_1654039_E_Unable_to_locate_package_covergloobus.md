---
title: "E: Unable to locate package covergloobus"
date: 2010-12-27
forum: General Help
---

### Post by TheNerdAL on 2010-12-27
I'm trying to install Covergloobus but it says it's not able to find it. :( 

Can anyone help me? 

It gives me this: ```
adrian@adrian-desktop:~$ sudo apt-get install covergloobus
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package covergloobus

```

---

### Post by SpadeIV on 2010-12-28
Do you have the repositories enabled?

sudo add-apt-repository ppa:gloobus-dev/gloobus-preview
sudo add-apt-repository ppa:gloobus-dev/covergloobus

---

### Post by TheNerdAL on 2010-12-28
> **SpadeIV said:**
> Do you have the repositories enabled?

sudo add-apt-repository ppa:gloobus-dev/gloobus-preview
sudo add-apt-repository ppa:gloobus-dev/covergloobus

Yeah, it does the same thing.

---

### Post by yetiman64 on 2010-12-28
> **TheNerdAL said:**
> Yeah, it does the same thing.
After installing the 2 ppas listed above you may have to run ```
sudo apt-get update
``` before the programs become available to the Package manager.

Just tried that here and covergloobus is now available for install in Synaptic (it wasn't there at all before).

Hope this is of some help, good luck.

---

### Post by TheNerdAL on 2010-12-28
> **yetiman64 said:**
> After installing the 2 ppas listed above you may have to run ```
sudo apt-get update
``` before the programs become available to the Package manager.

Just tried that here and covergloobus is now available for install in Synaptic (it wasn't there at all before).

Hope this is of some help, good luck.

Nope same thing. I might just do a fresh install.

---

### Post by wojox on 2010-12-28
Your going to do a fresh install on a ppa I told you to untick in Software Sources > Other Software last night?

---

### Post by TheNerdAL on 2010-12-28
> **wojox said:**
> Your going to do a fresh install on a ppa I told you to untick in Software Sources > Other Software last night?

I did that and then followed SpadeIV's steps and I got the same thing.

---

### Post by wojox on 2010-12-28
> **TheNerdAL said:**
> I did that and then followed SpadeIV's steps and I got the same thing.

So you re-enabled them and ran:

```
sudo apt-get update
```

And it doesn't show it.

---

### Post by TheNerdAL on 2010-12-28
> **wojox said:**
> So you re-enabled them and ran:

```
sudo apt-get update
```

And it doesn't show it.

Doesn't show any errors when updating but when I try installing covergloobus it says the same thing.

```
adrian@adrian-desktop:~$ sudo apt-get update
Hit http://linux.dropbox.com maverick Release.gpg
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en              
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_US           
Hit http://linux.dropbox.com maverick Release                                  
Get:1 http://dl.google.com stable Release.gpg [197B]                           
Ign http://apt.boxee.tv maverick Release.gpg                                   
Hit http://linux.dropbox.com maverick/main i386 Packages                       
Ign http://apt.boxee.tv/ maverick/main Translation-en                          
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en          
Hit http://us.archive.ubuntu.com maverick Release.gpg                          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_US       
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://dl.google.com/linux/chrome/deb/ stable/main Translation-en_US       
Get:2 http://download.tuxfamily.org  Release.gpg [198B]                        
Ign http://apt.boxee.tv/ maverick/main Translation-en_US                       
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en    
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en      
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu/ maverick/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_US   
Hit http://us.archive.ubuntu.com maverick-security Release.gpg                 
Hit http://us.archive.ubuntu.com maverick-updates Release.gpg                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en  
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_US
Hit http://security.ubuntu.com maverick-security Release                       
Ign http://apt.boxee.tv maverick Release                                       
Get:3 http://dl.google.com stable Release.gpg [197B]                           
Ign http://download.tuxfamily.org/gericom/libreoffice/  Translation-en         
Ign http://download.tuxfamily.org/gericom/libreoffice/  Translation-en_US      
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en      
Ign http://apt.boxee.tv maverick/main i386 Packages/DiffIndex                  
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release.gpg                              
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-proposed Release.gpg                 
Hit http://security.ubuntu.com maverick-security/universe i386 Packages        
Hit http://apt.boxee.tv maverick/main i386 Packages                            
Ign http://dl.google.com/linux/talkplugin/deb/ stable/main Translation-en_US   
Get:4 http://download.tuxfamily.org  Release [724B]                            
Get:5 http://dl.google.com stable Release [1,347B]                             
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ maverick/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release.gpg                              
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en 
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/main Translation-en_US
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-proposed/universe Translation-en_US
Hit http://us.archive.ubuntu.com maverick-backports Release.gpg                
Hit http://security.ubuntu.com maverick-security/main i386 Packages            
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages      
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages      
Get:6 http://dl.google.com stable Release [1,347B]                             
Ign http://download.tuxfamily.org  Packages                                    
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                        
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/multiverse Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en
Ign http://us.archive.ubuntu.com/ubuntu/ maverick-backports/universe Translation-en_US
Get:7 http://dl.google.com stable/main i386 Packages [1,076B]                  
Ign http://download.tuxfamily.org  Packages                                    
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                        
Hit http://us.archive.ubuntu.com maverick Release                              
Hit http://us.archive.ubuntu.com maverick-security Release                     
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick Release                                  
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main Sources                             
Get:8 http://dl.google.com stable/main i386 Packages [735B]                    
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main Sources                   
Hit http://ppa.launchpad.net maverick/main Sources                   
Get:9 http://download.tuxfamily.org  Packages [7,260B]               
Hit http://us.archive.ubuntu.com maverick-updates Release                     
Hit http://us.archive.ubuntu.com maverick-proposed Release                    
Hit http://us.archive.ubuntu.com maverick-backports Release                   
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main i386 Packages                       
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main Sources                             
Hit http://ppa.launchpad.net maverick/main Sources                            
Hit http://us.archive.ubuntu.com maverick/universe Sources                    
Hit http://us.archive.ubuntu.com maverick/main Sources                        
Hit http://us.archive.ubuntu.com maverick/restricted Sources                  
Hit http://us.archive.ubuntu.com maverick/multiverse Sources                  
Hit http://us.archive.ubuntu.com maverick/universe i386 Packages              
Hit http://us.archive.ubuntu.com maverick/main i386 Packages                  
Hit http://ppa.launchpad.net maverick/main Sources                            
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://ppa.launchpad.net maverick/main i386 Packages
Hit http://ppa.launchpad.net maverick/main Sources
Hit http://us.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-security/universe Sources
Hit http://us.archive.ubuntu.com maverick-security/main Sources
Hit http://us.archive.ubuntu.com maverick-security/restricted Sources
Hit http://us.archive.ubuntu.com maverick-security/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-updates/universe Sources
Hit http://us.archive.ubuntu.com maverick-updates/main Sources
Hit http://us.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://us.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-proposed/universe Sources
Hit http://us.archive.ubuntu.com maverick-proposed/main Sources
Hit http://us.archive.ubuntu.com maverick-proposed/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-proposed/restricted Sources
Hit http://us.archive.ubuntu.com maverick-proposed/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-proposed/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-proposed/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-proposed/restricted i386 Packages
Hit http://us.archive.ubuntu.com maverick-backports/universe Sources
Hit http://us.archive.ubuntu.com maverick-backports/main Sources
Hit http://us.archive.ubuntu.com maverick-backports/multiverse Sources
Hit http://us.archive.ubuntu.com maverick-backports/restricted Sources
Hit http://us.archive.ubuntu.com maverick-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com maverick-backports/main i386 Packages
Hit http://us.archive.ubuntu.com maverick-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com maverick-backports/restricted i386 Packages
Fetched 13.1kB in 1s (6,624B/s)
Reading package lists... Done

```

---

### Post by wojox on 2010-12-28
I see it calls it but Ignores the files. When you reactivated them in Software Sources when you close out does it ask you if you want to refresh or update the list?

---

### Post by TheNerdAL on 2010-12-28
> **wojox said:**
> I see it calls it but Ignores the files. When you reactivated them in Software Sources when you close out does it ask you if you want to refresh or update the list?

I never reactivated them. I used the terminal to add them. But when I close out it refreshes itself.

---

### Post by wojox on 2010-12-28
What is gloobus anyhow? 

Here go back into Software Sources > Other Software and delete all instances of gloobus. Then open a terminal

```
gksudo gedit /etc/apt/sources.list
```

And add

```

deb http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu maverick main 
deb-src http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu maverick main 

```

Then run 

```
sudo apt-get update; sudo apt-get upgrade
```

There is no sudo add-apt-repository ppa:gloobus-dev/covergloobus for above Karmic.

---

### Post by TheNerdAL on 2010-12-28
> **wojox said:**
> What is gloobus anyhow? 

Here go back into Software Sources > Other Software and delete all instances of gloobus. Then open a terminal

```
gksudo gedit /etc/apt/sources.list
```

And add

```

deb http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu maverick main 
deb-src http://ppa.launchpad.net/gloobus-dev/gloobus-preview/ubuntu maverick main 

```

Then run 

```
sudo apt-get update; sudo apt-get upgrade
```

There is no sudo add-apt-repository ppa:gloobus-dev/covergloobus for above Karmic.

Ohhh, so what you are saying is that the line I used can't be used for 10.10? 

And it does the same thing.

---

### Post by wojox on 2010-12-28
> **TheNerdAL said:**
> Ohhh, so what you are saying is that the line I used can't be used for 10.10? 

And it does the same thing.

You removed all traces of gloobus from Software Sources > Other Software?

Right

```
ppa:gloobus-dev/covergloobus
```

Doesn't work.

---

### Post by TheNerdAL on 2010-12-28
> **wojox said:**
> You removed all traces of gloobus from Software Sources > Other Software?

Right

```
ppa:gloobus-dev/covergloobus
```

Doesn't work.

Yes I did.

---

### Post by wojox on 2010-12-28
Actually I just found a ppa for Lucid at Launchpad for this. 

What does this do

```
sudo apt-get update && sudo apt-get install gloobus-preview 
```

---

### Post by TheNerdAL on 2010-12-28
So I can't install Covergloobus on 10.10? O.o 

If not, I have a similiar issue trynig to install True Combat: Elite.

I followed these steps: [http://ubuntuforums.org/showpost.php?p=10063534&postcount=4](http://ubuntuforums.org/showpost.php?p=10063534&postcount=4) 

But when I do the 4th step, I get this.

```
E: Unable to locate package enemy-territory

```

It's getting annoying now. :/

---

### Post by TheNerdAL on 2010-12-28
> **wojox said:**
> Actually I just found a ppa for Lucid at Launchpad for this. 

What does this do

```
sudo apt-get update && sudo apt-get install gloobus-preview 
```

I already have gloobus preview. I'm trying to install Covergloobus.

---

### Post by wojox on 2010-12-28
Have you had Covergloobus running in 10.10?

---

### Post by TheNerdAL on 2010-12-28
> **wojox said:**
> Have you had Covergloobus running in 10.10?

Yes I had it from 10.04 I believe then I upgraded to 10.10 but it crashed the last time I started it and froze my whole computer.

---

### Post by wojox on 2010-12-28
> **TheNerdAL said:**
> Yes I had it from 10.04 I believe then I upgraded to 10.10 but it crashed the last time I started it and froze my whole computer.

Yeah, they don't have a 10.10 package built yet. So I guess you will be doing that fresh install after all. :p

---

### Post by TheNerdAL on 2010-12-28
> **wojox said:**
> Yeah, they don't have a 10.10 package built yet. So I guess you will be doing that fresh install after all. :p

It's not worth it no more. :P But I want to install True Combat: Elite but it says the same error. D: I wonder if they have a 10.10 package built.

---

### Post by TheNerdAL on 2010-12-28
Can you help me? :(

---

### Post by mc4man on 2010-12-28
the covergloobus package for lucid does work in 10.10 (at least most 10.10 installs), either edit the entry(s) in software sources changing the Distribution from maverick to lucid 
Or just go to the ppa's package page and dl and install the .deb directly

[https://launchpad.net/~gloobus-dev/+archive/covergloobus/+packages](https://launchpad.net/~gloobus-dev/+archive/covergloobus/+packages)

If may or may not work on your install

(using the proposed repo as a matter of course generally isn't the best idea

---

