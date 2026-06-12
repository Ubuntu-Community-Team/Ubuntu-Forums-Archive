---
title: "new to ubuntu"
date: 2011-10-29
forum: General Help
---

### Post by ishandatt on 2011-10-29
hello people...
i have just installed ubuntu 11.10 for the first time and am facing a lot of issues... require someone patient enough to guide me through the various things and be patient enough for my doubts...

---

### Post by oldtimer7777 on 2011-10-29
> **ishandatt said:**
> hello people...
i have just installed ubuntu 11.10 for the first time and am facing a lot of issues... require someone patient enough to guide me through the various things and be patient enough for my doubts...

This will help get your started:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

---

### Post by ishandatt on 2011-10-29
well i had like to be more specific... i have proxy connection for internet... the internet on firefox seems to be working just fine, but the other applications dont seem to be working... like the chat client empathy, or while downloading codecs for media files or the software update centre... the software update centre starts to download and then towards the end of it says package could not be downloaded or repository not found...

---

### Post by oldtimer7777 on 2011-10-29
> **ishandatt said:**
> well i had like to be more specific... i have proxy connection for internet... the internet on firefox seems to be working just fine, but the other applications dont seem to be working... like the chat client empathy, or while downloading codecs for media files or the software update centre... the software update centre starts to download and then towards the end of it says package could not be downloaded or repository not found...

The best thing to do is to locate a hardwired connection to the internet so you can do your initial updates and upgrades on your system, and get any other packages installed, considering how many are required if you have just recently installed a fresh system of Ubuntu. If you read through the above checklist To Do List, you will see there is a considerable number of packages you are going to need to install to have a fully functional setup, and you are going to want a much more a reliable connection then the one you are using currently. 

Don't use a WiFi connection to do your intial updates and upgrades and the rest of the packages you need..  Use Wifi after you get everything the way you like it first.

---

### Post by ishandatt on 2011-10-29
allright... i will do that... but what about the messenger and what if i wish to download any program later...?

---

### Post by ishandatt on 2011-10-29
every time i try to install synaptic package manager, it firstly does not show me a install button and instead shows "more information". which when clicked displays message "available from the universe source" and then it starts updating cache...

---

### Post by ishandatt on 2011-10-30
can someone help me... whenever i try to download something, it always  shows updating cache... and then quits by either saying repository not  found or package cannot be downloaded... please check your internet...

---

### Post by linuxaddix on 2011-10-30
have you tried going through software center and repairing broken packages.i still get those occasionally in 11.04.i repair broken packages,do a quick sudo apt-get update,then try installing what failed.usually it works.if not try rebooting then try again.have you checked your update manager also?

---

### Post by Peterfc on 2011-10-30
Hi Ishandatt

I have the same problem but when i try to install using the Ubuntu Software Centre. I can when i use the synaptic manager install program but my problem is with the Ubuntu Software Centre.

Good luck

---

### Post by oldos2er on 2011-10-30
> **ishandatt said:**
> can someone help me... whenever i try to download something, it always  shows updating cache... and then quits by either saying repository not  found or package cannot be downloaded... please check your internet...

Can you open a terminal, (Ctrl-Alt-t), enter ```
sudo apt-get update
``` and copy and paste all the output from that command here?

---

### Post by ishandatt on 2011-10-31
ishan@Ishan:~$ sudo apt-get update
[sudo] password for ishan: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric InRelease
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release.gpg                          
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release   
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                     
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Sources
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex           
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner TranslationIndex    
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric InRelease   
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates InRelease
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en_US
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security InRelease
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en             
Ign [http://archive.canonical.com](http://archive.canonical.com) oneiric/partner Translation-en      
Get:2 [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric Release.gpg [198 B]
Get:3 [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates Release.gpg [198 B]
Get:4 [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports Release.gpg [198 B]
Get:5 [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security Release.gpg [198 B]
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric Release
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric Release      
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates Release
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates Release
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports Release
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports Release
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security Release
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security Release
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/restricted Sources/DiffIndex
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/universe Sources/DiffIndex                  
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/multiverse Sources/DiffIndex                
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/main i386 Packages/DiffIndex                
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/restricted i386 Packages/DiffIndex          
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/universe i386 Packages/DiffIndex            
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/multiverse i386 Packages/DiffIndex          
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/main TranslationIndex                       
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/multiverse TranslationIndex                 
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/restricted TranslationIndex                 
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/universe TranslationIndex                   
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/main Sources/DiffIndex              
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/restricted Sources/DiffIndex        
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/universe Sources/DiffIndex          
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/multiverse Sources/DiffIndex        
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/main i386 Packages/DiffIndex        
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/restricted i386 Packages/DiffIndex  
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/universe i386 Packages/DiffIndex    
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/multiverse i386 Packages/DiffIndex  
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/main TranslationIndex               
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/multiverse TranslationIndex
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/restricted TranslationIndex
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/universe TranslationIndex
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/main Sources/DiffIndex
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/restricted Sources/DiffIndex
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/universe Sources/DiffIndex
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/multiverse Sources/DiffIndex
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/main i386 Packages/DiffIndex
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/restricted i386 Packages/DiffIndex
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/universe i386 Packages/DiffIndex
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/multiverse i386 Packages/DiffIndex
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/main TranslationIndex
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/multiverse TranslationIndex
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/restricted TranslationIndex
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/universe TranslationIndex
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/main Sources/DiffIndex
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/restricted Sources/DiffIndex
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/universe Sources/DiffIndex
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/multiverse Sources/DiffIndex
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/main i386 Packages/DiffIndex
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/restricted i386 Packages/DiffIndex
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/universe i386 Packages/DiffIndex
Ign [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/multiverse i386 Packages/DiffIndex
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/main TranslationIndex
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/multiverse TranslationIndex
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/restricted TranslationIndex
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/universe TranslationIndex
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/restricted Sources
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/universe Sources
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/multiverse Sources
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/main i386 Packages
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/restricted i386 Packages
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/universe i386 Packages
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/multiverse i386 Packages
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/main Translation-en
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/multiverse Translation-en
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/restricted Translation-en
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/universe Translation-en
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/main Sources
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/restricted Sources
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/universe Sources
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/multiverse Sources
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/main i386 Packages
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/restricted i386 Packages
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/universe i386 Packages
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/multiverse i386 Packages
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/main Translation-en
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/multiverse Translation-en
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/restricted Translation-en
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates/universe Translation-en
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/main Sources
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/restricted Sources
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/universe Sources
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/multiverse Sources
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/main i386 Packages
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/restricted i386 Packages
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/universe i386 Packages
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/multiverse i386 Packages
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/main Translation-en
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/multiverse Translation-en
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/restricted Translation-en
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports/universe Translation-en
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/main Sources
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/restricted Sources
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/universe Sources
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/multiverse Sources
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/main i386 Packages
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/restricted i386 Packages
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/universe i386 Packages
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/multiverse i386 Packages
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/main Translation-en
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/multiverse Translation-en
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/restricted Translation-en
Hit [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security/universe Translation-en
Get:6 [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric/main Sources [1,095 kB]
Fetched 865 B in 42s (20 B/s)         
W: GPG error: [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ftp.ussg.iu.edu](http://ftp.ussg.iu.edu) oneiric-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch gzip:/var/lib/apt/lists/partial/ftp.ussg.iu.edu_linux_ubuntu_dists_oneiric_main_source_Sources  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by ishandatt on 2011-10-31
> **oldos2er said:**
> Can you open a terminal, (Ctrl-Alt-t), enter ```
sudo apt-get update
``` and copy and paste all the output from that command here?

i have done that.

---

### Post by oldos2er on 2011-10-31
Why do you have the backports repository enabled? You might want to think about disabling it.

In Synaptic, click Settings, Repositories, Download from, change to the main server, then reload your sources.

Try [http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html) to clear the BADSIG errors.

---

### Post by ishandatt on 2011-10-31
i dont think i have synaptic installed... please help me... totally stuck...

---

### Post by ishandatt on 2011-10-31
the link did not work for me...

---

### Post by ishandatt on 2011-10-31
ishan@ishan:~$ sudo aptitude -o Acquire::http::No-Cache=True -o Acquire::BrokenProxy=true update
[sudo] password for ishan: 
sudo: aptitude: command not found
ishan@ishan:~$ sudo -i
root@ishan:~# apt-get clean
root@ishan:~# cd /var/lib/apt
root@ishan:/var/lib/apt# mv lists lists.old
root@ishan:/var/lib/apt# mkdir -p lists/partial
root@ishan:/var/lib/apt# apt-get clean
root@ishan:/var/lib/apt# apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg [198 B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release [28.2 kB]            
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources [6,185 B]       
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric InRelease                             
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates InRelease           
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources [14 B]
Get:5 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]                      
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports InRelease                   
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources [14 B]
Get:7 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release [9,759 B]                       
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release.gpg [198 B]                 
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources [14 B]    
Get:10 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates Release.gpg [198 B]        
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages [14.3 kB]
Get:12 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports Release.gpg [198 B]      
Get:13 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release [40.8 kB]                  
Get:14 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources [14 B]                    
Get:15 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages [14 B]              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Get:16 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates Release [32.4 kB]          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release                               
Get:17 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports Release [24.3 kB]        
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates Release                       
Get:18 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main Sources [877 kB]              
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports Release                     
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_IN                    
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en                       
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages [14.3 kB]
98% [18 Sources bzip2 0 B] [Waiting for headers] [19 Packages 3,986 B/14.3 kB 2
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main TranslationIndex                 
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse TranslationIndex           
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted TranslationIndex           
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages [14.3 kB]
Get:21 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe TranslationIndex [2,640 B]
Get:22 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/main Sources [60.8 kB]     
Get:23 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/restricted Sources [14 B]  
Get:24 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/universe Sources [6,810 B] 
Get:25 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/multiverse Sources [1,032 B]
Get:26 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/main i386 Packages [110 kB]
Get:27 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages [14.3 kB]
Get:28 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/restricted i386 Packages [14 B]
Get:29 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/universe i386 Packages [28.1 kB]
Get:30 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages [2,703 B]
Get:31 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/main TranslationIndex [73 B]
Get:32 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex [72 B]
Get:33 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex [70 B]
Get:34 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/universe TranslationIndex [73 B]
Get:35 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/main Sources [743 B]     
Get:36 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/restricted Sources [14 B]
Get:37 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/universe Sources [814 B] 
Get:38 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/multiverse Sources [14 B]
Get:39 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/main i386 Packages [649 B]
Get:40 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/restricted i386 Packages [14 B]
Get:41 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/universe i386 Packages [681 B]
Get:42 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages [14 B]
Get:43 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/main TranslationIndex [71 B]
Get:44 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex [70 B]
Get:45 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex [70 B]
Get:46 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/universe TranslationIndex [71 B]
Get:47 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main Translation-en [701 kB]       
Get:48 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse Translation-en [92.6 kB]
Get:49 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages [14.3 kB]
Get:50 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted Translation-en [2,229 B]
Get:51 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe Translation-en [3,165 kB] 
Get:52 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages [14.3 kB]
62% [52 Packages bzip2 0 B] [51 Translation-en 1,232 kB/3,165 kB 38%] [Waiting 
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Get:53 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages [14 B]
Get:54 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages [5,250 B]
Get:55 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages [5,250 B]
82% [55 Packages bzip2 0 B] [51 Translation-en 2,266 kB/3,165 kB 71%] [Waiting 
bzip2: Data integrity error when decompressing.
    Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Get:56 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/main Translation-en [57.7 kB]
Get:57 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages [14 B]
Get:58 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex [72 B]
Get:59 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex [70 B]
Get:60 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex [70 B]
Get:61 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/multiverse Translation-en [1,190 B]
Get:62 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex [72 B]
Get:63 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/restricted Translation-en [14 B]
Get:64 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates/universe Translation-en [18.1 kB]
Get:65 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en [9,267 B]
Get:66 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/main Translation-en [604 B]
Get:67 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/multiverse Translation-en [14 B]
Get:68 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en [14 B]
Get:69 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/restricted Translation-en [14 B]
Get:70 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en [14 B]
Get:71 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports/universe Translation-en [647 B]
Get:72 [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en [4,303 B]
Err [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages         
  404  Not Found
Get:73 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted Sources [5,267 B]       
Get:74 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe Sources [5,792 kB]        
Get:75 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse Sources [180 kB]        
Get:76 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main i386 Packages [1,583 kB]      
Get:77 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted i386 Packages [8,882 B] 
Get:78 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/universe i386 Packages [5,769 kB]  
Get:79 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse i386 Packages [152 kB]  
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/main Translation-en_IN                
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/multiverse Translation-en_IN          
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric/restricted Translation-en_IN          
Fetched 18.8 MB in 5min 45s (54.3 kB/s)                                        
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch gzip:/var/lib/apt/lists/partial/security.ubuntu.com_ubuntu_dists_oneiric-security_main_binary-i386_Packages  Hash Sum mismatch

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/oneiric-security/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch gzip:/var/lib/apt/lists/partial/in.archive.ubuntu.com_ubuntu_dists_oneiric_main_source_Sources  Encountered a section with no Package: header

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

