---
title: "Google Chrome is not trusted software"
date: 2011-11-08
forum: General Help
---

### Post by MrsCogan on 2011-11-08
I can't install literally anything because I get the message "untrusted software." 

is there a secret handshake I'm overlooking?

---

### Post by fantab on 2011-11-08
> **MrsCogan said:**
> I can't install literally anything because I get the message "untrusted software." 

is there a secret handshake I'm overlooking?

Welcome to the Forums!

I usually have this kind of issue when I install software that is not in the repositories or in the Software-Center.

How are you trying to install Google Chrome? Is it a .deb package that you are trying to install via Software Center?
If it is then just ignore the warning and go ahead and install.

I suggest you do consider CHROMIUM BROWSER which is in the Ubuntu repositories and you can install it with Software Center... Chromium Browser is for Linux, Google Chrome and Chromium are same under the hood. If you install Chromium you can readily use all the apps and extensions which are available for Google Chrome.

---

### Post by techvish81 on 2011-11-08
+1 to the above post, actually u can even sync your google chrome passwords, history, bookmarks etc using your google account, so there is no major difference in the usability of both the softwares, chromium is more reliable than chrome as it is the same  minus all the useless advertisement stuff.

---

### Post by oldos2er on 2011-11-08
> **MrsCogan said:**
> I can't install literally anything because I get the message "untrusted software." 

is there a secret handshake I'm overlooking?

Can you run ```
sudo apt-get update && sudo apt-get upgrade
``` in a terminal and post the full output here?

---

### Post by vasa1 on 2011-11-08
> **techvish81 said:**
> +1 to the above post, actually u can even sync your google chrome passwords, history, bookmarks etc using your google account, so there is no major difference in the usability of both the softwares, chromium is more reliable than chrome as it is the same  minus all the useless advertisement stuff.

With Chromium you don't get the built-in PDF reader and the Flash specially modded to work well in the sandbox. And what "useless advertisement stuff" is there?

---

### Post by MrsCogan on 2011-11-08
> **fantab said:**
> Welcome to the Forums!

I usually have this kind of issue when I install software that is not in the repositories or in the Software-Center.

How are you trying to install Google Chrome? Is it a .deb package that you are trying to install via Software Center?
If it is then just ignore the warning and go ahead and install.

I suggest you do consider CHROMIUM BROWSER which is in the Ubuntu repositories and you can install it with Software Center... Chromium Browser is for Linux, Google Chrome and Chromium are same under the hood. If you install Chromium you can readily use all the apps and extensions which are available for Google Chrome.

it is a .deb package I downloaded from Google.

When I try to install from the Software center it says I have a problem with my internet connection (which I don't). Then I get a message saying it requires installation of untrusted software packages and when I click "ok" nothing happens. I won't download anything. That has been the case with any software I try to install from the Software Center.

---

### Post by MrsCogan on 2011-11-08
> **oldos2er said:**
> Can you run ```
sudo apt-get update && sudo apt-get upgrade
``` in a terminal and post the full output here?

where would I find a terminal? I'm not a programmer.

---

### Post by mcduck on 2011-11-08
Have you, at some point, added any third-party repository? The error message about untrusted sources is usually a result from adding a new software repository but not adding the PGP signing key for that repository. As a result, any package installation will give you the error (even if the package you are installing actually comes from a repository for which you do have signing key).

Could you run "sudo apt-get update" and "sudo apt-get upgrade" & post the outputs here?

edit: The terminal is where all your other applications are. Assuming you are using Ubuntu 11.10, just hit the Super key (the one that probably has a windows logo) and type "terminal". And by the way, very few of us here are programmers, running a command in a terminal is no more programming than clicking buttons in graphical windows is. :D It's just another type of *user* interface.

---

### Post by MrsCogan on 2011-11-08
> **mcduck said:**
> Have you, at some point, added any third-party repository? The error message about untrusted sources is usually a result from adding a new software repository but not adding the PGP signing key for that repository. As a result, any package installation will give you the error (even if the package you are installing actually comes from a repository for which you do have signing key).

Could you run "sudo apt-get update" and "sudo apt-get upgrade" & post the outputs here?

edit: The terminal is where all your other applications are. Assuming you are using Ubuntu 11.10, just hit the Super key (the one that probably has a windows logo) and type "terminal". And by the way, very few of us here are programmers, running a command in a terminal is no more programming than clicking buttons in graphical windows is. :D It's just another type of *user* interface.

thanks!

user@user-Inspiron-1012:~$ 
user@user-Inspiron-1012:~$ sudo apt-get update
[sudo] password for user: 
Sorry, try again.
[sudo] password for user: 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates InRelease
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease   
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release.gpg [198 B]
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                   
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources         
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates Release [32.4 kB]
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources/DiffIndex                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources/DiffIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources/DiffIndex  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages/DiffIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe TranslationIndex
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Sources [68.2 kB]
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en  
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Sources [1,345 B]
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Sources [12.5 kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Sources [1,032 B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main i386 Packages [128 kB]
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted i386 Packages [2,878 B]
Get:11 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe i386 Packages [37.2 kB]
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [2,703 B]
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main TranslationIndex [73 B]
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [72 B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [71 B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe TranslationIndex [73 B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/multiverse i386 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/main TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/universe TranslationIndex
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/main Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/multiverse Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric/universe Translation-en
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/main Translation-en [67.3 kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en     
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en [23.0 kB]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/main Translation-en           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/multiverse Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/multiverse Translation-en     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/restricted Translation-en     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/universe Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-backports/universe Translation-en       
Fetched 378 kB in 7s (49.6 kB/s)                                               
Reading package lists... Done
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
user@user-Inspiron-1012:~$ ^C
user@user-Inspiron-1012:~$ sudo apt-get update

---

### Post by oldos2er on 2011-11-08
Try running these commands one at a time. If you still get the BADSIG error let us know.

```
sudo apt-get clean

cd /var/lib/apt

sudo mv lists lists.old

sudo mkdir -p lists/partial

sudo apt-get clean

sudo apt-get update
```

---

### Post by MrsCogan on 2011-11-08
> **oldos2er said:**
> Try running these commands one at a time. If you still get the BADSIG error let us know.

```
sudo apt-get clean

cd /var/lib/apt

sudo mv lists lists.old

sudo mkdir -p lists/partial

sudo apt-get clean

sudo apt-get update
```

thank you! That appears to have worked.

---

### Post by techvish81 on 2011-11-08
> **vasa1 said:**
> With Chromium you don't get the built-in PDF reader and the Flash specially modded to work well in the sandbox. And what "useless advertisement stuff" is there?

it depends on personal likes and dislikes, as far as the pdf reader is concerned, it doesnt make much difference, coz still you can open them , only it will be opened in your pdf reader, flash works fine in my chromium, so i dont need that specially "modded" thing, 
and useless stuff is what is shown in your status bar,when you click on something, " ads.doubleclick.net" etc...  ,
and last but most important is user's privacy, chromium is opensource , u can see what is there inside, but not in chrome. they can use all your browsing data to various purposes. u never know, what they are doing with your data.   

still , i respect your opinion and expect the same from you..

---

### Post by oldos2er on 2011-11-08
> **MrsCogan said:**
> thank you! That appears to have worked.

You're welcome. Would you please mark the thread as 'Solved' (under Thread Tools)?

---

