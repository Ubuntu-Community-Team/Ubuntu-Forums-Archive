---
title: "update manager error message"
date: 2009-09-11
forum: General Help
---

### Post by oponto on 2009-09-11
Hey,

I got an update manager error message in my 9.04.

Here the screenshots:

Around update process left message comes up, after clicking "run action now", second message comes up and then only closing those windows manually remains.

[IMG]http://img40.imageshack.us/img40/5358/screenshot12cm.png[/IMG]

lala thanks
tamtamtam :D

---

### Post by dearingj on 2009-09-11
Looks like you haven't added the gpg key for Opera's repository. Run this in the terminal (I just got this off of [http://deb.opera.com](http://deb.opera.com)):

```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -

```

---

### Post by imhotep59 on 2009-09-11
This message means 2 things:
- Firstly, you have not the public key for the repository. You have to find this key and then to add it. However this does not block the download of the package. It is only an information
- Secondly, it indicates that the repository is unavailable. Check if you have indicated the right repository. If so, it is possible that this repository is temporarily unavailable. Try later.

---

### Post by oponto on 2009-09-11
Didn't work to do so.

But the tip appeared pretty good to me, because I installed Opera 10 manually before the repository was updated to the latest version. What to do to get the opera 10 "version" from the repository ? Maybe that solves the prob. ?

---

### Post by Soul-Sing on 2009-09-11
Imho the -apt authentication issue- message is a rather new protocol. I have never seen it before, but after a recent security
update I got it also on my screen, and also related to opera.

---

### Post by imhotep59 on 2009-09-12
The message related to the public key is frequent. As I said it means that you need to download this public key to "authenticate" the repository but this doesn't block the download. I previously had it with other packages (bibus etc...) and it was corrected after I obtained the public key. 
The second message is the most important one: obviously the repository for the .deb is false or broken.
To install the key and the repository from debian, which work with Ubuntu, you can try:
```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```
Then add the repository for Opera beta
```
deb http://deb.opera.com/opera-beta/ sid non-free
```
Here are the details for this repository and its key:
[http://deb.opera.com/]("http://deb.opera.com/")

(I don't use Opera, please verify which version it will download before installing)

---

### Post by oponto on 2009-09-13
```
deb
``` is not a command ?
I tried it with apt-get instead, but no way.

First I have to wait until ubuntu starts auto-update, because I think manually the error doesn't always appear.

---

### Post by philinux on 2009-09-13
> **oponto said:**
> ```
deb
``` is not a command ?
I tried it with apt-get instead, but no way.

First I have to wait until ubuntu starts auto-update, because I think manually the error doesn't always appear.

You need to add that repo like this not run the thing as a command.
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by oponto on 2009-09-13
> **philinux said:**
> You need to add that repo like this not run the thing as a command.
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Oh yeah, now the error does not appear anymore !

However, update manager downloads about 60 packages, which subsequently just don't appear for installation ?

---

### Post by philinux on 2009-09-13
Run this and post the output back.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by oponto on 2009-09-15
After restarting and auto- and manual- updating processes, those 60 packages don't appear anymore, everything works or at least seams fine now.
_______________________
_______________________
however, let us look if that command shows something still strange:

> **philinux said:**
> Run this and post the output back.

```
sudo apt-get update && sudo apt-get upgrade
```

> Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Translation-en_US                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty/main Translation-en_US                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release                                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty/universe Translation-en_US             
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty/multiverse Translation-en_US           
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty-updates/main Translation-en_US         
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US   
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty-updates/universe Translation-en_US     
Ign [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US   
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty Release                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty/main Packages                              
Hit [http://deb.opera.com](http://deb.opera.com) sid Release.gpg                                       
Ign [http://deb.opera.com](http://deb.opera.com) sid/non-free Translation-en_US                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty-updates Release              
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_US           
Hit [http://deb.opera.com](http://deb.opera.com) sid Release                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages     
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty/main Packages                
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty/restricted Packages          
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty/main Sources                 
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty/restricted Sources           
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty/universe Packages            
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources    
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty/universe Sources             
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty-updates/restricted Sources
Ign [http://deb.opera.com](http://deb.opera.com) sid/non-free Packages 
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://at.archive.ubuntu.com](http://at.archive.ubuntu.com) jaunty-updates/multiverse Sources
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Hit [http://deb.opera.com](http://deb.opera.com) sid/non-free Packages
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


is it ok^^ ?

---

