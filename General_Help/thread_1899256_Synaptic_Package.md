---
title: "Synaptic Package"
date: 2011-12-23
forum: General Help
---

### Post by gjohnno on 2011-12-23
I can not access Synaptic Package Manager (SPM) on my Desktop PC , although I can access the SPM using my Netbook PC. I am using Oneric on both PCs. 

I access the SPM by clicking through the Dash Home. Alls fine up to this stage. The authenication pop up appears on the screen. I type in my user password, click on the Ok button. the screen appears to do a bit of a refresh. but no SPM appears on my Desktop Screen.

 I have shutdown the system and rebooted, I have apt-get install new updates. I am starting to think that I have a virus of some type

Hopefully someone can assist

---

### Post by SnickerSnack on 2011-12-23
Have you tried running synaptic from the command line and looking for any error messages?

---

### Post by sikander3786 on 2011-12-23
Hi.

Please get to a Terminal and run and post the outputs of these commands:

```
sudo apt-get update && sudo apt-get upgrade
synaptic
gksu synaptic
```

The outputs might be big in size so please don't forget to wrap them in [code] tags by clicking the # icon in post menu and pasting your outputs in between the tags.

---

### Post by gjohnno on 2011-12-23
What command line do I use in the terminal ?

---

### Post by gjohnno on 2011-12-23
When I put in the second line " synaptic" and copy it in to the terminal I get the following pop up

Starting without administrative privileges

You will not be able to apply any changes. But you can still export the marked changes or create a download script for them.

---

### Post by gjohnno on 2011-12-23
user@user-desktop:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for user: 
Sorry, try again.
[sudo] password for user: 
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric InRelease
Ign [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates InRelease                     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric Release.gpg                           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates Release.gpg                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric Release                               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates Release                       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/main Sources                          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/restricted Sources                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/universe Sources                      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/multiverse Sources                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/main amd64 Packages                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/restricted amd64 Packages             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/universe amd64 Packages               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/multiverse amd64 Packages             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/main i386 Packages                    
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/restricted i386 Packages              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/universe i386 Packages                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/multiverse i386 Packages              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/main TranslationIndex                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/universe TranslationIndex             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/main Sources                  
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/restricted Sources            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/universe Sources              
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/multiverse Sources            
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/main amd64 Packages           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/restricted amd64 Packages     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/universe amd64 Packages       
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/main i386 Packages            
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric InRelease                                 
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/restricted i386 Packages      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/universe i386 Packages        
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages      
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/main TranslationIndex         
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/universe TranslationIndex     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/main Translation-en_AU                
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/main Translation-en                   
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/multiverse Translation-en_AU          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/multiverse Translation-en             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/restricted Translation-en_AU          
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/restricted Translation-en             
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric/universe Translation-en               
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/main Translation-en           
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/multiverse Translation-en     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/restricted Translation-en     
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) oneiric-updates/universe Translation-en       
Hit [http://linux.dropbox.com](http://linux.dropbox.com) oneiric Release.gpg                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease                             
Hit [http://linux.dropbox.com](http://linux.dropbox.com) oneiric Release                                   
Hit [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main amd64 Packages                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg                               
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                           
Hit [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main i386 Packages                        
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main TranslationIndex                     
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release                                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release                        
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources         
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner amd64 Packages      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main amd64 Packages             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main amd64 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted amd64 Packages      
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages                 
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe amd64 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main Translation-en_AU          
Ign [http://linux.dropbox.com](http://linux.dropbox.com) oneiric/main Translation-en                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en        
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_AU             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_AU          
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198 B]
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,338 B]                            
Get:3 [http://dl.google.com](http://dl.google.com) stable/main amd64 Packages [469 B]                  
Get:4 [http://dl.google.com](http://dl.google.com) stable/main i386 Packages [464 B]                   
Ign [http://dl.google.com](http://dl.google.com) stable/main TranslationIndex                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_AU                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en
Fetched 2,469 B in 50s (48 B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
user@user-desktop:~$ synaptic
gksu synaptic

---

### Post by sikander3786 on 2011-12-23
Hmmm, no errors at all.

Try re-installing Syanptic with:

```
sudo apt-get install --reinstall synaptic
```

Try starting Synaptic again, if that doesn't help either, try:

```
sudo apt-get purge synaptic
sudo apt-get install synaptic
sudo dpkg --configure -a
```

And again try opening Synaptic.

---

### Post by SnickerSnack on 2011-12-23
> **gjohnno said:**
> When I put in the second line " synaptic" and copy it in to the terminal I get the following pop up

Starting without administrative privileges

You will not be able to apply any changes. But you can still export the marked changes or create a download script for them.

So synaptic did run?

Running

```
gksudo synaptic
```

will fix that pop up you got.  Edit: A tip of my hat to sikander3786 for pointing out that it's bad practice to use sudo to run graphical programs.

---

### Post by gjohnno on 2011-12-23
I have followed all your instructions. However I still get the same results as stated in the first post. Also the Ubuntu Software Centre will not allow me access to " Systems" files All other files I have access

---

### Post by sikander3786 on 2011-12-23
> **gjohnno said:**
> I have followed all your instructions. However I still get the same results as stated in the first post. Also the Ubuntu Software Centre will not allow me access to " Systems" files All other files I have access
Then, it isn't any issue with Synaptic probably but with graphical sudo. Please try this:

```
gksu nautilus
```

Does the file browser show up?

Remember, don't make any changes to the files if file browser opens up. It is running as root and you might easily make changes to important system files, even accidentally. Just test it and then close the file browser.

---

### Post by gjohnno on 2011-12-23
Yes the file Browser shows up after I typed in my User Password

---

### Post by sikander3786 on 2011-12-23
This is taking a bit longer than expected. :)

Please try this:

```
gksudo /usr/sbin/synaptic &
```

Any error messages? If yes, post them. If not, please post the complete output from this one:

```
gksudo strace /usr/sbin/synaptic &
```

---

### Post by gjohnno on 2011-12-23
user@user-desktop:~$ gksudo /usr/sbin/synaptic &
[1] 6362
user@user-desktop:~$   what():  vector::_M_range_check
 instance of 'std::out_of_range'

---

### Post by gjohnno on 2011-12-23
user@user-desktop:~$ gksudo /usr/sbin/synaptic &
[1] 6381
user@user-desktop:~$ gksudo strace /usr/sbin/synaptic &
[2] 6401
[1]   Exit 134                gksudo /usr/sbin/synaptic
user@user-desktop:~$ poll([{fd=3, events=POLLIN}], 1, -1)    = 1 ([{fd=3, revents=POLLIN}])

---

### Post by sikander3786 on 2011-12-23
Ok thats it. Thanks for your patience.

Here is a solved thread with the same issue:

[http://ubuntuforums.org/showthread.php?t=1865094](http://ubuntuforums.org/showthread.php?t=1865094)

And the post that helped the OP solve his issue there is this one:

[http://ubuntuforums.org/showpost.php?p=11343209&postcount=10](http://ubuntuforums.org/showpost.php?p=11343209&postcount=10)

---

