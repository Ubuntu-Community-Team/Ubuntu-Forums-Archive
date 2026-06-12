---
title: "update manager waiting..."
date: 2010-12-11
forum: General Help
---

### Post by steveredshaw on 2010-12-11
Update manager reports new updates to install however when I try to install these it reports that it is waiting for apt-get to exit. As I understand it apt-get is the software manager installer and probably the update manager aswell.

The only way I can get round this it seems is to reboot the computer. I don't know why the Update Manager reports that apt-get is running. Can I close apt-get through the terminal? Would that enable Update Manager to proceed?

---

### Post by Quackers on 2010-12-11
You didn't have Synaptic or Software Sources open at the same time did you?

---

### Post by sikander3786 on 2010-12-11
The output of this command will also help diagnose the problem.

Applications > Accessories > Terminal:
```
sudo apt-get update
```

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

### Post by karthick87 on 2010-12-11
Do you have synaptic or the ubuntu software center open?Have a look under processes.
  To see running processes goto System-->Administration-->System Monitor
  [IMG]http://i.imgur.com/IyOwl.png[/IMG]
    Search for the processes that says apt-get or synaptic.If you find any process,select the process and click End Process.If no process were running but still if you cant install any packages then type the following in terminal..
```
sudo rm /var/lib/dpkg/lock
```

This will remove the lock,now you can install packages..
  Also See this [post]("http://ubuntuforums.org/showpost.php?p=9137287&postcount=2")

---

### Post by steveredshaw on 2010-12-11
as far as I can tell software manager is not running

couldn't run this

```
sudo apt-get update
```
as it got to a stage of asking for DVD disc, but when I inserted the installation disc, it still promted to insert the disc!!

I will try this

```
sudo rm /var/lib/dpkg/lock
```if Update Manager repeats the previous behaviour - thanks for the help - I may be back!!

---

### Post by sikander3786 on 2010-12-11
> couldn't run this

sudo apt-get update

as it got to a stage of asking for DVD disc, but when I inserted the installation disc, it still promted to insert the disc!!

That is also a part of the problem.

Go to Software Center > Edit > Software Sources > Other Software Tab and uncheck CD/DVD Rom. Try the apt-get update command again and please remember, in order to help you, we need to see the output whatever it is.

Thanks.

---

### Post by steveredshaw on 2010-12-11
here is output from sudo apt-get update;

```
Hit http://archive.canonical.com maverick Release.gpg
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en       
Ign http://archive.canonical.com/ubuntu/ maverick/partner Translation-en_GB    
Hit http://security.ubuntu.com maverick-security Release.gpg                   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en   
Ign http://security.ubuntu.com/ubuntu/ maverick-security/main Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick Release.gpg                          
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en          
Get:1 http://gb.archive.ubuntu.com/ubuntu/ maverick/main Translation-en_GB [94.5kB]
Hit http://archive.canonical.com maverick Release                              
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/multiverse Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/restricted Translation-en_GB
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en
Ign http://security.ubuntu.com/ubuntu/ maverick-security/universe Translation-en_GB
Hit http://security.ubuntu.com maverick-security Release                       
Hit http://archive.canonical.com maverick/partner i386 Packages                
Hit http://security.ubuntu.com maverick-security/main Sources                  
Hit http://linux.dropbox.com maverick Release.gpg                
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en              
Ign http://linux.dropbox.com/ubuntu/ maverick/main Translation-en_GB           
Hit http://security.ubuntu.com maverick-security/restricted Sources
Hit http://security.ubuntu.com maverick-security/universe Sources
Hit http://security.ubuntu.com maverick-security/multiverse Sources
Hit http://security.ubuntu.com maverick-security/main i386 Packages
Hit http://security.ubuntu.com maverick-security/restricted i386 Packages
Hit http://security.ubuntu.com maverick-security/universe i386 Packages
Hit http://security.ubuntu.com maverick-security/multiverse i386 Packages
Hit http://linux.dropbox.com maverick Release                    
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en
Get:2 http://gb.archive.ubuntu.com/ubuntu/ maverick/multiverse Translation-en_GB [91.2kB]
Hit http://linux.dropbox.com maverick/main i386 Packages                       
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en
Get:3 http://gb.archive.ubuntu.com/ubuntu/ maverick/restricted Translation-en_GB [2,332B]
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en
Get:4 http://gb.archive.ubuntu.com/ubuntu/ maverick/universe Translation-en_GB [32.0kB]
Hit http://gb.archive.ubuntu.com maverick-updates Release.gpg             
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/main Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en
Ign http://gb.archive.ubuntu.com/ubuntu/ maverick-updates/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com maverick Release       
Hit http://gb.archive.ubuntu.com maverick-updates Release
Hit http://gb.archive.ubuntu.com maverick/main Sources
Hit http://gb.archive.ubuntu.com maverick/restricted Sources
Hit http://gb.archive.ubuntu.com maverick/universe Sources
Hit http://gb.archive.ubuntu.com maverick/multiverse Sources
Hit http://gb.archive.ubuntu.com maverick/main i386 Packages
Hit http://gb.archive.ubuntu.com maverick/restricted i386 Packages
Hit http://gb.archive.ubuntu.com maverick/universe i386 Packages
Hit http://gb.archive.ubuntu.com maverick/multiverse i386 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/main Sources
Hit http://gb.archive.ubuntu.com maverick-updates/restricted Sources
Hit http://gb.archive.ubuntu.com maverick-updates/universe Sources
Hit http://gb.archive.ubuntu.com maverick-updates/multiverse Sources
Hit http://gb.archive.ubuntu.com maverick-updates/main i386 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/restricted i386 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/universe i386 Packages
Hit http://gb.archive.ubuntu.com maverick-updates/multiverse i386 Packages
Fetched 220kB in 1s (127kB/s)
Reading package lists... Done
```

---

### Post by sikander3786 on 2010-12-11
The output seems pretty ok at the moment. Did you try update manager once more? Is it still saying the error "waiting for apt-get to exit"? Or is it solved?

---

