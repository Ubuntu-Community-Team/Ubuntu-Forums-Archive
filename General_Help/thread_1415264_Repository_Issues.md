---
title: "Repository Issues"
date: 2010-02-24
forum: General Help
---

### Post by Lyerae on 2010-02-24
I tried to install Tor yesterday, and now I'm trying to remove the repositories. I went to System > Administration > Software Sources and deleted the entries I added so I can get Tor, and now I'm getting this: [http://i50.tinypic.com/2qbx9wz.png](http://i50.tinypic.com/2qbx9wz.png) (error is on the screenshot).

Is there any way to fix that?

---

### Post by spiderbatdad on 2010-02-24
try running apt-get update after you manually edit sources.

---

### Post by Lyerae on 2010-02-24
I get this when I do that:

```

Get:1 http://dl.google.com stable Release.gpg [189B]
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Ign http://deb.torproject.org <DISTRIBUTION> Release.gpg                       
Ign http://deb.torproject.org <DISTRIBUTION>/main Translation-en_US            
Hit http://us.archive.ubuntu.com karmic Release.gpg                            
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US                 
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com karmic-security Release                         
Hit http://archive.canonical.com karmic Release                                
Ign http://deb.torproject.org <DISTRIBUTION> Release                           
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US             
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US           
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg                    
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US         
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US   
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US     
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US   
Hit http://us.archive.ubuntu.com karmic Release                                
Ign http://deb.torproject.org <DISTRIBUTION>/main Packages                     
Hit http://security.ubuntu.com karmic-security/main Packages                   
Hit http://archive.canonical.com karmic/partner Packages                       
Hit http://us.archive.ubuntu.com karmic-updates Release                        
Ign http://deb.torproject.org <DISTRIBUTION>/main Packages                     
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Err http://deb.torproject.org <DISTRIBUTION>/main Packages                     
  404  Not Found [IP: 88.198.151.34 80]
Hit http://us.archive.ubuntu.com karmic/main Packages                          
Hit http://us.archive.ubuntu.com karmic/restricted Packages          
Hit http://us.archive.ubuntu.com karmic/main Sources                 
Hit http://us.archive.ubuntu.com karmic/restricted Sources           
Hit http://us.archive.ubuntu.com karmic/universe Packages            
Hit http://security.ubuntu.com karmic-security/main Sources          
Hit http://security.ubuntu.com karmic-security/restricted Sources    
Hit http://security.ubuntu.com karmic-security/universe Packages     
Hit http://security.ubuntu.com karmic-security/universe Sources      
Hit http://security.ubuntu.com karmic-security/multiverse Packages   
Hit http://security.ubuntu.com karmic-security/multiverse Sources    
Hit http://us.archive.ubuntu.com karmic/universe Sources             
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
98% [Waiting for headers]


```

It get stuck at 98%.

However, these: 

```
Ign http://deb.torproject.org <DISTRIBUTION> Release.gpg                       
Ign http://deb.torproject.org <DISTRIBUTION>/main Translation-en_US 
Ign http://deb.torproject.org <DISTRIBUTION> Release
Ign http://deb.torproject.org <DISTRIBUTION>/main Packages 
Ign http://deb.torproject.org <DISTRIBUTION>/main Packages    
Err http://deb.torproject.org <DISTRIBUTION>/main Packages                     
  404  Not Found [IP: 88.198.151.34 80]                 

```

Those make me think I entered it wrong. How can I manually remove those (they don't know up in the sources list I went to).

---

### Post by Enigmapond on 2010-02-24
Yes they were input wrong and instead of "DISTRIBUTION" you should have changed that to karmic you can edit that in the software sources.

---

### Post by Lyerae on 2010-02-24
Yeah, that's my bad.
How do I fix it?

---

### Post by Enigmapond on 2010-02-24
System -> Administration -> Software Sources....find the tor line(s), hit edit and change it.

---

### Post by Lyerae on 2010-02-24
They don't show up in there.

---

### Post by Lyerae on 2010-02-24
Okay, I think I got it.
I had to navigate to "/etc/apt" and edit the list in gedit.

Seems to work so far.
I ran "sudo apt-get update", and it finishes correctly. So trace of the Tor repository. 


Thank guys!

---

### Post by Enigmapond on 2010-02-24
Here...this may help you. Better you learn this than me telling you what to do...give it a go..:)

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by nos09 on 2010-02-24
> **Lyerae said:**
> Okay, I think I got it.
I had to navigate to "/etc/apt" and edit the list in gedit.

Seems to work so far.
I ran "sudo apt-get update", and it finishes correctly. So trace of the Tor repository. 


Thank guys!

what did u do ?

---

### Post by Lyerae on 2010-02-25
> **nos09 said:**
> what did u do ?

I just said... I navigated to the list, and edited manually.

---

### Post by booshire on 2010-02-25
> **Lyerae said:**
> I just said... I navigated to the list, and edited manually.

Hey dude, it is in /etc/apt/sources.list. Comment out the line(s) or remove it.

---

