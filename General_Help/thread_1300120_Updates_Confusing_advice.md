---
title: "Updates Confusing advice?"
date: 2009-10-24
forum: General Help
---

### Post by MadMax2 on 2009-10-24
[ATTACH]132977[/ATTACH]

[ATTACH]132978[/ATTACH]

Important security Updates

Recommended Updates


Warning: you are about to install software that cannot be authenticated!??

I installed it anyway.

---

### Post by dcstar on 2009-10-24
> **MadMax2 said:**
> 

Warning: you are about to install software that cannot be authenticated!??

I installed it anyway.

You get that message because you do not have Authentication Keys for** all** of the repositories you have in your system.

---

### Post by MadMax2 on 2009-10-24
so if I choose the *to be authenticated* they will be authenticated and then installed (if o.k)?

---

### Post by wilee-nilee on 2009-10-25
They wont be authenticated, but they will be installed. Chances are though whatever 3rd party repository you got them from is legitimate. So have you looked at the source list to see what you have installed extra or do you know?

---

### Post by MadMax2 on 2009-10-25
I'mnot sure what I've installed extra (printer, wireless applications, nut nutrition... all linux applications)

is this relevant. Source list:
[deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.]

---

### Post by wilee-nilee on 2009-10-25
All of those look like standard repositories, I wonder if some updates come from a repository that is a 3rd party. I have limited knowledge in this area, but if this happens again you might post the install packages again and see if anybody thinks it looks suspicious if your worried. That being said I have never had a problem in this area but if I install a 3rd party I make sure to get the keys. You might also try another server in your area, since New Zealand servers are updated daily at the least there is probably a logical reason for the unauthenticated info. Hopefully the people who really know whats up will chime in. The only thing I notice is that list is a bit short post the whole thing if you can.  Being a Linux down load doesn't mean you have the key so any additional sources added generally has a key if it's a third party there is a key. If you install via a deb or tar gz and it has a update option there may not be a key but you will see that warning, I think, but get a more accurate appraisal.

---

### Post by P4man on 2009-10-25
can you run

```
sudo apt-get update

```
in a terminal and paste the output here?

---

### Post by MadMax2 on 2009-10-25
xxx@xxxx:~$ sudo apt-get update
[sudo] password for xxxx: 
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid Release.gpg
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Translation-en_NZ
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Translation-en_NZ
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid Release
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Packages
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Packages
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Packages
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Packages
Err cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg [189B]            
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/main Translation-en_NZ              
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/restricted Translation-en_NZ        
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/universe Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/multiverse Translation-en_NZ
Get:2 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates Release.gpg [189B]
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/main Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/restricted Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/universe Translation-en_NZ
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_NZ
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty Release
Get:3 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates Release [57.9kB]          
Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates Release               
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/main Packages                 
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/main Sources                        
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/restricted Sources                  
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/universe Packages                   
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/universe Sources                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_NZ       
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/multiverse Packages                 
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty/multiverse Sources                  
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/main Packages               
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/restricted Packages         
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/main Sources                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_NZ 
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/restricted Sources          
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/universe Packages           
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/universe Sources            
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/multiverse Packages         
Hit [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates/multiverse Sources          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_NZ   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_NZ
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release [57.9kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Fetched 380B in 3s (101B/s)                           
W: GPG error: [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)/dists/intrepid/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
xxxxxx@xxxx:~$ 

Thanks a lot
may not be able to return for a few days.

---

### Post by wilee-nilee on 2009-10-25
> **P4man said:**
> can you run

```
sudo apt-get update

```in a terminal and paste the output here?

 Good idea why didn't I think of this. I well let you address the apt-get list it has some problems obviously, ;)

---

### Post by P4man on 2009-10-25
> **wilee-nilee said:**
> Good idea why didn't I think of this. I well let you address the apt-get list it has some problems obviously, ;)

Oh no, be my guest lol. Now that he posted it, Im actually not sure you see.

MadMax2, you could start by disabling the cdrom as source in system >adminstration > software sources. But Im not sure thats the only issue. but wilee-nilee will help you with that :p

---

### Post by wilee-nilee on 2009-10-25
So here is a link to what the list should look like. So save what you have in another gedit file or on open office, so that you can pull anything that is extra and jaunty or 3rd party and add it to the new list which is a copy and paste from the link into the apt-get sources list the computer is reading for updates. So when you copy the list from the link you want the apt-get sources list empty, because you don't want double repositories, and you have saved your original for looking at side by side to add any extras that are not in the stock sources list in the link. I think understanding this process is one of the most important things to know how to do, as it is all about keeping your computer updated and having control over the source list. Make sure you hit the save button before closing any edited list.  [http://ubuntuforums.org/archive/index.php/t-997890.html](http://ubuntuforums.org/archive/index.php/t-997890.html)  So the command from the terminal for opening the source list for editing is sudo gedit /etc/apt/sources.list Hope this makes sense to you, I just see a mixture of intrepid in with jaunty which if a person knows what there doing having a mixed source list is on occasion needed due to incompatibilities in a driver or in some other area.  Feel free to post more questions if needed before doing anything I have the instant email on.  With the koala release I have found that any server other then the USA or main give me failed updates partially but I am in the USA.

---

### Post by MadMax2 on 2009-10-26
Thanks I'll do that soon.

---

