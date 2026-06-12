---
title: "Error Msg &amp; Lock-up"
date: 2009-12-22
forum: General Help
---

### Post by lotusalive on 2009-12-22
Dodo-bird here locked up her system, and was wondering if someone might be able to help me untangle it...  Terminal is giving me Error Msg: 

root@lightening-desktop:/home/lightening# apt-get install repositories
E: Malformed line 54 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
root@lightening-desktop:/home/lightening# 

Pkg Mgr Crashes with Error Msg to Report the Bug to Devs, but won't open a window to do so.

Synaptics Pkg Mgr has the same Error Msg, and asks me to 'go to the repository dialogue to correct the problem,' but also crashes on close of the Error Msg...  

As usual, all suggestions Welcome...

---

### Post by lavinog on 2009-12-23
can you post /etc/apt/sources.list?
Could it be corrupt?
if so there should be a backup somewhere in /etc/apt

---

### Post by lotusalive on 2009-12-23
Thanks...  Result:

lightening@lightening-desktop:~$ sudo su /etc/apt/sources.list
[sudo] password for lightening: 
pam_mount(pam_mount.c:100): unknown pam_mount option "use_first_pass"
Unknown id: /etc/apt/sources.list

Don't know how to use /etc/apt dir in terminal...  sorry.

---

### Post by lavinog on 2009-12-23
it's just
```

cat /etc/apt/sources.list

```

you shouldn't use sudo su...sudo -i does a simmilar thing, but viewing the sources file doesn't require root access.

---

### Post by lotusalive on 2009-12-23
Is this what you want to see ?  

lightening@lightening-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/jaunty](http://archive.ubuntu.com/ubuntu/jaunty) main
lightening@lightening-desktop:~$ 


Strange, in that it looks like I have both Intrepid and Jaunty, and should NOT, huh... ?

---

### Post by lavinog on 2009-12-23
> **lotusalive said:**
> 
Strange, in that it looks like I have both Intrepid and Jaunty, and should NOT, huh... ?
Its ok, the intrepid lines have a leading pound sign that comments them out.
the problem is the last line:
```

deb [http://archive.ubuntu.com/ubuntu/jaunty](http://archive.ubuntu.com/ubuntu/jaunty) main

```

it is not complete.
it looks like you can just comment it out.
```

sudo nano /etc/apt/sources.list

```
go to the last line and add a # to the beginning, then press ctrl-x then 'y' to save.
then refresh the repository:
```

sudo apt-get update

```

Then you should be able to install or perform upgrades.
```

# to upgrade everything
sudo apt-get upgrade

# to install a package
sudo apt-get install packagename

```

are you not able to use the gui?

---

### Post by lotusalive on 2009-12-23
Right, the Update Mgr gui is crashing due to the same error msg, and has a huge red circle with a 'negatory sign' in it on my launch panel, (lol...)

command code is not recognizing:

lightening@lightening-desktop:~$ sudo deb [http://archive.ubuntu.com/ubuntu/jaunty](http://archive.ubuntu.com/ubuntu/jaunty) main
sudo: deb: command not found
lightening@lightening-desktop:~$ deb [http://archive.ubuntu.com/ubuntu/jaunty](http://archive.ubuntu.com/ubuntu/jaunty) main
bash: deb: command not found
lightening@lightening-desktop:~$

sorry, I misunderstood, will try it the way you suggest...  will be back...

---

### Post by lotusalive on 2009-12-23
After cat /etc/apt/sources.list, when I run the sudo nano code, it only gives me this, where I cannot insert anything: 

  GNU nano 2.0.9         File: /etc/apt/sources.list                          

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrep$
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jaunty-updates main restricted
                              [ Read 54 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

---

### Post by lavinog on 2009-12-23
> **lotusalive said:**
> After cat /etc/apt/sources.list, when I run the sudo nano code, it only gives me this, where I cannot insert anything: 


nano is a text editor.  use it just like a word processor...I assumed you didn't have the ability to use the gui.
You could try gedit instead if you do have a gui:
press alt-f2
```

gksudo gedit /etc/apt/sources.list

```
then scroll to the bottom, add a # to the beginning of the last line. then save and close gedit.
Then try using synaptic.

---

### Post by iponeverything on 2009-12-23
It looks like your sources.list got truncated.

do a "df" to make sure your partition is not full and perhaps someone can post a good sources.list for jaunty that you can replace yours with.

---

### Post by lotusalive on 2009-12-23
That Worked !  Is THAT ever cool !  :))  Thank you...  Synaptic Pkg Mgr opened just fine !

But the launch panel Package Mgr Red-Dot-Neg error says my 'E: 54...' usually means installed packages have unmet dependencies... and I have no idea what I was installing when lost power, so can I just do sudo apt-get update ?  Will that look for my unmet dependencies ?

---

### Post by lavinog on 2009-12-23
in synaptic, do a reload, then mark all updates, then apply.

---

### Post by lotusalive on 2009-12-23
silly brave-heart that I am, ran the Terminal sudo apt-get update, and it was fine...  then in Synaptic, Reload, Mark All Upgrades, and it loaded the 5 pkgs I needed...  Boy, was I EVER over my head, on that one...  I love this stuff and wish I was good at it !  :))  Thank you SO, So much lavinog !

I'd post you a Happy Holidays photo, but I'd have to go find the 'url' deal, and it would take too much time !  (If you ck back here, I'll try to, or send you a msg !)   Thanks again, VERY MUCH !

---

### Post by lavinog on 2009-12-23
iponeverything has a good point, you might want to make sure you have plenty of disk space
```

#This will work in the terminal:
df -h
```

or you can use system>admin>system monitor, then go to the file systems tab.

usually though if you are running low on disk space, you should be getting a notification about it.

---

### Post by lotusalive on 2009-12-23
lightening@lightening-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              92G  7.1G   80G   9% /
tmpfs                 497M     0  497M   0% /lib/init/rw
varrun                497M  160K  496M   1% /var/run
varlock               497M     0  497M   0% /var/lock
udev                  497M  184K  496M   1% /dev
tmpfs                 497M   84K  496M   1% /dev/shm
lrm                   497M  2.2M  494M   1% /lib/modules/2.6.28-17-generic/volatile
/dev/sda6              24G  289M   23G   2% /home
/dev/sda1              30G   67M   30G   1% /windows
/dev/sdg1            1000M  104M  896M  11% /media/USB DISK
/dev/sdf1            1000M  786M  215M  79% /media/USB DISK_
/dev/sr0              8.0G  8.0G     0 100% /media/cdrom0
lightening@lightening-desktop:~$

---

### Post by lavinog on 2009-12-23
looks like you have plenty of space.

For future reference it helps to post command output in code blocks
```

like this

```
There should be a [img]http://ubuntuforums.org/images/editor/code.gif[/img] button on the post editor...if not use [noparse]```
 stuff to be inside 
```[/noparse]

I have a link in my signature for more information.

---

### Post by lotusalive on 2009-12-23
no **#** on this post editor, but, see if this works, like this: ```
I'm trying to 'grow up' but I have so many interruptions in my life, it really isn't even funny !  Thank you for all the help and suggestions, you guys...  I'll work at getting to them.  I'd like to ! :)  (It's snowing here tonight !)  your friend, lotusalive
```  NO-doh. / EY !

---

### Post by lotusalive on 2009-12-23
they might not like me for this, but here it is:  ```
[http://img138.imageshack.us/img138/4149/julevindu1.gif]("http://img138.imageshack.us/img138/4149/julevindu1.gif")
```

Thank you:  From our No. American neck of the wookies: [http://yfrog.com/7grotatingholidaysg]("http://yfrog.com/7grotatingholidaysg")

---

### Post by lotusalive on 2009-12-27
I still don't seem to have Jaunty installed properly.  Neither Intrepid, nor Jaunty are Checked Off in my Repositories !

When I go to Syn Pkg Mgr Repositories, **[http://archive.ubuntu.com/ubuntu/jaunty](http://archive.ubuntu.com/ubuntu/jaunty) main** is unchecked, and when I Add it, give the APT line, it will not give me the option to add it.  If I just reload Repos, it locks up Synaptics stating that the Repo is no longer available... and gives me details: 

```
E: Malformed line 54 in source list /etc/apt/sources.list (dist parse)

E: The list of sources could not be read.

Go to the repository dialog to correct the problem.

E: _cache->open() failed, please report.
```

I then have to repeat the whole process in this Thread to unlock Synaptics again...  So I am not getting any updates, etc.

This is Terminal result of asking for upgrade and update:

```
lightening@lightening-desktop:~$ gksudo gedit /etc/apt/sources.list
lightening@lightening-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lightening@lightening-desktop:~$ sudo apt-get update
Hit http://us.archive.ubuntu.com jaunty Release.gpg
Ign http://us.archive.ubuntu.com jaunty/main Translation-en_US      
Hit http://security.ubuntu.com jaunty-security Release.gpg           
Ign http://security.ubuntu.com jaunty-security/main Translation-en_US
Hit http://archive.canonical.com jaunty Release.gpg                  
Ign http://archive.canonical.com jaunty/partner Translation-en_US    
Hit http://packages.medibuntu.org jaunty Release.gpg                 
Ign http://packages.medibuntu.org jaunty/free Translation-en_US      
Ign http://packages.medibuntu.org jaunty/non-free Translation-en_US  
Ign http://us.archive.ubuntu.com jaunty/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com jaunty/universe Translation-en_US   
Ign http://us.archive.ubuntu.com jaunty/multiverse Translation-en_US 
Hit http://us.archive.ubuntu.com jaunty-updates Release.gpg          
Ign http://us.archive.ubuntu.com jaunty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com jaunty-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-backports Release.gpg      
Ign http://security.ubuntu.com jaunty-security/restricted Translation-en_US
Ign http://security.ubuntu.com jaunty-security/universe Translation-en_US
Ign http://security.ubuntu.com jaunty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com jaunty-security Release               
Hit http://archive.canonical.com jaunty Release                                
Hit http://packages.medibuntu.org jaunty Release                               
Ign http://us.archive.ubuntu.com intrepid-backports/main Translation-en_US     
Ign http://us.archive.ubuntu.com intrepid-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-backports/universe Translation-en_US 
Ign http://us.archive.ubuntu.com intrepid-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com jaunty Release                                
Hit http://us.archive.ubuntu.com jaunty-updates Release                        
Hit http://security.ubuntu.com jaunty-security/main Packages                   
Hit http://archive.canonical.com jaunty/partner Packages                       
Hit http://packages.medibuntu.org jaunty/free Packages                         
Hit http://us.archive.ubuntu.com intrepid-backports Release          
Hit http://security.ubuntu.com jaunty-security/restricted Packages             
Hit http://security.ubuntu.com jaunty-security/main Sources          
Hit http://security.ubuntu.com jaunty-security/restricted Sources    
Hit http://security.ubuntu.com jaunty-security/universe Packages     
Hit http://packages.medibuntu.org jaunty/non-free Packages           
Hit http://us.archive.ubuntu.com jaunty/main Packages                
Hit http://us.archive.ubuntu.com jaunty/restricted Packages
Hit http://us.archive.ubuntu.com jaunty/main Sources
Hit http://us.archive.ubuntu.com jaunty/restricted Sources
Hit http://us.archive.ubuntu.com jaunty/universe Packages
Hit http://us.archive.ubuntu.com jaunty/universe Sources
Hit http://security.ubuntu.com jaunty-security/universe Sources
Hit http://security.ubuntu.com jaunty-security/multiverse Packages
Hit http://security.ubuntu.com jaunty-security/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty/multiverse Sources
Hit http://us.archive.ubuntu.com jaunty-updates/main Packages
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Packages
Hit http://us.archive.ubuntu.com jaunty-updates/main Sources
Hit http://us.archive.ubuntu.com jaunty-updates/restricted Sources
Hit http://us.archive.ubuntu.com jaunty-updates/universe Packages
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Packages
Hit http://us.archive.ubuntu.com jaunty-updates/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-backports/main Packages
Hit http://us.archive.ubuntu.com intrepid-backports/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-backports/universe Packages
Hit http://us.archive.ubuntu.com intrepid-backports/multiverse Packages
Reading package lists... Done
lightening@lightening-desktop:~$ 

```

---

### Post by lotusalive on 2009-12-27
Is it just that for Jaunty, the only Repo currently available is now: [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner ? ?

---

### Post by lavinog on 2009-12-27
> **lotusalive said:**
> 
When I go to Syn Pkg Mgr Repositories, **[http://archive.ubuntu.com/ubuntu/jaunty](http://archive.ubuntu.com/ubuntu/jaunty) main** is unchecked, and when I Add it, give the APT line, it will not give me the option to add it. 

What do you mean by "give the APT line?"
Are you trying to manually add the repo under the other software tab, or are you using the check boxes under the ubuntu software tab? (I am using karmic so the labels might be different...see screenshot)

---

### Post by lotusalive on 2009-12-27
Yeah, I was trying to manually Add the Repo, by checking the box, but then it asks for the 'APT line,' which is just the Repo http location, but then that box of the 'APT line' does not give me a live Add Button...  (It's there, but won't activate.) If I just leave it checked and Close, it locks up Synaptic with that SAME E: line 54 Msg !  

So, then, I went to the site of the Jaunty Main on the Internet and I got a 404: [http://archive.ubuntu.com/ubuntu/jaunty%20main](http://archive.ubuntu.com/ubuntu/jaunty%20main)  (* I don't know why this url is adding a '%20main' at the end, since it's not there on the url, only shows up when I Copy and Paste it here...) ! 

Not Found The requested URL /ubuntu/jaunty main was not found on this server.  Apache/2.2.8 (Ubuntu) Server at archive.ubuntu.com Port 80  

So, I assume the Repo is no longer available ? ? :confused:

---

### Post by lavinog on 2009-12-27
its there...its under [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/)
but you shouldn't add it manually.
the the apt line isn't looking just for a url:
> 
The APT line includes the type, location and components of a repository, for example  'deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main'.
so if you want to try it try:
```

deb http://archive.ubuntu.com/ubuntu/ jaunty main

```

BTW: %20 is a code for a space character since spaces are not allowed in urls.  That is why the %20 appeared.  The space is required for the repository list.

---

### Post by lotusalive on 2009-12-27
Well, thanks for that info.  I'm Still getting this problem.  (I always thought my root p/w is the same as my install password... Is that not so ?  Otherwise, what would it be, since it never asks me to make another 'root p/w' ?) 

```
 lightening@lightening-desktop:~$ su
Password: 
su: Authentication failure
lightening@lightening-desktop:~$ sudo -i
[sudo] password for lightening: 
pam_mount(pam_mount.c:100): unknown pam_mount option "use_first_pass"
root@lightening-desktop:~# deb http://archive.ubuntu.com/ubuntu/ jaunty main
-bash: deb: command not found
root@lightening-desktop:~# 

root@lightening-desktop:~# sudo apt-get deb http://archive.ubuntu.com/ubuntu/ jaunty main
E: Invalid operation deb
root@lightening-desktop:~# 

```

---

### Post by lotusalive on 2009-12-28
Will someone help me to understand my Network Connection ?  I don't know why, but Eth0 was at 'never' and yet I was still able to connect to the Internet...  I deleted that Eth0, since it wasn't working anyway, and re-established with Wired Connection 1.  


Yet, I still cannot Add [http://archive.ubuntu.com/ubuntu/jaunty](http://archive.ubuntu.com/ubuntu/jaunty) main, not with System>Enable Software Sources and not with System>Configure Software Sources and Updates. 

```
ightening@lightening-desktop:~$ sudo apt-get upgrade
[sudo] password for lightening: 
E: Malformed line 54 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
lightening@lightening-desktop:~$ gksudo gedit /etc/apt/sources.list
lightening@lightening-desktop:~$ gksudo gedit /etc/apt/sources.list
lightening@lightening-desktop:~$ gksudo gedit /etc/apt/sources.list
lightening@lightening-desktop:~$ 

```

Do I have to RE-INSTALL ?:confused:

---

### Post by 3rdalbum on 2009-12-28
> **lotusalive said:**
> Well, thanks for that info.  I'm Still getting this problem.  (I always thought my root p/w is the same as my install password... Is that not so ?  Otherwise, what would it be, since it never asks me to make another 'root p/w' ?) 

```
 lightening@lightening-desktop:~$ su
Password: 
su: Authentication failure
lightening@lightening-desktop:~$ sudo -i
[sudo] password for lightening: 
pam_mount(pam_mount.c:100): unknown pam_mount option "use_first_pass"
root@lightening-desktop:~# deb http://archive.ubuntu.com/ubuntu/ jaunty main
-bash: deb: command not found
root@lightening-desktop:~# 

root@lightening-desktop:~# sudo apt-get deb http://archive.ubuntu.com/ubuntu/ jaunty main
E: Invalid operation deb
root@lightening-desktop:~# 

```

No - put that line into the System > Administration > Software Sources program, under "third party software" tab.

Manage all your repositories from this program.

The reason why the Add button wasn't enabled before was because all software sources lines must begin in "deb" or "deb-src" - the Software Sources program will not let you add an invalid line, which is brilliant.

Also, don't use "su" - use "sudo -i" (or run a single command with the word "sudo" before the command).

---

### Post by lotusalive on 2009-12-28
So sorry 3rdalbum, I just don't understand your instruction.  

When I go to Sys > Software Sources, either choice, and check it, it will not add the Repo without the E: line 54 msg, and crashes Synaptic Pkg Mgr, at which point, I have to repeat the gksudo process to 'uncomment' the line, just to make the SPM usable again.  

This process just doesn't fix the Repo problem.

(p.s.:  I never touched ANY of my Repositories on this re-install that I did just a few days ago.)

When I try to add the Repo, the Apt Line is fine, until it asks me to 'Reload,' at which point it gives me only THIS Error: 

[B][U]"Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."[/U][/B]

Aghhh, HELP ! lol...

```
# This is my gksudo gedit /etc/apt/sources.list...

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu jaunty partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://us.archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://us.archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb http://archive.ubuntu.com/ubuntu/jaunty main

deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports restricted main multiverse universe
```

Is there anything else I can 'uncomment' ??

---

### Post by lotusalive on 2009-12-28
I'm going to work on how my Network Connection is connected/malfunctioning, in the Help Manual, to see if this can be corrected...  All suggestions, knowledge, welcome...

---

### Post by lavinog on 2009-12-28
> **lotusalive said:**
> Yeah, I was trying to manually Add the Repo, by checking the box, but then it asks for the 'APT line,' which is just the Repo http location, but then that box of the 'APT line' does not give me a live Add Button...  (It's there, but won't activate.) If I just leave it checked and Close, it locks up Synaptic with that SAME E: line 54 Msg !  


What 3rdalbum and I are trying to say is that the APT line needs to start with deb not http.
From your sources.list: 
```

deb http://archive.ubuntu.com/ubuntu/jaunty main

```
This is not a valid entry, and I think it came from you trying to manually add it.
remove it and the blank line following it.

I do not understand why you are trying to manually add a main repository?
Can you post a screenshot of the software sources showing the other software tab?

for your network issue you should really start a new thread...otherwise things will get really confusing.
When you start that thread, post the output of ifconfig

---

### Post by lotusalive on 2009-12-28
> What 3rdalbum and I are trying to say is that the APT line needs to start with deb not http.
From your sources.list:
Code:

deb [http://archive.ubuntu.com/ubuntu/jaunty](http://archive.ubuntu.com/ubuntu/jaunty) main

This is not a valid entry, and I think it came from you trying to manually add it.
remove it and the blank line following it.

I do not understand why you are trying to manually add a main repository?
Can you post a screenshot of the software sources showing the other software tab? 

Well now I'm really confused, that you don't understand why I should want that main repository for Jaunty to be active in my installation of Ubuntu Jaunty... Am I wrong to think it is the Source of my installation packages ?  I do not understand why it is NOT active !  Are you telling me Jaunty Main Repo is not required for my Jaunty installation to be complete and working properly ?:confused:

I have APT line written the code above correctly 3 times now, and receiving the same Network Error Msg, which is WHY I posted the question here.  Then I have been forced to follow the gksudo gedit command you gave me here to get my SPM back to working, at all, after uncommenting the line 54, again.

I will ask the Network Question in a different Thread, as you ask, but since it was the msg that came with trying to Add Jaunty Main, I thought it might be the reason that I cannot Add it.  If it is not necessary to have Jaunty Main, then I have misunderstood how this installation works completely !  And I apologize for wasting your time in asking for help on this question, if Jaunty Main is totally not required !

---

### Post by lavinog on 2009-12-28
You don't need to manually add the main repository.  It already was added with this line:
```

deb http://us.archive.ubuntu.com/ubuntu/ jaunty-backports restricted main multiverse universe
```
The APT line is used for PPAs and third party repositories...not the main.

---

### Post by lotusalive on 2009-12-29
Then WHY does it not appear checked in EITHER of the lists of Software Sources ?  That's why I was worried about it in the first place !:confused:

And you're not gonna believe this... lol, this is the new error msg from Syn Pkg Mgr: 

W: Duplicate sources.list entry [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages)  (And, of course I couldn't find the line of code in gedit, not even once ? ?)

---

### Post by lavinog on 2009-12-29
Could be a bug, or it could be because it doesn't want to override any manual changes.

What if you erased the sources.list and created a new one with the software sources application.  I just verified it worked in lucid.  I don't have jaunty machine setup at the moment so you should backup your current sources.list

```

sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
sudo rm /etc/apt/sources.list

```
Then startup the software sources application and check the repositories you want.
Let me know if it worked.

---

### Post by lotusalive on 2009-12-29
It didn't look like it did anything in the Terminal, but now in SMP, Third-party Software, all that even shows up, (under both Main Server and Server for US), and is checked is:

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner, 
Medibuntu - Ubuntu 9.04 "jaunty jackalope" free non-free
(and unchecked: Medibuntu (source) - Ubuntu 9.04 "jaunty jackalope" free non-free)

But under Enable or Disable Software Sources, more Repos appear, and are checked than in Synaptics.  Is this about as correct as I can make it ? lol :)

---

