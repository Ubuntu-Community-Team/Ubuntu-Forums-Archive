---
title: "Constant error when installing..."
date: 2009-12-28
forum: General Help
---

### Post by ][_, {[]} ][_, on 2009-12-28
Ok every time I try to install something from the Ubuntu Software Center I get the same error message:
```

Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.
```Why does this keep popping up and how can I stop it?

*I am the admin on the computer and I always put the correct password in when it asks for it during installation.

So please help as soon as possible.  Thx 4 your time.

---

### Post by oldos2er on 2009-12-28
You're missing gpg keys for one or more repositories. If you run **sudo apt-get update** in a terminal, it should tell you which repositories are missing keys.

---

### Post by ][_, {[]} ][_, on 2009-12-29
Then what do I do?  This is what I got after I typed what you said to in terminal...

```
Ign http://archive.canonical.com karmic Release.gpg
Ign http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://us.archive.ubuntu.com karmic Release.gpg                            
Ign http://archive.canonical.com karmic/partner Translation-en_US              
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US           
Ign http://archive.canonical.com karmic Release                                
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US     
Ign http://archive.canonical.com karmic/partner Packages                       
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US             
Ign http://archive.canonical.com karmic/partner Packages                       
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US           
Err http://archive.canonical.com karmic/partner Packages                       
  400  Bad Request
Ign http://security.ubuntu.com karmic-security Release                         
Ign http://us.archive.ubuntu.com karmic-updates Release.gpg
Ign http://security.ubuntu.com karmic-security/main Packages
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://security.ubuntu.com karmic-security/restricted Packages
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security/main Sources
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/restricted Sources              
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US   
Ign http://security.ubuntu.com karmic-security/universe Packages         
Ign http://us.archive.ubuntu.com karmic Release                          
Ign http://security.ubuntu.com karmic-security/universe Sources          
Ign http://us.archive.ubuntu.com karmic-updates Release                  
Ign http://security.ubuntu.com karmic-security/multiverse Packages       
Ign http://us.archive.ubuntu.com karmic/main Packages                    
Ign http://security.ubuntu.com karmic-security/multiverse Sources              
Ign http://us.archive.ubuntu.com karmic/restricted Packages                    
Ign http://security.ubuntu.com karmic-security/main Packages                   
Ign http://us.archive.ubuntu.com karmic/main Sources                           
Ign http://security.ubuntu.com karmic-security/restricted Packages             
Ign http://us.archive.ubuntu.com karmic/restricted Sources                     
Ign http://security.ubuntu.com karmic-security/main Sources              
Ign http://us.archive.ubuntu.com karmic/universe Packages                
Ign http://security.ubuntu.com karmic-security/restricted Sources        
Ign http://us.archive.ubuntu.com karmic/universe Sources
Ign http://security.ubuntu.com karmic-security/universe Packages
Ign http://us.archive.ubuntu.com karmic/multiverse Packages
Ign http://security.ubuntu.com karmic-security/universe Sources
Ign http://us.archive.ubuntu.com karmic/multiverse Sources
Ign http://security.ubuntu.com karmic-security/multiverse Packages
Ign http://us.archive.ubuntu.com karmic-updates/main Packages            
Ign http://security.ubuntu.com karmic-security/multiverse Sources              
Ign http://us.archive.ubuntu.com karmic-updates/restricted Packages            
Err http://security.ubuntu.com karmic-security/main Packages
  400  Bad Request
Ign http://us.archive.ubuntu.com karmic-updates/main Sources             
Err http://security.ubuntu.com karmic-security/restricted Packages             
  400  Bad Request
Ign http://us.archive.ubuntu.com karmic-updates/restricted Sources             
Err http://security.ubuntu.com karmic-security/main Sources                    
  400  Bad Request
Ign http://us.archive.ubuntu.com karmic-updates/universe Packages              
Err http://security.ubuntu.com karmic-security/restricted Sources              
  400  Bad Request
Ign http://us.archive.ubuntu.com karmic-updates/universe Sources               
Err http://security.ubuntu.com karmic-security/universe Packages               
  400  Bad Request
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Packages            
Err http://security.ubuntu.com karmic-security/universe Sources                
  400  Bad Request
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Sources             
Err http://security.ubuntu.com karmic-security/multiverse Packages             
  400  Bad Request
Ign http://us.archive.ubuntu.com karmic/main Packages                          
Err http://security.ubuntu.com karmic-security/multiverse Sources        
  400  Bad Request
Ign http://us.archive.ubuntu.com karmic/restricted Packages
Ign http://us.archive.ubuntu.com karmic/main Sources
Ign http://us.archive.ubuntu.com karmic/restricted Sources
Ign http://us.archive.ubuntu.com karmic/universe Packages
Ign http://us.archive.ubuntu.com karmic/universe Sources
Ign http://us.archive.ubuntu.com karmic/multiverse Packages
Ign http://us.archive.ubuntu.com karmic/multiverse Sources
Ign http://us.archive.ubuntu.com karmic-updates/main Packages
Ign http://us.archive.ubuntu.com karmic-updates/restricted Packages
Ign http://us.archive.ubuntu.com karmic-updates/main Sources
Ign http://us.archive.ubuntu.com karmic-updates/restricted Sources
Ign http://us.archive.ubuntu.com karmic-updates/universe Packages
Ign http://us.archive.ubuntu.com karmic-updates/universe Sources
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Err http://us.archive.ubuntu.com karmic/main Packages
  400  Bad Request
Err http://us.archive.ubuntu.com karmic/restricted Packages
  400  Bad Request
Err http://us.archive.ubuntu.com karmic/main Sources
  400  Bad Request
Err http://us.archive.ubuntu.com karmic/restricted Sources
  400  Bad Request
Err http://us.archive.ubuntu.com karmic/universe Packages
  400  Bad Request
Err http://us.archive.ubuntu.com karmic/universe Sources
  400  Bad Request
Err http://us.archive.ubuntu.com karmic/multiverse Packages
  400  Bad Request
Err http://us.archive.ubuntu.com karmic/multiverse Sources
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-updates/main Packages
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-updates/restricted Packages
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-updates/main Sources
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-updates/restricted Sources
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-updates/universe Packages
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-updates/universe Sources
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-updates/multiverse Packages
  400  Bad Request
Err http://us.archive.ubuntu.com karmic-updates/multiverse Sources
  400  Bad Request
W: Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/partner/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz  400  Bad Request

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz  400  Bad Request

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz  400  Bad Request

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz  400  Bad Request

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz  400  Bad Request

E: Some index files failed to download, they have been ignored, or old ones used instead.
```[B]
[/B]
What's up with the bad requests and errors?

---

### Post by oldos2er on 2009-12-29
Are you behind a proxy? Or having problems with your internet connection?

You could try changing servers, if you haven't already.

---

### Post by ][_, {[]} ][_, on 2009-12-30
> **oldos2er said:**
> Are you behind a proxy? Or having problems with your internet connection?

You could try changing servers, if you haven't already.

I'm not behind a proxy or vpn and my internet connection is strong. Right now I'm using ubuntu along-side with vista (in a dual-boot).  Could that be causing the problem?

---

### Post by oldos2er on 2009-12-30
No, dual booting shouldn't cause a problem. Have you tried a different server? System, Administration, Software Sources, click the bar nest to 'Download from:', Other, Select Best Server.

---

### Post by ][_, {[]} ][_, on 2009-12-30
> **oldos2er said:**
> No, dual booting shouldn't cause a problem. Have you tried a different server? System, Administration, Software Sources, click the bar nest to 'Download from:', Other, Select Best Server.

Ok I tried switching from the "Server for United States" to the "Main Server" but when I did that I got the following error:

```
Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch http://archive.canonical.com/ubuntu/dists/karmic/partner/binary-i386/Packages.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/main/binary-i386/Packages.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/binary-i386/Packages.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/main/source/Sources.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/restricted/source/Sources.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/universe/binary-i386/Packages.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/universe/source/Sources.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/binary-i386/Packages.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic/multiverse/source/Sources.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/main/source/Sources.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/source/Sources.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/binary-i386/Packages.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/source/Sources.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/binary-i386/Packages.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/binary-i386/Packages.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/main/source/Sources.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/restricted/source/Sources.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/binary-i386/Packages.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/universe/source/Sources.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/binary-i386/Packages.gz  400  Bad Request
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/karmic-security/multiverse/source/Sources.gz  400  Bad Request
Some index files failed to download, they have been ignored, or old ones used instead.


```
Here lemme show you some screenshots of my software sources and you could tell me if they are correct...

[IMG]http://i45.tinypic.com/hv3293.jpg
[IMG]http://i48.tinypic.com/28hmxch.png
[IMG]http://i50.tinypic.com/2irngv5.png
[IMG]http://i49.tinypic.com/21ep0ye.png
[IMG]http://i45.tinypic.com/4l6l9g.png

Well thx for your time so far...  if you need to see any screenshots of anything else to help me further just say so.

---

### Post by Evie~ on 2010-01-13
Bump, I have the same problem :(

---

### Post by DannStarr on 2010-01-22
The following fixed it for me:


```
sudo apt-get clean
```

```
cd /var/lib/apt
```

```
sudo mv lists lists.old
```

```
sudo mkdir -p lists/partial
```

```
sudo apt-get clean
```

```
sudo apt-get update
```

---

