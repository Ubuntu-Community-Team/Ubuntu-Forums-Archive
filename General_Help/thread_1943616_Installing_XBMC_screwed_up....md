---
title: "Installing XBMC screwed up..."
date: 2012-03-19
forum: General Help
---

### Post by picorex on 2012-03-19
I know what the problem is but I don't know how to fix it.

/etc/apt/sources.list.d/team-xbmc-ppa-oneiric.list
/etc/apt/sources.list.d/team-xbmc-ppa-oneiric.list.save

these files have a spurious 3rd line that simply reads "ain". it is preventing install of XBMC and now preventing me from opening synaptic too.

I get permission denied if I try to delete the files, permission denied if I try to edit and save the files, gksudo gedit from terminal does not do anything and rmdir also permission denied.

How can I sort this?

Thanks

---

### Post by JC Cheloven on 2012-03-19
have you tried to edit those from a terminal, with (for example) the 'nano' editor?
```
sudo nano <full path to your file here>
```

Perhaps you can try the above booting to a console in secure mode, to ensure the file is not in use in any way (unlikely, but anyway).

In the worst case you can edit it from a live session.

Hope that helps

---

### Post by picorex on 2012-03-20
Thank you ever so much, using nano I managed to edit the files. But still I'm having trouble installing XBMC. Here is the error I get - 

```
alex@MICROMAMMOTH:~$ sudo add-apt-repository ppa:team-xbmc
You are about to add the following PPA to your system:
 XBMC PPA
 
 More info: [https://launchpad.net/~team-&#8203;xbmc/+archive/ppa]("https://launchpad.net/%7Eteam-%E2%80%8Bxbmc/+archive/ppa")
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.YDXRzhSqlJ --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 189701DA570C56B9488EF60A6D975C&#8203;4791E7EE5E
gpg: requesting key 91E7EE5E from hkp server keyserver.ubuntu.com
gpg: key 91E7EE5E: public key "Launchpad PPA for XBMC for Linux" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
alex@MICROMAMMOTH:~$ sudo apt-get install xbmc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xbmc
```

```
alex@MICROMAMMOTH:~$ sudo apt-get update
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates InRelease          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports InRelease         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release.gpg                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates Release.gpg         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease                       
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports Release.gpg       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric Release                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates Release                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports Release                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse TranslationIndex 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe TranslationIndex             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main Sources                  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe Sources              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main i386 Packages  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe i386 Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex                     
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main Sources      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse Sources          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main i386 Packages          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted i386 Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe i386 Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main TranslationIndex       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Translation-en_GB      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Translation-en_GB          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/multiverse Translation-en             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric/universe Translation-en     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/main Translation-en 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-updates/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) oneiric-backports/universe Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources
  404  Not Found
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_GB
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages
  404  Not Found
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_GB
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
[B]W: Failed to fetch [http://ppa.launchpad.net/team-&#8203;xbmc/ppa/ubuntu/dists/oneiric/&#8203;main/source/Sources]("http://ppa.launchpad.net/team-%E2%80%8Bxbmc/ppa/ubuntu/dists/oneiric/%E2%80%8Bmain/source/Sources")  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/team-&#8203;xbmc/ppa/ubuntu/dists/oneiric/&#8203;main/binary-i386/Packages]("http://ppa.launchpad.net/team-%E2%80%8Bxbmc/ppa/ubuntu/dists/oneiric/%E2%80%8Bmain/binary-i386/Packages")  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.[/B]
```

Do you have any idea what the problem is? Sorry for being a newbie.

---

### Post by JC Cheloven on 2012-03-20
To start with the simplest: are you sure about that "ain" being spurious?

I'm thinking about it belonging to the previous line, for example as the ending of the word "main", which may have be cut off by a text editor or so. Also please note that text editors usually accomodates in the window width as much as possible of a single line, and show the rest of it in the following line (it's still a single line, and will be shown as such if you enlarge the window).

Side note: please consider using "code" tags instead of "quote" tags for the output of commands etc. It results in a nice scrollable area instead of a large text area ;)

---

### Post by picorex on 2012-03-20
pretty sure it doesnt belong to the previous line. the contents of both files read as follows

```

deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) oneiric main
deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) oneiric main

```

you'll notice that the 404 Not Found error (first post) does indeed lead to a dead link when you try to open it in a browser... so i guess that's the problem.

---

### Post by picorex on 2012-03-20
well in the end i followed another random instruction to install XBMC - this one:

```

**[COLOR=red]>>[/COLOR] _Method 2 to Install XBMC on Ubuntu 11.10/_****_Ubuntu 11.04/10.10/10.04/9.10/9.04/8.04_****_:_**

To install XBMC on **Ubuntu 11.10 Oneiric** open Terminal (Press *Ctrl+Alt+T*) and copy the following commands in the Terminal: **(You don't need to enter all PPA's)**[INDENT] 
[LIST]
[*][COLOR=red][FONT=monospace]sudo add-apt-repository ppa:nathan-renniewaldock/xbmc-stable[/FONT][/COLOR] This following PPA is for XBMC Eden 11.0 PRE (unstable)
[*][COLOR=red][FONT=monospace]sudo add-apt-repository ppa:team-xbmc/unstable[/FONT][/COLOR] This following PPA is for XBMC Eden 11.0 PRE (unstable)
[*][COLOR=red][FONT=monospace]sudo add-apt-repository ppa:alexandr-surkov/xbmc[/FONT][/COLOR] This following PPA is for XBMC Eden 11.0 PRE (unstable)
[*][COLOR=red][FONT=monospace]sudo add-apt-repository ppa:alexandr-surkov/xbmc-pvr[/FONT][/COLOR] This following PPA is for XBMC Dharma 10.1
[*][COLOR=red][FONT=monospace]sudo add-apt-repository ppa:team-xbmc/ppa[/FONT][/COLOR] Then install
[*][COLOR=red][FONT=monospace]sudo apt-get update[/FONT][/COLOR]
[*][COLOR=red][FONT=monospace]sudo apt-get install xbmc[/FONT][/COLOR]
[/LIST]
[/INDENT]
```[INDENT]
and it seems to have installed properly . god knows what i've done to the machine and how much unnecessary stuff got installed but at least XBMC is installed and working now.


thanks for the help.


[/INDENT]

---

### Post by JC Cheloven on 2012-03-20
Strange enough, the web location
[http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu)
seems to be on line at this moment... oh wait, digging in, I see it has packages only until maverick (10.10). You're using a newer ubuntu version (oneiric, as I see in your error output). It must be that...

As a caution, I'd have a look to /etc/apt/sources.list, or in the sources.list.d directory, and eventually remove the lines of your first attempted ppa, if they are present (this also can be done using the graphical frontend provided in the menu as 'software sources').

BTW, do you know that [xbmc]("http://xbmc.org/about/") exists as an independent 'distribution' (well, perhaps much to say). Perhaps you're interested in.

Anyway, glad you found a proper ppa to install Xbox media center under ubuntu. Enjoy!

---

