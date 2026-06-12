---
title: "parsing errors?"
date: 2011-06-11
forum: General Help
---

### Post by stevovets on 2011-06-11
my windows have been becoming unresponsive more and more.  I ran KlamAV and had an error reported.  When I ran package manager it reports:

E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

It says that installed packages could have unmet dependencies.  It also won't let me open the update manager.

Any ideas?

---

### Post by wildmanne39 on 2011-06-11
> **stevovets said:**
> my windows have been becoming unresponsive more and more.  I ran KlamAV and had an error reported.  When I ran package manager it reports:

E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

It says that installed packages could have unmet dependencies.  It also won't let me open the update manager.

Any ideas?
Hi, try this in a terminal.
```
sudo apt-get install -f install
```
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by stevovets on 2011-06-11
It seems that every code that i put in, it gets stuck while reading the package lists.
You probably don't need the entire list but this is everything from the terminal


> sudo apt-get install -f install
doops@doops:~$ sudo apt-get install -f install
[sudo] password for doops: 
Sorry, try again.
[sudo] password for doops: 
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
doops@doops:~$ sudo apt-get update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_US   
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US   
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Get:4 [http://dl.google.com](http://dl.google.com) stable/main Packages [764B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [44.7kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release 
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [194kB]
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [44.7kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources            
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [502kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]  
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [58.2kB]         
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [14B]      
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [71.5kB]  
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [21.3kB]     
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [4,555B]  
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [1,745B]   
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [3,240B] 
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [194kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [1,443B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [204kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [74.8kB]
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [10.5kB]
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [5,061B]
Fetched 1,437kB in 3s (383kB/s)                       
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
doops@doops:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package list

---

### Post by stevovets on 2011-06-12
my  windows have been becoming unresponsive more and more.  I ran KlamAV  and had an error reported.  When I ran package manager it reports:

E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

It says that installed packages could have unmet dependencies.  It also won't let me open the update manager.

Any ideas?

---

### Post by wildmanne39 on 2011-06-12
> **stevovets said:**
> It seems that every code that i put in, it gets stuck while reading the package lists.
You probably don't need the entire list but this is everything from the terminal

Hi, try 
```
sudo dpkg --configure -a
```
```
sudo apt-get clean
```
```
sudo rm -r /var/lib/apt/lists/* -vf
```
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by stevovets on 2011-06-12
got this

> doops@doops:~$ sudo dpkg --configure -a
[sudo] password for doops: 
dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/status': Input/output error
doops@doops:~$ sudo apt-get clean
E: Lists directory /var/lib/apt/lists/partial is missing.
doops@doops:~$ sudo rm -r /var/lib/apt/lists/* -vf
removed `/var/lib/apt/lists/lock'
doops@doops:~$ sudo apt-get update && sudo apt-get upgrade
E: Lists directory /var/lib/apt/lists/partial is missing.

---

### Post by Wim Sturkenboom on 2011-06-12
You might have a HD that is on its way out. I suggest that you run the tools of your harddisk manufacturer to check it out.

---

### Post by linuxinstalledfromhdd on 2011-06-12
> **Wim Sturkenboom said:**
> You might have a HD that is on its way out. I suggest that you run the tools of your harddisk manufacturer to check it out.

+2

I would think it might be hardware first, unless you changed some of your settings or installed something new recently? 

:popcorn:

---

### Post by wildmanne39 on 2011-06-12
> **stevovets said:**
> got this
Hi, try this one last thing.
```
sudo rm /var/lib/apt/lists/partial/*
```
```
sudo apt-get install -f install
```
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by stevovets on 2011-06-12
still having problems reading package list

> doops@doops:~$ sudo rm /var/lib/apt/lists/partial/*
[sudo] password for doops: 
rm: cannot remove `/var/lib/apt/lists/partial/*': No such file or directory
doops@doops:~$ sudo apt-get install -f install
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
doops@doops:~$ sudo apt-get update && sudo apt-get upgrade
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_US   
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]                             
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [764B]                         
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]     
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [189B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [44.7kB]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg [198B]
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release [57.2kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [194kB]  
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [58.2kB]  
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [14B]      
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [71.5kB]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [21.3kB]     
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [4,555B]
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [1,745B]   
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release [44.7kB]             
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages [1,386kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages [6,208B]         
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources [659kB]                 
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources [3,775B]          
Get:22 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages [5,448kB]          
Get:23 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources [3,165kB]           
Get:24 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages [180kB]          
Get:25 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources [119kB]           
Get:26 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [502kB]        
Get:27 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [3,240B] 
Get:28 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [194kB]         
Get:29 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [1,443B]  
Get:30 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [204kB]    
Get:31 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [74.8kB]    
Get:32 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [10.5kB] 
Get:33 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [5,061B]
Fetched 12.5MB in 37s (329kB/s)   
Reading package lists... Error!
E: Read error - read (5: Input/output error)
E: The package lists or status file could not be parsed or opened.
doops@doops:~$ 


what should i do now?

---

### Post by Rubi1200 on 2011-06-12
I respectfully disagree with the 2 previous posts about the source of the problem.

Of course, you are more than welcome to check the disk integrity, but I suggest you try the solution in post # 3 here (You need to replace aptitude with apt-get):
[https://answers.launchpad.net/ubuntu/+source/update-manager/+question/66668](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/66668)

---

### Post by coffeecat on 2011-06-12
@stevovets, whilst hardware faults always need to be kept in mind as a possibility when faced with problems, I suggest you look through Rubi1200's link first. If your problem is the same, then the commands there would hopefully fix it for you. Also, have a look at the last post in that link, the page it links to, here:

[https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

One for your bookmarks. In fact, one for my bookmarks! :)

I also found this fairly recent thread, but I don't think it adds anything to the link that Rubi1200 posted:

[http://ubuntuforums.org/showthread.php?t=1679274](http://ubuntuforums.org/showthread.php?t=1679274)

If those commands don't work for you, post the output of:

```
cat /etc/apt/sources.list
```And also, which version of Ubuntu are you running?

**EDIT**: also, what was the exact message klamav reported?

---

### Post by Wim Sturkenboom on 2011-06-12
> **Rubi1200 said:**
> I respectfully disagree with the 2 previous posts about the source of the problem.
You're welcome to disagree :D

However, I've seen several PCs (including my company laptop, my wifes laptop and my daughter in law's desktop) where a sluggish Windows behavior was caused by a bad HD; fresh windows installs did not help. Add to that the read errors under Linux, and it was simply my first thought.

---

### Post by Elfy on 2011-06-12
Please do not post duplicates, it dilutes community effort.

Threads merged

---

### Post by coffeecat on 2011-06-12
> **Wim Sturkenboom said:**
> where a sluggish Windows behavior was caused by a bad HD; fresh windows installs did not help.

Indeed. But when the OP said...

> my windows have been becoming unresponsive more and more.... do they mean Windows or windows? :) I must admit when I first read that, like you I took it to mean Windows the operating system, but then I wondered how klamav and the Ubuntu package manager could be running in Windows! So then I read it to mean that the OP's application windows in Ubuntu are unresponsive. I could be wrong so I think we need more information.

@stevovets, by "unresponsive windows" do you mean your application windows in Ubuntu, or Windows the operating system? Do you have (Microsoft) Windows on that machine? If so, is it running OK?

---

### Post by stevovets on 2011-06-12
> @stevovets, by "unresponsive windows" do you mean your application  windows in Ubuntu, or Windows the operating system? Do you have  (Microsoft) Windows on that machine? If so, is it running OK?

Sorry about that, I meant the application windows.  I don't have Windows running on my computer.

I ran the Troubleshooting method Rubi1200 suggested.  I posted my results to Launchpad here: [https://answers.launchpad.net/ubuntu/+question/161194](https://answers.launchpad.net/ubuntu/+question/161194)

---

### Post by wildmanne39 on 2011-06-12
Hi, thank you Ruby1200 and Coffeecat I appreciate the help resolving this problem for the OP, I just could not seem to get the problem solved. Your help is always appreciated and if I am wrong about something please let me know so I will have a better understanding the next time. Thanks again.

---

### Post by coffeecat on 2011-06-12
> **wildmanne39 said:**
> Hi, thank you Ruby1200 and Coffeecat I appreciate the help resolving this problem for the OP, I just could not seem to get the problem solved. Your help is always appreciated and if I am wrong about something please let me know so I will have a better understanding the next time. Thanks again.

Hi, I think you were helping out on one of the OP's two threads and Rubi1200 and I were trying to help on the other, both of which have now been (rightly) merged. Which makes this combined thread rather confusing now. Since the OP has now taken this to answers.launchpad, I'm not sure what else we can do. :(

---

### Post by wildmanne39 on 2011-06-12
> **coffeecat said:**
> Hi, I think you were helping out on one of the OP's two threads and Rubi1200 and I were trying to help on the other, both of which have now been (rightly) merged. Which makes this combined thread rather confusing now. Since the OP has now taken this to answers.launchpad, I'm not sure what else we can do. :(
Hi, I noticed that the OP went to launch pad but I did not know the OP had 2 threads, that really does make it harder. I think I was on the right track but I just could not quite solved it.

---

### Post by stevovets on 2011-06-12
sorry about all the confusion with the double posts, my mistake.  I appreciate all the help though.  Still haven't gotten it all sorted out with Launchpad either though.  

A couple of weeks ago I downloaded an application to allow use my webcam with Google.  That's the only real recent addition to my computer I can think of.  Getting a lot of freezing on my computer still and can't upgrade anything

---

### Post by stevovets on 2011-06-12
correction:  now I can access my update manager and package manager.  Says I have 729 broken packages but it doesn't seem to let me fix them.  Can't update anything either.  Gives me this message:

> E: Could not perform immediate configuration on 'libc6'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)

---

### Post by wildmanne39 on 2011-06-12
> **stevovets said:**
> correction:  now I can access my update manager and package manager.  Says I have 729 broken packages but it doesn't seem to let me fix them.  Can't update anything either.  Gives me this message:Hi,open synaptic and click on edit then on fix broken packages and see if it will fix them that way.

---

### Post by stevovets on 2011-06-12
it says in Synaptic that it succesfully fixed all dependencies.  But then when I open update manager, it says that I have 729 broken packages and to use the "Broken" filter to locate them.  IDK where this filter is

---

### Post by wildmanne39 on 2011-06-12
> **stevovets said:**
> it says in Synaptic that it succesfully fixed all dependencies.  But then when I open update manager, it says that I have 729 broken packages and to use the "Broken" filter to locate them.  IDK where this filter is
Hi, that problem sure is persisting, have you tried to restart your system after all the commands you ran to see if it clears the problem up?

---

### Post by stevovets on 2011-06-12
haha, that hadn't occurred to me, but i just tried it.  no such luck.  Launchpad seems to have forgotten about me also.

---

### Post by wildmanne39 on 2011-06-13
> **stevovets said:**
> haha, that hadn't occurred to me, but i just tried it.  no such luck.  Launchpad seems to have forgotten about me also.
Hi, the only thing I can say is that we are getting closer I think. Lets try
sudo mkdir /var/lib/apt/lists/partial
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install -f

---

### Post by stevovets on 2011-06-13
no change, still receiving the same error.  Here's the terminal read-out
> doops@doops:~$ sudo mkdir /var/lib/apt/lists/partial
[sudo] password for doops: 
mkdir: cannot create directory `/var/lib/apt/lists/partial': File exists
doops@doops:~$ sudo dpkg --configure -a
dpkg: parse error, in file '/var/lib/dpkg/status' near line 18945 package 'mawk':
 EOF during value of field `Description' (missing final newline)
doops@doops:~$ sudo aptitude update
Writing extended state information... Done
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [197B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg [198B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release [44.7kB]
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_US
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]    
Get:5 [http://dl.google.com](http://dl.google.com) stable/main Packages [764B]                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages [502kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages [3,240B]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources [194kB]
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources [1,443B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages [203kB]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources [74.8kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages [10.5kB]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources [5,061B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources
Fetched 1,041kB in 5s (180kB/s)
Reading package lists... Done             

doops@doops:~$ sudo aptitude upgrade
W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
open: 78; closed: 318; defer: 531; conflict: 1                                 .Resolving dependencies...
open: 78; closed: 389; defer: 679; conflict: 1                                 .Resolving dependencies...
open: 77; closed: 441; defer: 784; conflict: 1                                 .Resolving dependencies...
Resolving dependencies...
open: 29; closed: 771; defer: 1324; conflict: 1                                .The following NEW packages will be installed:
  apport{a} apt-utils{a} aptdaemon{a} aptitude{a} aspell{a} avahi-daemon{a} 
  bash{a} bash-completion{a} binutils{a} bogofilter-bdb{a} brltty{a} 
  bsdmainutils{a} busybox-initramfs{a} busybox-static{a} ca-certificates{a} 
  ca-certificates-java{a} cabextract{a} cheese-common{a} 
  compiz-fusion-plugins-main{a} compiz-gnome{a} 
  compizconfig-backend-gconf{a} console-terminus{a} couchdb-bin{a} cpio{a} 
  cpp{a} cron{a} cups{a} dbus-x11{a} debconf-english{a} defoma{a} 
  dhcp3-common{a} docbook-xml{a} dosfstools{a} dpkg{a} e2fsprogs{a} 
  eject{a} erlang-crypto{a} erlang-runtime-tools{a} espeak-data{a} 
  findutils{a} firefox{a} fontconfig-config{a} foomatic-db{a} 
  foomatic-db-engine{a} foomatic-filters{a} freepats{a} ftp{a} 
  fuse-utils{a} gcc-4.4-base{a} gconf-defaults-service{a} gconf2{a} 
  ghostscript{a} ghostscript-cups{a} gksu{a} gnome-about{a} 
  gnome-desktop-data{a} gnome-panel-data{a} gnome-session-bin{a} 
  gnome-terminal-data{a} gnupg{a} gnupg-curl{a} groff-base{a} 
  gstreamer0.10-gnonlin{a} gstreamer0.10-plugins-base{a} 
  gstreamer0.10-plugins-good{a} gstreamer0.10-pulseaudio{a} 
  gstreamer0.10-tools{a} gstreamer0.10-x{a} gvfs{a} gzip{a} 
  hunspell-en-ca{a} icedtea-6-jre-cacao{a} info{a} initscripts{a} 
  insserv{a} iptables{a} iputils-ping{a} iputils-tracepath{a} iso-codes{a} 
  kbd{a} kdebase-runtime-data{a} kdelibs-data{a} kdelibs5-data{a} 
  kdepimlibs5{a} language-pack-gnome-en{a} language-selector-common{a} 
  launchpad-integration{a} libaa1{a} libaccess-bridge-java{a} 
  libaccess-bridge-java-jni{a} libacl1{a} libarchive1{a} libatk1.0-0{a} 
  libatk1.0-data{a} libaudio2{a} libavahi-client3{a} 
  libavahi-common-data{a} libavahi-common3{a} libavahi-core6{a} 
  libavahi-gobject0{a} libavformat52{a} libbeagle1{a} libblkid1{a} 
  libbonoboui2-common{a} libboost-program-options1.40.0{a} 
  libbrasero-media0{a} libbrlapi0.5{a} libbsd0{a} libbz2-1.0{a} libc-bin{a} 
  libc6{a} libc6-i686{a} libcaca0{a} libcairo-perl{a} libcamel1.2-14{a} 
  libcanberra-gtk0{a} libcanberra0{a} libcap2{a} libcdparanoia0{a} 
  libclucene0ldbl{a} libcompizconfig0{a} libcouchdb-glib-1.0-2{a} 
  libcroco3{a} libcryptui0{a} libcupscgi1{a} libcupsimage2{a} 
  libcupsppdc1{a} libcurl3{a} libcwidget3{a} libdatrie1{a} libdb4.8{a} 
  libdbusmenu-gtk1{a} libdbusmenu-qt2{a} libdc1394-22{a} 
  libdevkit-power-gobject1{a} libdjvulibre-text{a} libdjvulibre21{a} 
  libdrm-intel1{a} libdrm-nouveau1{a} libdvdnav4{a} libebackend1.2-0{a} 
  libedata-book1.2-2{a} libedata-cal1.2-6{a} libedataserverui1.2-8{a} 
  libedit2{a} libept0{a} libesd0{a} libexiv2-6{a} libfaac0{a} libfaad2{a} 
  libfile-copy-recursive-perl{a} libfontenc1{a} libfs6{a} libgadu3{a} 
  libgail18{a} libgcj-bc{a} libgcj-common{a} libgdata-google1.2-1{a} 
  libgdata1.2-1{a} libglade2.0-cil{a} libglib2.0-0{a} libglib2.0-cil{a} 
  libglibmm-2.4-1c2a{a} libglitz1{a} libgmime-2.4-2{a} libgnome-keyring0{a} 
  libgnome-media0{a} libgnome-vfs2.0-cil{a} libgnome2-0{a} 
  libgnome2.24-cil{a} libgnomecanvas2-common{a} libgnomekbd-common{a} 
  libgnomeui-common{a} libgnomevfs2-0{a} libgnutls26{a} libgomp1{a} 
  libgphoto2-2{a} libgphoto2-port0{a} libgpm2{a} libgsl0ldbl{a} 
  libgstreamer0.10-0{a} libgtk2-perl{a} libgtk2.0-bin{a} 
  libgtkhtml3.14-19{a} libgtksourceview2.0-0{a} 
  libgtksourceview2.0-common{a} libgupnp-1.0-3{a} libgutenprint2{a} 
  libgweather-common{a} libhpmud0{a} libhtml-parser-perl{a} 
  libhtml-tagset-perl{a} libhyphen0{a} libice6{a} libicu42{a} libid3tag0{a} 
  libido-0.1-0{a} libiec61883-0{a} libijs-0.35{a} libilmbase6{a} 
  libindicate4{a} libindicator0{a} libio-string-perl{a} libiptcdata0{a} 
  libjasper1{a} libkate1{a} libkrb5-3{a} liblaunchpad-integration1{a} 
  liblcms1{a} libldap-2.4-2{a} liblircclient0{a} liblocale-gettext-perl{a} 
  liblockfile1{a} liblouis-data{a} liblouis0{a} liblualib50{a} liblzma1{a} 
  libmad0{a} libmeanwhile1{a} libmetacity-private0{a} libmimic0{a} 
  libmjpegtools-1.9{a} libmng1{a} libmodplug0c2{a} libmono-addins0.2-cil{a} 
  libmono-cairo2.0-cil{a} libmono-corlib2.0-cil{a} 
  libmono-i18n-west2.0-cil{a} libmono-security2.0-cil{a} 
  libmono-sharpzip2.84-cil{a} libmono-sqlite2.0-cil{a} 
  libmono-system-web2.0-cil{a} libmono-system2.0-cil{a} libmp3lame0{a} 
  libmpeg2-4{a} libmusicbrainz4c2a{a} libmysqlclient16{a} 
  libnautilus-extension1{a} libncursesw5{a} libnet-dbus-perl{a} 
  libnewt0.52{a} libnih-dbus1{a} libnih1{a} libnm-glib2{a} libnspr4-0d{a} 
  libnss-mdns{a} libnss3-1d{a} libntfs-3g75{a} libntfs10{a} libofa0{a} 
  libopencore-amrnb0{a} libopenexr6{a} libopenobex1{a} liborbit2{a} 
  libpackagekit-glib2-12{a} libpackagekit-qt-12{a} libpam-runtime{a} 
  libpangomm-1.4-1{a} libpaper1{a} libparse-debianchangelog-perl{a} 
  libpciaccess0{a} libpcre3{a} libpcsclite1{a} libphonon4{a} libpisock9{a} 
  libpixman-1-0{a} libplasma3{a} libplist1{a} libpng12-0{a} 
  libpolkit-backend-1-0{a} libpolkit-qt-1-0{a} libpoppler-glib4{a} 
  libpoppler5{a} libpostproc51{a} libpulse-browse0{a} libqt4-assistant{a} 
  libqt4-designer{a} libqt4-help{a} libqt4-qt3support{a} 
  libqt4-scripttools{a} libqt4-test{a} libqt4-xml{a} libqt4-xmlpatterns{a} 
  libraptor1{a} librasqal2{a} librsvg2-common{a} libsasl2-2{a} 
  libsasl2-modules{a} libschroedinger-1.0-0{a} libsdl1.2debian-all{a} 
  libselinux1{a} libsensors4{a} libsidplay1{a} libsigc++-2.0-0c2a{a} 
  libsilcclient-1.1-3{a} libslang2{a} libsm6{a} libsndfile1{a} 
  libspectre1{a} libss2{a} libssh-4{a} libstartup-notification0{a} 
  libstdc++6{a} libstlport4.6ldbl{a} libstreamanalyzer0{a} 
  libsub-name-perl{a} libtag1c2a{a} libtalloc2{a} libtelepathy-farsight0{a} 
  libtext-charwidth-perl{a} libunique-1.0-0{a} libvisual-0.4-0{a} 
  libvisual-0.4-plugins{a} libvorbis0a{a} libvte9{a} libwebkit-1.0-2{a} 
  libwebkit-1.0-common{a} libwnck-common{a} libwnck22{a} libwpd8c2a{a} 
  libwrap0{a} libwww-perl{a} libx11-6{a} libx11-data{a} libx264-85{a} 
  libxau6{a} libxaw7{a} libxcursor1{a} libxdamage1{a} libxfixes3{a} 
  libxft2{a} libxklavier16{a} libxml-twig-perl{a} libxmu6{a} libxt6{a} 
  libxtst6{a} libxvidcore4{a} libxxf86vm1{a} libzephyr4{a} light-themes{a} 
  linux-headers-2.6.32-25{a} linux-headers-2.6.32-27{a} 
  linux-headers-2.6.32-29{a} linux-headers-2.6.32-32{a} lsof{a} ltrace{a} 
  make{a} media-player-info{a} mime-support{a} min12xxw{a} myspell-en-za{a} 
  nautilus{a} net-tools{a} openjdk-6-jre{a} openjdk-6-jre-headless{a} 
  openjdk-6-jre-lib{a} openoffice.org-base-core{a} openoffice.org-common{a} 
  openoffice.org-writer{a} openssh-client{a} oss-compat{a} 
  oxygen-icon-theme{a} p7zip-full{a} passwd{a} perl{a} phonon{a} 
  phonon-backend-null{a} pkg-config{a} plasma-scriptengine-javascript{a} 
  plymouth{a} plymouth-label{a} pnm2ppa{a} policykit-1{a} poppler-utils{a} 
  popularity-contest{a} powermgmt-base{a} pptp-linux{a} pulseaudio{a} 
  pulseaudio-esound-compat{a} python-apt{a} python-aptdaemon-gtk{a} 
  python-central{a} python-configglue{a} python-couchdb{a} python-crypto{a} 
  python-cups{a} python-cupshelpers{a} python-debian{a} 
  python-desktopcouch{a} python-desktopcouch-records{a} python-farsight{a} 
  python-gconf{a} python-glade2{a} python-gnomekeyring{a} python-gobject{a} 
  python-gst0.10{a} python-gtk2{a} python-gtksourceview2{a} 
  python-httplib2{a} python-launchpadlib{a} python-lazr.restfulclient{a} 
  python-libxml2{a} python-notify{a} python-oauth{a} python-openssl{a} 
  python-pam{a} python-problem-report{a} python-pygoocanvas{a} 
  python-pyinotify{a} python-qt4{a} python-simplejson{a} 
  python-telepathy{a} python-twisted-core{a} python-twisted-names{a} 
  python-ubuntuone-storageprotocol{a} python-uno{a} python-wadllib{a} 
  python-webkit{a} python-xapian{a} python-xdg{a} python2.6-minimal{a} 
  rarian-compat{a} readline-common{a} rtkit{a} samba-common-bin{a} 
  screen{a} sgml-data{a} software-properties-gtk{a} strace{a} syslinux{a} 
  system-config-printer-common{a} sysvinit-utils{a} time{a} totem-common{a} 
  tsconf{a} ttf-dejavu-core{a} ttf-dejavu-extra{a} ttf-opensymbol{a} 
  ubuntu-mono{a} ubuntu-system-service{a} udev{a} unattended-upgrades{a} 
  update-manager-kde{a} upower{a} upstart{a} usbmuxd{a} util-linux{a} 
  wbritish{a} wodim{a} x11-apps{a} x11-common{a} x11-xfs-utils{a} 
  x11-xserver-utils{a} xauth{a} xbitmaps{a} xdg-user-dirs{a} xdg-utils{a} 
  xfonts-75dpi{a} xfonts-encodings{a} xfonts-utils{a} xinput{a} xkb-data{a} 
  xml-core{a} xorg-docs-core{a} xserver-xorg-input-mouse{a} 
  xserver-xorg-video-ark{a} xserver-xorg-video-ati{a} 
  xserver-xorg-video-chips{a} xserver-xorg-video-cirrus{a} 
  xserver-xorg-video-geode{a} xserver-xorg-video-i128{a} 
  xserver-xorg-video-i740{a} xserver-xorg-video-intel{a} 
  xserver-xorg-video-mach64{a} xserver-xorg-video-mga{a} 
  xserver-xorg-video-neomagic{a} xserver-xorg-video-nouveau{a} 
  xserver-xorg-video-nv{a} xserver-xorg-video-r128{a} 
  xserver-xorg-video-s3{a} xserver-xorg-video-siliconmotion{a} 
  xserver-xorg-video-trident{a} xserver-xorg-video-tseng{a} xsltproc{a} 
  yelp{a} zenity{a} 
The following packages will be REMOVED:
  audacity-data{u} clamav{u} clamav-freshclam{u} grub-common{u} 
  krosspython{u} ktorrent-data{u} libclamav6{u} libflac++6{u} 
  libsolidcontrol4{u} libtommath0{u} libwxbase2.8-0{u} libwxgtk2.8-0{u} 
  libxcb-shm0{u} libxine1-console{u} libxine1-misc-plugins{u} os-prober{u} 
  pidgin-data{u} 
The following partially installed packages will be configured:
  flashplugin-installer sysv-rc 
0 packages upgraded, 486 newly installed, 17 to remove and 0 not upgraded.
Need to get 1,631kB/320MB of archives. After unpacking 1,161MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main debconf-english 1.5.28ubuntu4 [894B]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main libsdl1.2debian-all 1.2.14-4ubuntu1.1 [216kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe p7zip-full 9.04~dfsg.1-1 [1,404kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe phonon-backend-null 4:4.4.0-0ubuntu2 [10.3kB]
Fetched 1,631kB in 7s (215kB/s)                                                 
E: Could not perform immediate configuration on 'libc6'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file '/var/lib/dpkg/status' near line 18945 package 'mawk':
 EOF during value of field `Description' (missing final newline)
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

doops@doops:~$ sudo aptitude install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following NEW packages will be installed:
  apport{a} apt-utils{a} aptdaemon{a} aptitude{a} aspell{a} avahi-daemon{a} 
  bash{a} bash-completion{a} binutils{a} bogofilter-bdb{a} brltty{a} 
  bsdmainutils{a} busybox-initramfs{a} busybox-static{a} ca-certificates{a} 
  ca-certificates-java{a} cabextract{a} cheese-common{a} 
  compiz-fusion-plugins-main{a} compiz-gnome{a} 
  compizconfig-backend-gconf{a} console-terminus{a} couchdb-bin{a} cpio{a} 
  cpp{a} cron{a} cups{a} dbus-x11{a} debconf-english{a} defoma{a} 
  dhcp3-common{a} docbook-xml{a} dosfstools{a} dpkg{a} e2fsprogs{a} 
  eject{a} erlang-crypto{a} erlang-runtime-tools{a} espeak-data{a} 
  findutils{a} firefox{a} fontconfig-config{a} foomatic-db{a} 
  foomatic-db-engine{a} foomatic-filters{a} freepats{a} ftp{a} 
  fuse-utils{a} gcc-4.4-base{a} gconf-defaults-service{a} gconf2{a} 
  ghostscript{a} ghostscript-cups{a} gksu{a} gnome-about{a} 
  gnome-desktop-data{a} gnome-panel-data{a} gnome-session-bin{a} 
  gnome-terminal-data{a} gnupg{a} gnupg-curl{a} groff-base{a} 
  gstreamer0.10-gnonlin{a} gstreamer0.10-plugins-base{a} 
  gstreamer0.10-plugins-good{a} gstreamer0.10-pulseaudio{a} 
  gstreamer0.10-tools{a} gstreamer0.10-x{a} gvfs{a} gzip{a} 
  hunspell-en-ca{a} icedtea-6-jre-cacao{a} info{a} initscripts{a} 
  insserv{a} iptables{a} iputils-ping{a} iputils-tracepath{a} iso-codes{a} 
  kbd{a} kdebase-runtime-data{a} kdelibs-data{a} kdelibs5-data{a} 
  kdepimlibs5{a} language-pack-gnome-en{a} language-selector-common{a} 
  launchpad-integration{a} libaa1{a} libaccess-bridge-java{a} 
  libaccess-bridge-java-jni{a} libacl1{a} libarchive1{a} libatk1.0-0{a} 
  libatk1.0-data{a} libaudio2{a} libavahi-client3{a} 
  libavahi-common-data{a} libavahi-common3{a} libavahi-core6{a} 
  libavahi-gobject0{a} libavformat52{a} libbeagle1{a} libblkid1{a} 
  libbonoboui2-common{a} libboost-program-options1.40.0{a} 
  libbrasero-media0{a} libbrlapi0.5{a} libbsd0{a} libbz2-1.0{a} libc-bin{a} 
  libc6{a} libc6-i686{a} libcaca0{a} libcairo-perl{a} libcamel1.2-14{a} 
  libcanberra-gtk0{a} libcanberra0{a} libcap2{a} libcdparanoia0{a} 
  libclucene0ldbl{a} libcompizconfig0{a} libcouchdb-glib-1.0-2{a} 
  libcroco3{a} libcryptui0{a} libcupscgi1{a} libcupsimage2{a} 
  libcupsppdc1{a} libcurl3{a} libcwidget3{a} libdatrie1{a} libdb4.8{a} 
  libdbusmenu-gtk1{a} libdbusmenu-qt2{a} libdc1394-22{a} 
  libdevkit-power-gobject1{a} libdjvulibre-text{a} libdjvulibre21{a} 
  libdrm-intel1{a} libdrm-nouveau1{a} libdvdnav4{a} libebackend1.2-0{a} 
  libedata-book1.2-2{a} libedata-cal1.2-6{a} libedataserverui1.2-8{a} 
  libedit2{a} libept0{a} libesd0{a} libexiv2-6{a} libfaac0{a} libfaad2{a} 
  libfile-copy-recursive-perl{a} libfontenc1{a} libfs6{a} libgadu3{a} 
  libgail18{a} libgcj-bc{a} libgcj-common{a} libgdata-google1.2-1{a} 
  libgdata1.2-1{a} libglade2.0-cil{a} libglib2.0-0{a} libglib2.0-cil{a} 
  libglibmm-2.4-1c2a{a} libglitz1{a} libgmime-2.4-2{a} libgnome-keyring0{a} 
  libgnome-media0{a} libgnome-vfs2.0-cil{a} libgnome2-0{a} 
  libgnome2.24-cil{a} libgnomecanvas2-common{a} libgnomekbd-common{a} 
  libgnomeui-common{a} libgnomevfs2-0{a} libgnutls26{a} libgomp1{a} 
  libgphoto2-2{a} libgphoto2-port0{a} libgpm2{a} libgsl0ldbl{a} 
  libgstreamer0.10-0{a} libgtk2-perl{a} libgtk2.0-bin{a} 
  libgtkhtml3.14-19{a} libgtksourceview2.0-0{a} 
  libgtksourceview2.0-common{a} libgupnp-1.0-3{a} libgutenprint2{a} 
  libgweather-common{a} libhpmud0{a} libhtml-parser-perl{a} 
  libhtml-tagset-perl{a} libhyphen0{a} libice6{a} libicu42{a} libid3tag0{a} 
  libido-0.1-0{a} libiec61883-0{a} libijs-0.35{a} libilmbase6{a} 
  libindicate4{a} libindicator0{a} libio-string-perl{a} libiptcdata0{a} 
  libjasper1{a} libkate1{a} libkrb5-3{a} liblaunchpad-integration1{a} 
  liblcms1{a} libldap-2.4-2{a} liblircclient0{a} liblocale-gettext-perl{a} 
  liblockfile1{a} liblouis-data{a} liblouis0{a} liblualib50{a} liblzma1{a} 
  libmad0{a} libmeanwhile1{a} libmetacity-private0{a} libmimic0{a} 
  libmjpegtools-1.9{a} libmng1{a} libmodplug0c2{a} libmono-addins0.2-cil{a} 
  libmono-cairo2.0-cil{a} libmono-corlib2.0-cil{a} 
  libmono-i18n-west2.0-cil{a} libmono-security2.0-cil{a} 
  libmono-sharpzip2.84-cil{a} libmono-sqlite2.0-cil{a} 
  libmono-system-web2.0-cil{a} libmono-system2.0-cil{a} libmp3lame0{a} 
  libmpeg2-4{a} libmusicbrainz4c2a{a} libmysqlclient16{a} 
  libnautilus-extension1{a} libncursesw5{a} libnet-dbus-perl{a} 
  libnewt0.52{a} libnih-dbus1{a} libnih1{a} libnm-glib2{a} libnspr4-0d{a} 
  libnss-mdns{a} libnss3-1d{a} libntfs-3g75{a} libntfs10{a} libofa0{a} 
  libopencore-amrnb0{a} libopenexr6{a} libopenobex1{a} liborbit2{a} 
  libpackagekit-glib2-12{a} libpackagekit-qt-12{a} libpam-runtime{a} 
  libpangomm-1.4-1{a} libpaper1{a} libparse-debianchangelog-perl{a} 
  libpciaccess0{a} libpcre3{a} libpcsclite1{a} libphonon4{a} libpisock9{a} 
  libpixman-1-0{a} libplasma3{a} libplist1{a} libpng12-0{a} 
  libpolkit-backend-1-0{a} libpolkit-qt-1-0{a} libpoppler-glib4{a} 
  libpoppler5{a} libpostproc51{a} libpulse-browse0{a} libqt4-assistant{a} 
  libqt4-designer{a} libqt4-help{a} libqt4-qt3support{a} 
  libqt4-scripttools{a} libqt4-test{a} libqt4-xml{a} libqt4-xmlpatterns{a} 
  libraptor1{a} librasqal2{a} librsvg2-common{a} libsasl2-2{a} 
  libsasl2-modules{a} libschroedinger-1.0-0{a} libsdl1.2debian-all{a} 
  libselinux1{a} libsensors4{a} libsidplay1{a} libsigc++-2.0-0c2a{a} 
  libsilcclient-1.1-3{a} libslang2{a} libsm6{a} libsndfile1{a} 
  libspectre1{a} libss2{a} libssh-4{a} libstartup-notification0{a} 
  libstdc++6{a} libstlport4.6ldbl{a} libstreamanalyzer0{a} 
  libsub-name-perl{a} libtag1c2a{a} libtalloc2{a} libtelepathy-farsight0{a} 
  libtext-charwidth-perl{a} libunique-1.0-0{a} libvisual-0.4-0{a} 
  libvisual-0.4-plugins{a} libvorbis0a{a} libvte9{a} libwebkit-1.0-2{a} 
  libwebkit-1.0-common{a} libwnck-common{a} libwnck22{a} libwpd8c2a{a} 
  libwrap0{a} libwww-perl{a} libx11-6{a} libx11-data{a} libx264-85{a} 
  libxau6{a} libxaw7{a} libxcursor1{a} libxdamage1{a} libxfixes3{a} 
  libxft2{a} libxklavier16{a} libxml-twig-perl{a} libxmu6{a} libxt6{a} 
  libxtst6{a} libxvidcore4{a} libxxf86vm1{a} libzephyr4{a} light-themes{a} 
  linux-headers-2.6.32-25{a} linux-headers-2.6.32-27{a} 
  linux-headers-2.6.32-29{a} linux-headers-2.6.32-32{a} lsof{a} ltrace{a} 
  make{a} media-player-info{a} mime-support{a} min12xxw{a} myspell-en-za{a} 
  nautilus{a} net-tools{a} openjdk-6-jre{a} openjdk-6-jre-headless{a} 
  openjdk-6-jre-lib{a} openoffice.org-base-core{a} openoffice.org-common{a} 
  openoffice.org-writer{a} openssh-client{a} oss-compat{a} 
  oxygen-icon-theme{a} p7zip-full{a} passwd{a} perl{a} phonon{a} 
  phonon-backend-null{a} pkg-config{a} plasma-scriptengine-javascript{a} 
  plymouth{a} plymouth-label{a} pnm2ppa{a} policykit-1{a} poppler-utils{a} 
  popularity-contest{a} powermgmt-base{a} pptp-linux{a} pulseaudio{a} 
  pulseaudio-esound-compat{a} python-apt{a} python-aptdaemon-gtk{a} 
  python-central{a} python-configglue{a} python-couchdb{a} python-crypto{a} 
  python-cups{a} python-cupshelpers{a} python-debian{a} 
  python-desktopcouch{a} python-desktopcouch-records{a} python-farsight{a} 
  python-gconf{a} python-glade2{a} python-gnomekeyring{a} python-gobject{a} 
  python-gst0.10{a} python-gtk2{a} python-gtksourceview2{a} 
  python-httplib2{a} python-launchpadlib{a} python-lazr.restfulclient{a} 
  python-libxml2{a} python-notify{a} python-oauth{a} python-openssl{a} 
  python-pam{a} python-problem-report{a} python-pygoocanvas{a} 
  python-pyinotify{a} python-qt4{a} python-simplejson{a} 
  python-telepathy{a} python-twisted-core{a} python-twisted-names{a} 
  python-ubuntuone-storageprotocol{a} python-uno{a} python-wadllib{a} 
  python-webkit{a} python-xapian{a} python-xdg{a} python2.6-minimal{a} 
  rarian-compat{a} readline-common{a} rtkit{a} samba-common-bin{a} 
  screen{a} sgml-data{a} software-properties-gtk{a} strace{a} syslinux{a} 
  system-config-printer-common{a} sysvinit-utils{a} time{a} totem-common{a} 
  tsconf{a} ttf-dejavu-core{a} ttf-dejavu-extra{a} ttf-opensymbol{a} 
  ubuntu-mono{a} ubuntu-system-service{a} udev{a} unattended-upgrades{a} 
  update-manager-kde{a} upower{a} upstart{a} usbmuxd{a} util-linux{a} 
  wbritish{a} wodim{a} x11-apps{a} x11-common{a} x11-xfs-utils{a} 
  x11-xserver-utils{a} xauth{a} xbitmaps{a} xdg-user-dirs{a} xdg-utils{a} 
  xfonts-75dpi{a} xfonts-encodings{a} xfonts-utils{a} xinput{a} xkb-data{a} 
  xml-core{a} xorg-docs-core{a} xserver-xorg-input-mouse{a} 
  xserver-xorg-video-ark{a} xserver-xorg-video-ati{a} 
  xserver-xorg-video-chips{a} xserver-xorg-video-cirrus{a} 
  xserver-xorg-video-geode{a} xserver-xorg-video-i128{a} 
  xserver-xorg-video-i740{a} xserver-xorg-video-intel{a} 
  xserver-xorg-video-mach64{a} xserver-xorg-video-mga{a} 
  xserver-xorg-video-neomagic{a} xserver-xorg-video-nouveau{a} 
  xserver-xorg-video-nv{a} xserver-xorg-video-r128{a} 
  xserver-xorg-video-s3{a} xserver-xorg-video-siliconmotion{a} 
  xserver-xorg-video-trident{a} xserver-xorg-video-tseng{a} xsltproc{a} 
  yelp{a} zenity{a} 
The following packages will be REMOVED:
  audacity-data{u} clamav{u} clamav-freshclam{u} grub-common{u} 
  krosspython{u} ktorrent-data{u} libclamav6{u} libflac++6{u} 
  libsolidcontrol4{u} libtommath0{u} libwxbase2.8-0{u} libwxgtk2.8-0{u} 
  libxcb-shm0{u} libxine1-console{u} libxine1-misc-plugins{u} os-prober{u} 
  pidgin-data{u} 
The following partially installed packages will be configured:
  flashplugin-installer sysv-rc 
0 packages upgraded, 486 newly installed, 17 to remove and 0 not upgraded.
Need to get 0B/320MB of archives. After unpacking 1,161MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
E: Could not perform immediate configuration on 'libc6'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file '/var/lib/dpkg/status' near line 18945 package 'mawk':
 EOF during value of field `Description' (missing final newline)
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done


---

### Post by wildmanne39 on 2011-06-13
> **stevovets said:**
> no change, still receiving the same error.  Here's the terminal read-out
Hi, it looks like it installed all but that one package is that correct.

---

### Post by wildmanne39 on 2011-06-13
Hi, according to all of that it looks like you are trying to upgrade to a new version of ubunbtu is that right? or has it been a long time since you updated any packages? What version of ubuntu are you using?

---

### Post by wildmanne39 on 2011-06-13
Hi, it looks like I missed part of the command I wanted you to run earlier, let fix that now and see if it works.
sudo rm /var/lib/dpkg/status
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo rm -rf /var/lib/apt/lists/*
sudo dpkg --configure -a
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install -f

---

### Post by stevovets on 2011-06-13
>             Depends: libesd0 (>= 0.2.35) which is a virtual package.
            Depends: libice6 (>= 1:1.0.0) which is a virtual package.
            Depends: libpng12-0 (>= 1.2.13-4) which is a virtual package.
            Depends: libsm6 which is a virtual package.
            Depends: libvorbis0a (>= 1.1.2) which is a virtual package.
            Depends: libx11-6 which is a virtual package.
            Depends: libxaw7 which is a virtual package.
            Depends: libxmu6 which is a virtual package.
            Depends: libxt6 which is a virtual package.
  indicator-session: Depends: libatk1.0-0 (>= 1.29.3) which is a virtual package.
                     Depends: libc6 (>= 2.3.6-6~) which is a virtual package.
                     Depends: libdbusmenu-gtk1 (>= 0.2.5) which is a virtual package.
                     Depends: libglib2.0-0 (>= 2.18.0) which is a virtual package.
                     Depends: libindicator0 (>= 0.3.6) which is a virtual package.
                     Depends: gconf2 (>= 2.10.1-2) which is a virtual package.
                     Depends: upower which is a virtual package.
  gconf-editor: Depends: libc6 (>= 2.3.6-6~) which is a virtual package.
                Depends: libglib2.0-0 (>= 2.16.0) which is a virtual package.
                Depends: liblaunchpad-integration1 (>= 0.1.17) which is a virtual package.
                Depends: gconf2 (>= 2.10.1-2) which is a virtual package.
                Depends: gconf-defaults-service (>= 2.28) which is a virtual package.
  radeontool: Depends: libc6 (>= 2.4) which is a virtual package.
              Depends: libpciaccess0 (>= 0) which is a virtual package.
  openssl: Depends: libc6 (>= 2.7) which is a virtual package.
  packagekit-backend-apt: Depends: libc6 (>= 2.3.6-6~) which is a virtual package.
                          Depends: libglib2.0-0 (>= 2.12.0) which is a virtual package.
                          Depends: python-central (>= 0.6.11) which is a virtual package.
                          Depends: python-apt (>= 0.7.13.2) which is a virtual package.
  erlang-ssl: Depends: erlang-crypto (= 1:13.b.3-dfsg-2ubuntu2.1) which is a virtual package.
              Depends: libc6 (>= 2.4) which is a virtual package.
  cpp-4.4: Depends: gcc-4.4-base (= 4.4.3-4ubuntu5) which is a virtual package.
           Depends: libc6 (>= 2.11) which is a virtual package.
  python-wnck: Depends: libatk1.0-0 (>= 1.29.3) which is a virtual package.
               Depends: libc6 (>= 2.3.6-6~) which is a virtual package.
               Depends: libglib2.0-0 (>= 2.16.0) which is a virtual package.
               Depends: libwnck22 (>= 2.22.0) which is a virtual package.
               Depends: python-gtk2 which is a virtual package.
  mount: PreDepends: libblkid1 (>= 2.17) which is a virtual package.
         PreDepends: libc6 (>= 2.7) which is a virtual package.
         PreDepends: libselinux1 (>= 2.0.15) which is a virtual package.
  libpulse0: Depends: libc6 (>= 2.4) which is a virtual package.
             Depends: libice6 (>= 1:1.0.0) which is a virtual package.
             Depends: libsm6 which is a virtual package.
             Depends: libsndfile1 (>= 1.0.20) which is a virtual package.
             Depends: libwrap0 (>= 7.6-4~) which is a virtual package.
             Depends: libx11-6 (>= 0) which is a virtual package.
             Depends: libxtst6 which is a virtual package.
  libhtml-tree-perl: Depends: perl (>= 5.6.0-16) which is a virtual package.
                     Depends: libhtml-parser-perl which is a virtual package.
                     Depends: libhtml-tagset-perl (>= 3.02) which is a virtual package.
  brasero: Depends: libatk1.0-0 (>= 1.29.3) which is a virtual package.
           Depends: libbeagle1 (>= 0.3.9) which is a virtual package.
           Depends: libbrasero-media0 (>= 2.27.92) which is a virtual package.
           Depends: libc6 (>= 2.7) which is a virtual package.
           Depends: libglib2.0-0 (>= 2.23.5) which is a virtual package.
           Depends: libgstreamer0.10-0 (>= 0.10.15) which is a virtual package.
           Depends: libice6 (>= 1:1.0.0) which is a virtual package.
           Depends: liblaunchpad-integration1 (>= 0.1.17) which is a virtual package.
           Depends: libnautilus-extension1 (>= 1:2.29.1) which is a virtual package.
           Depends: libsm6 which is a virtual package.
           Depends: libunique-1.0-0 (>= 1.0.0) which is a virtual package.
           Depends: gstreamer0.10-plugins-base (>= 0.10.0) which is a virtual package.
           Depends: gvfs which is a virtual package.
           Depends: wodim which is a virtual package.
  liboil0.3: Depends: libc6 (>= 2.11) which is a virtual package.
  libgc1c2: Depends: libc6 (>= 2.11) which is a virtual package.
            Depends: libstdc++6 (>= 4.1.1) which is a virtual package.
  libavahi-glib1: Depends: libavahi-common3 (>= 0.6.16) which is a virtual package.
                  Depends: libc6 (>= 2.3.6-6~) which is a virtual package.
                  Depends: libglib2.0-0 (>= 2.16.0) which is a virtual package.
  telepathy-butterfly: Depends: python-central (>= 0.6.11) which is a virtual package.
                       Depends: python-gobject which is a virtual package.
                       Depends: python-telepathy (>= 0.15.17) which is a virtual package.
  libgnome-keyring1.0-cil: Depends: libc6 (>= 2.1.3) which is a virtual package.
                           Depends: libglib2.0-0 (>= 2.12.0) which is a virtual package.
                           Depends: libgnome-keyring0 (>= 2.20.3) which is a virtual package.
                           Depends: libglib2.0-cil (>= 2.12.9) which is a virtual package.
                           Depends: libmono-corlib2.0-cil (>= 1.2.2.1) which is a virtual package.
  firefox-branding: Depends: firefox (= 3.6.17+build3+nobinonly-0ubuntu0.10.04.1) which is a virtual package.
  libqt3-mt: Depends: libaudio2 which is a virtual package.
             Depends: libc6 (>= 2.4) which is a virtual package.
             Depends: libice6 (>= 1:1.0.0) which is a virtual package.
             Depends: libmng1 (>= 1.0.3-1) which is a virtual package.
             Depends: libpng12-0 (>= 1.2.13-4) which is a virtual package.
             Depends: libsm6 which is a virtual package.
             Depends: libstdc++6 (>= 4.1.1) which is a virtual package.
             Depends: libx11-6 which is a virtual package.
             Depends: libxcursor1 (> 1.1.2) which is a virtual package.
             Depends: libxft2 (> 2.1.1) which is a virtual package.
             Depends: libxt6 which is a virtual package.
  libgtkspell0: Depends: libatk1.0-0 (>= 1.29.3) which is a virtual package.
                Depends: libc6 (>= 2.3.6-6~) which is a virtual package.
                Depends: libglib2.0-0 (>= 2.16.0) which is a virtual package.
  compiz: Depends: compiz-gnome which is a virtual package. or
                   compiz-kde which is a virtual package.
          Depends: compiz-fusion-plugins-main (>= 0.8.3) which is a virtual package.
          Depends: libcompizconfig0 (>= 0.8.3) which is a virtual package.
  libxml2-utils: Depends: libc6 (>= 2.7) which is a virtual package.
  python-ubuntuone-client: Depends: python-central (>= 0.6.11) which is a virtual package.
                           Depends: python-ubuntuone-storageprotocol (>= 1.2.0) which is a virtual package.
                           Depends: python-xdg which is a virtual package.
                           Depends: xdg-utils which is a virtual package.
                           Depends: python-gnomekeyring which is a virtual package. or
                                    python-gnome2-desktop which is a virtual package.
                           Depends: python-notify which is a virtual package.
                           Depends: python-pyinotify which is a virtual package.
                           Depends: python-twisted-names which is a virtual package.
                           Depends: python-oauth (>= 1.0~svn1092-0ubuntu2) which is a virtual package.
  gnome-panel: Depends: libatk1.0-0 (>= 1.29.3) which is a virtual package.
               Depends: libc6 (>= 2.7) which is a virtual package.
               Depends: libcanberra-gtk0 (>= 0.17) which is a virtual package.
               Depends: libcanberra0 (>= 0.2) which is a virtual package.
               Depends: libedataserverui1.2-8 (>= 2.28.3.1) which is a virtual package.
               Depends: libglib2.0-0 (>= 2.23.5) which is a virtual package.
               Depends: libice6 (>= 1:1.0.0) which is a virtual package.
               Depends: liborbit2 (>= 1:2.14.10) which is a virtual package.
               Depends: libsm6 which is a virtual package.
               Depends: libwnck22 (>= 2.22.0) which is a virtual package.
               Depends: libx11-6 (>= 0) which is a virtual package.
               Depends: gnome-panel-data (>= 1:2.30) which is a virtual package.
               Depends: gnome-panel-data (< 1:2.31) which is a virtual package.
               Depends: gnome-desktop-data (>= 2.10.0-1) which is a virtual package.
               Depends: gnome-about (>= 2.10.0-1) which is a virtual package.
  libgssapi-krb5-2: Depends: libc6 (>= 2.7) which is a virtual package.
                    Depends: libkrb5-3 (= 1.8.1+dfsg-2ubuntu0.9) which is a virtual package.
  x11-xkb-utils: Depends: libc6 (>= 2.7) which is a virtual package.
                 Depends: libx11-6 which is a virtual package.
                 Depends: libxaw7 which is a virtual package.
                 Depends: libxmu6 which is a virtual package.
                 Depends: libxt6 which is a virtual package.
                 Depends: cpp which is a virtual package.
                 PreDepends: x11-common (>= 1:7.0.0) which is a virtual package.
  libcelt0-0: Depends: libc6 (>= 2.4) which is a virtual package.
  gvfs-backends: Depends: libarchive1 (>= 2.2.3) which is a virtual package.
                 Depends: libavahi-client3 (>= 0.6.16) which is a virtual package.
                 Depends: libavahi-common3 (>= 0.6.16) which is a virtual package.
                 Depends: libc6 (>= 2.7) which is a virtual package.
                 Depends: libglib2.0-0 (>= 2.23.5) which is a virtual package.
                 Depends: libgnome-keyring0 (>= 2.20.3) which is a virtual package.
                 Depends: libgphoto2-2 (>= 2.4.3) which is a virtual package.
                 Depends: libgphoto2-port0 (>= 2.4.3) which is a virtual package.
                 Depends: gvfs (= 1.6.1-0ubuntu1build1) which is a virtual package.
  xfonts-mathml: Depends: xfonts-utils which is a virtual package.
  language-pack-en: PreDepends: dpkg (>= 1.10.27ubuntu1) which is a virtual package.
  libgnome-desktop-2-17: Depends: libc6 (>= 2.4) which is a virtual package.
                         Depends: libglib2.0-0 (>= 2.23.5) which is a virtual package.
                         Depends: libstartup-notification0 (>= 0.10) which is a virtual package.
                         Depends: libx11-6 (>= 0) which is a virtual package.
  ttf-unfonts-core: Depends: defoma which is a virtual package.
  liblua50: Depends: libc6 (>= 2.4) which is a virtual package.
  linux-image-2.6.32-29-generic: PreDepends: dpkg (>= 1.10.24) which is a virtual package.
  python-apport: Depends: python-central (>= 0.6.11) which is a virtual package.
                 Depends: python-apt which is a virtual package.
                 Depends: python-problem-report (>= 0.94) which is a virtual package.
                 Depends: python-launchpadlib (>= 1.5.7) which is a virtual package.
  python-papyon: Depends: python-gobject (>= 2.10) which is a virtual package.
                 Depends: python-openssl (>= 0.6) which is a virtual package.
                 Depends: python-gst0.10 which is a virtual package.
                 Depends: python-farsight which is a virtual package.
                 Depends: python-crypto which is a virtual package.
  libexif12: Depends: libc6 (>= 2.4) which is a virtual package.
  sysv-rc: Depends: sysvinit-utils (>= 2.86.ds1-62) which is a virtual package.
           Depends: insserv (> 1.12.0-10) which is a virtual package.
  python-xkit: Depends: python-central (>= 0.6.11) which is a virtual package.
  libisc60: Depends: libc6 (>= 2.4) which is a virtual package.
            Depends: libcap2 (>= 2.10) which is a virtual package.
  libqt4-script: Depends: libc6 (>= 2.4) which is a virtual package.
                 Depends: libstdc++6 (>= 4.1.1) which is a virtual package.
  libxi6: Depends: libc6 (>= 2.4) which is a virtual package.
          Depends: libx11-6 (>= 2:1.2.99.901) which is a virtual package.
  intel-gpu-tools: Depends: libc6 (>= 2.8) which is a virtual package.
                   Depends: libdrm-intel1 (>= 2.4.9) which is a virtual package.
                   Depends: libpciaccess0 (>= 0.8.0+git20071002) which is a virtual package.
  libquicktime1: Depends: libc6 (>= 2.11) which is a virtual package.
                 Depends: libfaad2 which is a virtual package.
                 Depends: libpng12-0 (>= 1.2.13-4) which is a virtual package.
                 Depends: libschroedinger-1.0-0 (>= 1.0.0) which is a virtual package.
                 Depends: libvorbis0a (>= 1.1.2) which is a virtual package.
  libnice0: Depends: libc6 (>= 2.4) which is a virtual package.
            Depends: libglib2.0-0 (>= 2.16.0) which is a virtual package.
            Depends: libgupnp-1.0-3 (>= 0.13.2) which is a virtual package.
  compiz-core: Depends: libc6 (>= 2.7) which is a virtual package.
               Depends: libice6 (>= 1:1.0.0) which is a virtual package.
               Depends: libsm6 which is a virtual package.
               Depends: libstartup-notification0 (>= 0.10) which is a virtual package.
               Depends: libx11-6 (>= 0) which is a virtual package.
               Depends: libxcursor1 (> 1.1.2) which is a virtual package.
               Depends: libxdamage1 (>= 1:1.1) which is a virtual package.
               Depends: libxfixes3 (>= 1:4.0.1) which is a virtual package.
  totem: Depends: libatk1.0-0 (>= 1.29.3) which is a virtual package.
         Depends: libc6 (>= 2.7) which is a virtual package.
         Depends: libglib2.0-0 (>= 2.23.5) which is a virtual package.
         Depends: libgstreamer0.10-0 (>= 0.10.26) which is a virtual package.
         Depends: libice6 (>= 1:1.0.0) which is a virtual package.
         Depends: liblaunchpad-integration1 (>= 0.1.17) which is a virtual package.
         Depends: libnautilus-extension1 (>= 1:2.29.1) which is a virtual package.
         Depends: libsm6 which is a virtual package.
         Depends: libunique-1.0-0 (>= 1.0.0) which is a virtual package.
         Depends: libx11-6 (>= 0) which is a virtual package.
         Depends: libxtst6 which is a virtual package.
         Depends: libxxf86vm1 which is a virtual package.
         Depends: gstreamer0.10-plugins-base (>= 0.10.26) which is a virtual package.
         Depends: gstreamer0.10-plugins-good (>= 0.10.7) which is a virtual package.
         Depends: gstreamer0.10-x which is a virtual package.
         Depends: totem-common (>= 2.30) which is a virtual package.
         Depends: totem-common (< 2.31) which is a virtual package.
  gnome-accessibility-themes: Depends: librsvg2-common which is a virtual package.
  binfmt-support: Depends: perl which is a virtual package.
  libdirac-encoder0: Depends: libc6 (>= 2.4) which is a virtual package.
                     Depends: libstdc++6 (>= 4.4.0) which is a virtual package.
  mountall: Depends: udev which is a virtual package.
            Depends: plymouth which is a virtual package.
            Depends: libc6 (>= 2.9) which is a virtual package.
            Depends: libnih-dbus1 (>= 1.0.0) which is a virtual package.
            Depends: libnih1 (>= 1.0.0) which is a virtual package.
  xserver-xorg-input-synaptics: Depends: udev which is a virtual package.
                                Depends: libc6 (>= 2.4) which is a virtual package.
                                Depends: libpciaccess0 which is a virtual package.
                                Depends: libpixman-1-0 which is a virtual package.
                                Depends: libx11-6 (>= 0) which is a virtual package.
  libattr1: Depends: libc6 (>= 2.4) which is a virtual package.
  python-ibus: Depends: python-gtk2 which is a virtual package.
               Depends: iso-codes which is a virtual package.
  openoffice.org-help-en-us: Depends: openoffice.org-writer which is a virtual package. or
                                      language-support-translations-en which is a virtual package.
  soprano-daemon: Depends: libc6 (>= 2.4) which is a virtual package.
                  Depends: libraptor1 (>= 1.4.19) which is a virtual package.
                  Depends: libstdc++6 (>= 4.1.1) which is a virtual package.
  desktop-file-utils: Depends: libc6 (>= 2.7) which is a virtual package.
                      Depends: libglib2.0-0 (>= 2.23.5) which is a virtual package.
  libxinerama1: Depends: libc6 (>= 2.1.3) which is a virtual package.
                Depends: libx11-6 which is a virtual package.
  libxv1: Depends: libc6 (>= 2.4) which is a virtual package.
          Depends: libx11-6 which is a virtual package.
  apport-gtk: Depends: python-gtk2 (>= 2.12) which is a virtual package.
              Depends: python-xdg which is a virtual package.
              Depends: apport (>= 0.41) which is a virtual package.
  libxext6: Depends: libc6 (>= 2.4) which is a virtual package.
            Depends: libx11-6 which is a virtual package.
  libavahi-ui0: Depends: libatk1.0-0 (>= 1.29.3) which is a virtual package.
                Depends: libavahi-client3 (>= 0.6.16) which is a virtual package.
                Depends: libavahi-common3 (>= 0.6.22) which is a virtual package.
                Depends: libc6 (>= 2.4) which is a virtual package.
                Depends: libglib2.0-0 (>= 2.23.5) which is a virtual package.
  libgstreamer-plugins-base0.10-0: Depends: libc6 (>= 2.7) which is a virtual package.
                                   Depends: libglib2.0-0 (>= 2.23.5) which is a virtual package.
                                   Depends: libgstreamer0.10-0 (>= 0.10.28) which is a virtual package.
                                   Depends: iso-codes which is a virtual package.
  xserver-xorg-video-sisusb: Depends: libc6 (>= 2.7) which is a virtual package.
  gnome-session: Depends: nautilus which is a virtual package.
                 Depends: gnome-session-bin (>= 2.30) which is a virtual package.
                 Depends: gnome-session-bin (< 2.31) which is a virtual package.
  mscompress: Depends: libc6 (>= 2.4) which is a virtual package.
  libreadline6: Depends: readline-common which is a virtual package.
                Depends: libc6 (>= 2.11~20100104-0ubuntu5) which is a virtual package.
  libiodbc2: Depends: libc6 (>= 2.4) which is a virtual package.
  gdm-guest-session: Depends: passwd which is a virtual package.
  libmpcdec3: Depends: libc6 (>= 2.4) which is a virtual package.
  linux-image-2.6.32-21-generic: PreDepends: dpkg (>= 1.10.24) which is a virtual package.
  libxrandr2: Depends: libc6 (>= 2.1.3) which is a virtual package.
              Depends: libx11-6 (>= 0) which is a virtual package.
  python-twisted-bin: Depends: libc6 (>= 2.3.6-6~) which is a virtual package.
  ntfs-3g: Depends: libc6 (>= 2.4) which is a virtual package.
           Depends: libntfs-3g75 which is a virtual package.
           PreDepends: fuse-utils which is a virtual package.
  lsb-release: Depends: python-central (>= 0.6.11) which is a virtual package.
  xscreensaver-data: Depends: libc6 (>= 2.7) which is a virtual package.
                     Depends: libglib2.0-0 (>= 2.12.0) which is a virtual package.
                     Depends: libice6 (>= 1:1.0.0) which is a virtual package.
                     Depends: libsm6 which is a virtual package.
                     Depends: libx11-6 (>= 0) which is a virtual package.
                     Depends: libxmu6 which is a virtual package.
                     Depends: libxt6 which is a virtual package.
  libgoocanvas3: Depends: libatk1.0-0 (>= 1.29.3) which is a virtual package.
                 Depends: libc6 (>= 2.4) which is a virtual package.
                 Depends: libglib2.0-0 (>= 2.18.0) which is a virtual package.
  libaspell15: Depends: libc6 (>= 2.4) which is a virtual package.
               Depends: libstdc++6 (>= 4.1.1) which is a virtual package.
  dmidecode: Depends: libc6 (>= 2.4) which is a virtual package.
  modemmanager: Depends: libc6 (>= 2.7) which is a virtual package.
                Depends: libglib2.0-0 (>= 2.18.0) which is a virtual package.
  libgupnp-igd-1.0-2: Depends: libc6 (>= 2.3.6-6~) which is a virtual package.
                      Depends: libglib2.0-0 (>= 2.16.0) which is a virtual package.
                      Depends: libgupnp-1.0-3 (>= 0.13.2) which is a virtual package.
  totem-mozilla: Depends: libc6 (>= 2.4) which is a virtual package.
                 Depends: libglib2.0-0 (>= 2.22) which is a virtual package.
                 Depends: libstdc++6 (>= 4.1.1) which is a virtual package.
                 Depends: libx11-6 which is a virtual package.
                 Depends: dbus-x11 (>= 0.61) which is a virtual package.
  xserver-xorg-video-radeon: Depends: libc6 (>= 2.7) which is a virtual package.
                             Depends: libpciaccess0 (>= 0.10.2) which is a virtual package.
                             Depends: libpixman-1-0 which is a virtual package.
  libopencore-amrwb0: Depends: libc6 (>= 2.1.3) which is a virtual package.
                      Depends: libstdc++6 (>= 4.1.1) which is a virtual package.
  linux-headers-2.6.32-25-generic: Depends: linux-headers-2.6.32-25 which is a virtual package.
                                   Depends: libc6 (>= 2.8) which is a virtual package.
  libitext-java-gcj: Depends: libgcj-common (> 1:4.1.1-13) which is a virtual package.
                     Depends: libc6 (>= 2.3.6-6~) which is a virtual package.
                     Depends: libgcj-bc (>= 4.3.3-1) which is a virtual package.
  python-cairo: Depends: libc6 (>= 2.4) which is a virtual package.
  libgtk2.0-0: Depends: libatk1.0-0 (>= 1.29.3) which is a virtual package.
               Depends: libc6 (>= 2.11) which is a virtual package.
               Depends: libglib2.0-0 (>= 2.23.6) which is a virtual package.
               Depends: libgnutls26 (>= 2.7.14-0) which is a virtual package.
               Depends: libjasper1 (>= 1.900.1) which is a virtual package.
               Depends: libpng12-0 (>= 1.2.13-4) which is a virtual package.
               Depends: libx11-6 (>= 0) which is a virtual package.
               Depends: libxcursor1 (> 1.1.2) which is a virtual package.
               Depends: libxdamage1 (>= 1:1.1) which is a virtual package.
               Depends: libxfixes3 (>= 1:4.0.1) which is a virtual package.
  netcat-openbsd: Depends: libc6 (>= 2.7) which is a virtual package.
                  Depends: libglib2.0-0 (>= 2.12.0) which is a virtual package.
  libgnome2-canvas-perl: Depends: perl (>= 5.10.1-8ubuntu1) which is a virtual package.
                         Depends: libatk1.0-0 (>= 1.29.3) which is a virtual package.
                         Depends: libc6 (>= 2.1.3) which is a virtual package.
                         Depends: libglib2.0-0 (>= 2.16.0) which is a virtual package.
                         Depends: libgtk2-perl (>= 1.040) which is a virtual package.
  libgsf-1-114: Depends: libbz2-1.0 which is a virtual package.
                Depends: libc6 (>= 2.7) which is a virtual package.
                Depends: libglib2.0-0 (>= 2.18.0) which is a virtual package.
  libpolkit-agent-1-0: Depends: libc6 (>= 2.3.6-6~) which is a virtual package.
                       Depends: libglib2.0-0 (>= 2.21.4) which is a virtual package.
  ncurses-bin: PreDepends: libc6 (>= 2.4) which is a virtual package.
  gsfonts: Depends: defoma (>= 0.11.10) which is a virtual package.
  file-roller: Depends: libc6 (>= 2.4) which is a virtual package.
               Depends: libglib2.0-0 (>= 2.23.5) which is a virtual package.
               Depends: liblaunchpad-integration1 (>= 0.1.17) which is a virtual package.
               Depends: libnautilus-extension1 (>= 1:2.29.1) which is a virtual package.
               Depends: gconf2 (>= 2.10.1-2) which is a virtual package.
               Depends: gzip (>= 1.3.2) which is a virtual package.
               Depends: unzip which is a virtual package. or
                        p7zip-full which is a virtual package.
               Depends: zip which is a virtual package. or
                        p7zip-full which is a virtual package.
  libxkbfile1: Depends: libc6 (>= 2.7) which is a virtual package.
               Depends: libx11-6 which is a virtual package.
  libgdiplus: Depends: libc6 (>= 2.11) which is a virtual package.
              Depends: libglib2.0-0 (>= 2.16.0) which is a virtual package.
              Depends: libpng12-0 (>= 1.2.13-4) which is a virtual package.
              Depends: libx11-6 (>= 0) which is a virtual package.
  libspeexdsp1: Depends: libc6 (>= 2.4) which is a virtual package.
  libmms0: Depends: libc6 (>= 2.4) which is a virtual package.
           Depends: libglib2.0-0 (>= 2.12.0) which is a virtual package.
  libneon27-gnutls: Depends: libc6 (>= 2.4) which is a virtual package.
                    Depends: libgnutls26 (>= 2.7.14-0) which is a virtual package.
                    Depends: libkrb5-3 (>= 1.6.dfsg.2) which is a virtual package.
  transmission-gtk: Depends: libc6 (>= 2.11) which is a virtual package.
                    Depends: libcanberra-gtk0 (>= 0.2) which is a virtual package.
                    Depends: libcanberra0 (>= 0.2) which is a virtual package.
                    Depends: libglib2.0-0 (>= 2.23.5) which is a virtual package.
                    Depends: liblaunchpad-integration1 (>= 0.1.17) which is a virtual package.
  libltdl7: Depends: libc6 (>= 2.4) which is a virtual package.
  libmagic1: Depends: libc6 (>= 2.8) which is a virtual package.
  python-kde4: Depends: kdepimlibs5 (>= 4:4.4.5) which is a virtual package.
               Depends: libc6 (>= 2.1.3) which is a virtual package.
               Depends: libphonon4 (>= 4:4.6.2-0ubuntu5.1) which is a virtual package.
               Depends: libplasma3 which is a virtual package.
               Depends: libqt4-xml (>= 4:4.5.3) which is a virtual package.
               Depends: libstdc++6 (>= 4.1.1) which is a virtual package.
               Depends: phonon (>= 4:4.5.2) which is a virtual package.
               Depends: python-qt4 (>= 4.7.2-0ubuntu1) which is a virtual package.
  empathy-common: Depends: gconf2 (>= 2.12.1-1) which is a virtual package.
  ssh-askpass-gnome: Depends: libc6 (>= 2.3.6-6~) which is a virtual package.
                     Depends: libglib2.0-0 (>= 2.12.0) which is a virtual package.
                     Depends: libx11-6 (>= 0) which is a virtual package.
                     Depends: openssh-client which is a virtual package. or
                              ssh (>= 1:1.2pre7-4) which is a virtual package. or
                              ssh-krb5 which is a virtual package.
  libpisync1: Depends: libc6 (>= 2.3.6-6~) which is a virtual package.
              Depends: libpisock9 which is a virtual package.
  erlang-base: Depends: libc6 (>= 2.7) which is a virtual package.
  lftp: Depends: libc6 (>= 2.4) which is a virtual package.
        Depends: libgnutls26 (>= 2.7.14-0) which is a virtual package.
  erlang-public-key: Depends: erlang-crypto (= 1:13.b.3-dfsg-2ubuntu2.1) which is a virtual package.
  libgnomevfs2-common: Depends: gconf2 (>= 2.12.1-1) which is a virtual package.
  mawk: PreDepends: libc6 (>= 2.11~20100104-0ubuntu3) which is a virtual package.
  libogg0: Depends: libc6 (>= 2.1.3) which is a virtual package.
  consolekit: Depends: libc6 (>= 2.4) which is a virtual package.
              Depends: libglib2.0-0 (>= 2.23.5) which is a virtual package.
              Depends: libx11-6 (>= 0) which is a virtual package.
  liba52-0.7.4: Depends: libc6 (>= 2.1.3) which is a virtual package.
  python-indicate: Depends: libatk1.0-0 (>= 1.29.3) which is a virtual package.
                   Depends: libc6 (>= 2.4) which is a virtual package.
                   Depends: libglib2.0-0 (>= 2.16.0) which is a virtual package.
                   Depends: libindicate4 (>= 0.2.2) which is a virtual package.
                   Depends: python-gobject (>= 2.15.2) which is a virtual package.
                   Depends: python-central (>= 0.6.11) which is a virtual package.
Resolve these dependencies by hand? [N/+/-/_/:/?]


That's what I got.  I'm not try to upgrade to a new version, I just haven't been able to update in a while (apparently because of this).  I'm running 10.04

---

### Post by wildmanne39 on 2011-06-13
Hi, go into synaptic click on settings repositories, updates, at the bottom of that window make sure release upgrade is marked long term release only.

---

### Post by stevovets on 2011-06-13
it was already set as that

---

### Post by wildmanne39 on 2011-06-13
> **stevovets said:**
> it was already set as that
Hi, tomorrow CoffeeCat is going to take a look and hopefully get you fixed up, I am out of ideas, usually it is not so hard to fix the problem, the commands you have already run usually fixes it.

---

### Post by stevovets on 2011-06-13
yeah I'm pretty flustered on the whole thing.  Thanks so much for trying though, I appreciate it!

---

### Post by wildmanne39 on 2011-06-13
> **stevovets said:**
> yeah I'm pretty flustered on the whole thing.  Thanks so much for trying though, I appreciate it!
Hi, your welcome, I will check tomorrow and see how coffeecat fixes it. We are just missing some little something.

---

### Post by coffeecat on 2011-06-14
> **wildmanne39 said:**
> Hi, your welcome, I will check tomorrow and see how coffeecat fixes it. 

I think you may have misplaced faith in me! :) But there is progress. You seem to have fixed all the earlier dpkg errors which is a considerable achievement. I salute you!

@stevovets, what you seem to be left with is dependency hell but without dpkg errors - unless I've missed any. If I have, please someone, point them out.

Before we go any further, I've looked through your earlier outputs and I can't see any evidence of 3rd party repositories, but to be sure, post the output of:

```
cat /etc/apt/sources.list
```...and...

```
ls /etc/apt/sources.list.d/
```... just so that we can double-check your sources.

Next thing: I presume that last output you posted was the result of wildmanne39's last suggested command, "sudo aptitude install -f". Was it? Or was it the output of "sudo aptitude upgrade"? If it was the output of aptitude upgrade, did you try aptitude install -f? If not, try it. 

Also, your posted output seems incomplete. Did it really start with "Depends: libesd0 (>= 0.2.35) which is a virtual package."? If it is the output of aptitude install -f, I suggest you try the equivalent apt-get command, although I don't hold out much hope it will work where aptitude doesn't.

Try this:

```
sudo apt-get update
sudo apt-get -f install
```Post the output.

There are a few other apt-get options to try, but let's see what we get with the above.

---

### Post by wildmanne39 on 2011-06-14
Hi coffeecat, thank you for helping out with this issue, hopefully it can get resolved to day. I have never seen one like this. I really appreciate the help.

---

### Post by stevovets on 2011-06-14
Hi coffecat,

Here's the output for those first two commands


doops@doops:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-security multiverse
doops@doops:~$ ls /etc/apt/sources.list.d/
google-talkplugin.list  google-talkplugin.list.save

---

### Post by stevovets on 2011-06-14
and here's the output for the last two commands:

> doops@doops:~$ sudo apt-get update
[sudo] password for doops: 
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [198B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US          
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources
Ign [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main Translation-en_US
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [1,347B]
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [766B]
Fetched 2,311B in 3s (587B/s)
Reading package lists... Done
doops@doops:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libsolidcontrolifaces4 clamav libwxgtk2.8-0 clamav-freshclam audacity-data
  libflac++6 clamav-base libclamav6 pidgin-data krosspython libwxbase2.8-0
  os-prober libsolidcontrol4 ktorrent-data libtommath0 grub-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apport apt-utils aptdaemon aptitude arora aspell avahi-daemon bash
  bash-completion binutils bogofilter-bdb brltty bsdmainutils
  busybox-initramfs busybox-static ca-certificates ca-certificates-java
  cabextract cheese-common clamav-base compiz-fusion-plugins-main compiz-gnome
  compizconfig-backend-gconf console-terminus couchdb-bin cpio cpp cron cups
  dbus-x11 debconf-i18n defoma dhcp3-common docbook-xml dosfstools dpkg
  e2fsprogs eject erlang-crypto erlang-runtime-tools espeak-data findutils
  firefox fontconfig-config foomatic-db foomatic-db-engine foomatic-filters
  freepats ftp fuse-utils gcc-4.4-base gconf-defaults-service gconf2
  ghostscript ghostscript-cups gksu gnome-about gnome-desktop-data
  gnome-panel-data gnome-session-bin gnome-terminal-data gnupg gnupg-curl
  groff-base gstreamer0.10-gnonlin gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools
  gstreamer0.10-x gvfs gzip hunspell-en-ca icedtea-6-jre-cacao info
  initscripts insserv iptables iputils-ping iputils-tracepath iso-codes kbd
  kdebase-runtime-data kdelibs-data kdelibs5-data kdepimlibs5
  language-pack-gnome-en language-selector-common launchpad-integration libaa1
  libaccess-bridge-java libaccess-bridge-java-jni libacl1 libarchive1
  libatk1.0-0 libatk1.0-data libaudio2 libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-core6 libavahi-gobject0 libavformat52 libbeagle1
  libblkid1 libbonoboui2-common libboost-program-options1.40.0
  libbrasero-media0 libbrlapi0.5 libbsd0 libbz2-1.0 libc-bin libc6 libc6-i686
  libcaca0 libcairo-perl libcamel1.2-14 libcanberra-gtk0 libcanberra0 libcap2
  libcdparanoia0 libclucene0ldbl libcompizconfig0 libcouchdb-glib-1.0-2
  libcroco3 libcryptui0 libcupscgi1 libcupsimage2 libcupsppdc1 libcurl3
  libcwidget3 libdatrie1 libdb4.8 libdbusmenu-gtk1 libdbusmenu-qt2
  libdc1394-22 libdevkit-power-gobject1 libdjvulibre-text libdjvulibre21
  libdrm-intel1 libdrm-nouveau1 libdvdnav4 libebackend1.2-0 libedata-book1.2-2
  libedata-cal1.2-6 libedataserverui1.2-8 libedit2 libept0 libesd0 libexiv2-6
  libfaac0 libfaad2 libfile-copy-recursive-perl libfontenc1 libfs6 libgadu3
  libgail18 libgcj-bc libgcj-common libgdata-google1.2-1 libgdata1.2-1
  libglade2.0-cil libglib2.0-0 libglib2.0-cil libglibmm-2.4-1c2a libglitz1
  libgmime-2.4-2 libgnome-keyring0 libgnome-media0 libgnome-vfs2.0-cil
  libgnome2-0 libgnome2.24-cil libgnomecanvas2-common libgnomekbd-common
  libgnomeui-common libgnomevfs2-0 libgnutls26 libgomp1 libgphoto2-2
  libgphoto2-port0 libgpm2 libgsl0ldbl libgstreamer0.10-0 libgtk2-perl
  libgtk2.0-bin libgtkhtml3.14-19 libgtksourceview2.0-0
  libgtksourceview2.0-common libgupnp-1.0-3 libgutenprint2 libgweather-common
  libhpmud0 libhtml-parser-perl libhtml-tagset-perl libhyphen0 libice6
  libicu42 libid3tag0 libido-0.1-0 libiec61883-0 libijs-0.35 libilmbase6
  libindicate4 libindicator0 libio-string-perl libiptcdata0 libjasper1
  libkate1 libkrb5-3 liblaunchpad-integration1 liblcms1 libldap-2.4-2
  liblircclient0 liblocale-gettext-perl liblockfile1 liblouis-data liblouis0
  liblualib50 liblzma1 libmad0 libmeanwhile1 libmetacity-private0 libmimic0
  libmjpegtools-1.9 libmng1 libmodplug0c2 libmono-addins0.2-cil
  libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-i18n-west2.0-cil
  libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil
  libmono-system-web2.0-cil libmono-system2.0-cil libmp3lame0 libmpeg2-4
  libmusicbrainz4c2a libmysqlclient16 libnautilus-extension1 libncursesw5
  libnet-dbus-perl libnewt0.52 libnih-dbus1 libnih1 libnm-glib2 libnspr4-0d
  libnss-mdns libnss3-1d libntfs-3g75 libntfs10 libofa0 libopencore-amrnb0
  libopenexr6 libopenobex1 liborbit2 libpackagekit-glib2-12
  libpackagekit-qt-12 libpam-runtime libpangomm-1.4-1 libpaper1
  libparse-debianchangelog-perl libpciaccess0 libpcre3 libpcsclite1 libphonon4
  libpisock9 libpixman-1-0 libplasma3 libplist1 libpng12-0
  libpolkit-backend-1-0 libpolkit-qt-1-0 libpoppler-glib4 libpoppler5
  libpostproc51 libpulse-browse0 libqt4-assistant libqt4-designer libqt4-help
  libqt4-qt3support libqt4-scripttools libqt4-test libqt4-xml
  libqt4-xmlpatterns libraptor1 librasqal2 librsvg2-common libsasl2-2
  libsasl2-modules libschroedinger-1.0-0 libsdl1.2debian-alsa libselinux1
  libsensors4 libsidplay1 libsigc++-2.0-0c2a libsilcclient-1.1-3 libslang2
  libsm6 libsndfile1 libsolidcontrolifaces4 libspectre1 libss2 libssh-4
  libstartup-notification0 libstdc++6 libstlport4.6ldbl libstreamanalyzer0
  libsub-name-perl libtag1c2a libtalloc2 libtelepathy-farsight0
  libtext-charwidth-perl libunique-1.0-0 libvisual-0.4-0 libvisual-0.4-plugins
  libvorbis0a libvte9 libwebkit-1.0-2 libwebkit-1.0-common libwnck-common
  libwnck22 libwpd8c2a libwrap0 libwww-perl libx11-6 libx11-data libx264-85
  libxau6 libxaw7 libxcb-shape0 libxcb-xv0 libxcursor1 libxdamage1 libxfixes3
  libxft2 libxine1 libxine1-bin libxine1-x libxklavier16 libxml-twig-perl
  libxmu6 libxt6 libxtst6 libxvidcore4 libxxf86vm1 libzephyr4 light-themes
  linux-headers-2.6.32-25 linux-headers-2.6.32-27 linux-headers-2.6.32-29
  linux-headers-2.6.32-32 lsof ltrace make media-player-info mime-support
  min12xxw myspell-en-za nautilus net-tools openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib openoffice.org-base-core
  openoffice.org-common openoffice.org-writer openssh-client oss-compat
  oxygen-icon-theme passwd perl phonon phonon-backend-xine pkg-config
  plasma-scriptengine-javascript plymouth plymouth-label pnm2ppa policykit-1
  poppler-utils popularity-contest powermgmt-base pptp-linux pulseaudio
  pulseaudio-esound-compat python-apt python-aptdaemon-gtk python-central
  python-configglue python-couchdb python-crypto python-cups
  python-cupshelpers python-debian python-desktopcouch
  python-desktopcouch-records python-farsight python-gconf python-glade2
  python-gnomekeyring python-gobject python-gst0.10 python-gtk2
  python-gtksourceview2 python-httplib2 python-launchpadlib
  python-lazr.restfulclient python-libxml2 python-notify python-oauth
  python-openssl python-pam python-problem-report python-pygoocanvas
  python-pyinotify python-qt4 python-simplejson python-telepathy
  python-twisted-core python-twisted-names python-ubuntuone-storageprotocol
  python-uno python-wadllib python-webkit python-xapian python-xdg
  python2.6-minimal rarian-compat readline-common rtkit samba-common-bin
  screen scrollkeeper sgml-data software-properties-gtk strace syslinux
  system-config-printer-common sysvinit-utils time totem-common tsconf
  ttf-dejavu-core ttf-dejavu-extra ttf-opensymbol ubuntu-mono
  ubuntu-system-service udev unattended-upgrades unzip update-manager-kde
  upower upstart usbmuxd util-linux wbritish wodim x11-apps x11-common
  x11-xfs-utils x11-xserver-utils xauth xbitmaps xdg-user-dirs xdg-utils
  xfonts-75dpi xfonts-encodings xfonts-utils xinput xkb-data xml-core
  xorg-docs-core xserver-xorg-input-mouse xserver-xorg-video-ark
  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus
  xserver-xorg-video-geode xserver-xorg-video-i128 xserver-xorg-video-i740
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-r128 xserver-xorg-video-s3
  xserver-xorg-video-siliconmotion xserver-xorg-video-trident
  xserver-xorg-video-tseng xsltproc yelp zenity zip
Suggested packages:
  aptitude-doc-en aptitude-doc debtags aspell-doc spellutils bash-doc
  binutils-doc pax db4.7-util brltty-speechd vacation gnome-themes couchdb
  cpp-doc exim4 postfix mail-transport-agent anacron checksecurity cups-bsd
  cups-ppdc hplip xpdf-korean xpdf-japanese xpdf-chinese-traditional
  xpdf-chinese-simplified cups-pdf smbclient defoma-doc x-ttcidfont-conf
  dfontmgr libfont-freetype-perl docbook docbook-dsssl docbook-xsl
  docbook-defguide gpart e2fsck-static cdtool setcd erlang erlang-manpages
  erlang-doc-html mlocate locate slocate firefox-gnome-support kmozillahelper
  latex-xft-fonts hplip-cups m2300w openprinting-ppds-extra cjet
  foomatic-db-hpijs foomatic-db-gutenprint foomatic-gui ghostscript-x
  gnupg-doc groff less hunspell texinfo-doc-nonfree bootchart traceroute
  isoquery konqueror nas glibc-doc libcanberra-pulse libcwidget-dev libdvdcss2
  esound-clients esound monodoc-gtk2.0-manual libgnomevfs2-bin
  libgnomevfs2-extra gnutls-bin gphoto2 gtkam gpm gsl-ref-psdoc gsl-doc-pdf
  gsl-doc-info gsl-ref-html gstreamer0.10-plugins libgtk2-perl-doc
  libgtkhtml3.14-dbg gutenprint-locales libdata-dump-perl libjasper-runtime
  krb5-doc krb5-user liblcms-utils lirc libmono-i18n2.0-cil
  libmono-winforms2.0-cil libhtml-template-perl libxml-simple-perl pcscd
  jpilot pilot-link kpilot gnome-pilot evolution claws-mail sylpheed
  raptor-utils libsasl2-modules-otp libsasl2-modules-ldap libsasl2-modules-sql
  libsasl2-modules-gssapi-mit libsasl2-modules-gssapi-heimdal sidplay-base
  xsidplay libspectre1-dbg libcrypt-ssleay-perl libio-socket-ssl-perl gxine
  xine-ui libxine1-doc libxine-doc libxine1-ffmpeg libunicode-map8-perl
  libunicode-string-perl xml-twig-tools make-doc gnome-app-install
  sun-java6-fonts ttf-sazanami-gothic ttf-kochi-gothic ttf-sazanami-mincho
  ttf-kochi-mincho ttf-telugu-fonts ttf-oriya-fonts ttf-kannada-fonts
  ttf-bengali-fonts openoffice.org-base openoffice.org-style-industrial
  openoffice.org-style-hicontrast openoffice.org-style-tango
  openoffice.org-style-crystal openoffice.org-style-oxygen openoffice.org-gcj
  openoffice.org-filter-binfilter openoffice.org-java-common libpam-ssh
  keychain openssh-blacklist openssh-blacklist-extra libterm-readline-gnu-perl
  libterm-readline-perl-perl phonon-backend-gstreamer phonon-backend-vlc
  phonon-backend-mplayer kcm-phonon-xine magicfilter apsfilter pavumeter paman
  paprefs python-apt-dbg python-apt-doc python-crypto-dbg python-gnome2-doc
  python-gtk2-doc python-gobject-dbg python-gst0.10-dev python-gst0.10-dbg
  python-numpy libgtksourceview2.0-dev python-libxml2-dbg python-openssl-doc
  python-openssl-dbg python-pam-dbg python-pyinotify-doc python-qt4-dbg
  python-tk python-qt3 python-wxgtk2.8 python-wxgtk2.6 python-profiler
  xapian-doc perlsgml doc-html-w3 opensp sash watershed bsd-mailx
  util-linux-locales cdrkit-doc mesa-utils nickle cairo-5c exo-utils debhelper
  xorg-docs firmware-linux ttf-dejavu
Recommended packages:
  iceweasel www-browser xserver-xorg-video-cyrix xserver-xorg-video-nsc
The following NEW packages will be installed:
  apport apt-utils aptdaemon aptitude arora aspell avahi-daemon bash
  bash-completion binutils bogofilter-bdb brltty bsdmainutils
  busybox-initramfs busybox-static ca-certificates ca-certificates-java
  cabextract cheese-common clamav-base compiz-fusion-plugins-main compiz-gnome
  compizconfig-backend-gconf console-terminus couchdb-bin cpio cpp cron cups
  dbus-x11 debconf-i18n defoma dhcp3-common docbook-xml dosfstools dpkg
  e2fsprogs eject erlang-crypto erlang-runtime-tools espeak-data findutils
  firefox fontconfig-config foomatic-db foomatic-db-engine foomatic-filters
  freepats ftp fuse-utils gcc-4.4-base gconf-defaults-service gconf2
  ghostscript ghostscript-cups gksu gnome-about gnome-desktop-data
  gnome-panel-data gnome-session-bin gnome-terminal-data gnupg gnupg-curl
  groff-base gstreamer0.10-gnonlin gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools
  gstreamer0.10-x gvfs gzip hunspell-en-ca icedtea-6-jre-cacao info
  initscripts insserv iptables iputils-ping iputils-tracepath iso-codes kbd
  kdebase-runtime-data kdelibs-data kdelibs5-data kdepimlibs5
  language-pack-gnome-en language-selector-common launchpad-integration libaa1
  libaccess-bridge-java libaccess-bridge-java-jni libacl1 libarchive1
  libatk1.0-0 libatk1.0-data libaudio2 libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-core6 libavahi-gobject0 libavformat52 libbeagle1
  libblkid1 libbonoboui2-common libboost-program-options1.40.0
  libbrasero-media0 libbrlapi0.5 libbsd0 libbz2-1.0 libc-bin libc6 libc6-i686
  libcaca0 libcairo-perl libcamel1.2-14 libcanberra-gtk0 libcanberra0 libcap2
  libcdparanoia0 libclucene0ldbl libcompizconfig0 libcouchdb-glib-1.0-2
  libcroco3 libcryptui0 libcupscgi1 libcupsimage2 libcupsppdc1 libcurl3
  libcwidget3 libdatrie1 libdb4.8 libdbusmenu-gtk1 libdbusmenu-qt2
  libdc1394-22 libdevkit-power-gobject1 libdjvulibre-text libdjvulibre21
  libdrm-intel1 libdrm-nouveau1 libdvdnav4 libebackend1.2-0 libedata-book1.2-2
  libedata-cal1.2-6 libedataserverui1.2-8 libedit2 libept0 libesd0 libexiv2-6
  libfaac0 libfaad2 libfile-copy-recursive-perl libfontenc1 libfs6 libgadu3
  libgail18 libgcj-bc libgcj-common libgdata-google1.2-1 libgdata1.2-1
  libglade2.0-cil libglib2.0-0 libglib2.0-cil libglibmm-2.4-1c2a libglitz1
  libgmime-2.4-2 libgnome-keyring0 libgnome-media0 libgnome-vfs2.0-cil
  libgnome2-0 libgnome2.24-cil libgnomecanvas2-common libgnomekbd-common
  libgnomeui-common libgnomevfs2-0 libgnutls26 libgomp1 libgphoto2-2
  libgphoto2-port0 libgpm2 libgsl0ldbl libgstreamer0.10-0 libgtk2-perl
  libgtk2.0-bin libgtkhtml3.14-19 libgtksourceview2.0-0
  libgtksourceview2.0-common libgupnp-1.0-3 libgutenprint2 libgweather-common
  libhpmud0 libhtml-parser-perl libhtml-tagset-perl libhyphen0 libice6
  libicu42 libid3tag0 libido-0.1-0 libiec61883-0 libijs-0.35 libilmbase6
  libindicate4 libindicator0 libio-string-perl libiptcdata0 libjasper1
  libkate1 libkrb5-3 liblaunchpad-integration1 liblcms1 libldap-2.4-2
  liblircclient0 liblocale-gettext-perl liblockfile1 liblouis-data liblouis0
  liblualib50 liblzma1 libmad0 libmeanwhile1 libmetacity-private0 libmimic0
  libmjpegtools-1.9 libmng1 libmodplug0c2 libmono-addins0.2-cil
  libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-i18n-west2.0-cil
  libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil
  libmono-system-web2.0-cil libmono-system2.0-cil libmp3lame0 libmpeg2-4
  libmusicbrainz4c2a libmysqlclient16 libnautilus-extension1 libncursesw5
  libnet-dbus-perl libnewt0.52 libnih-dbus1 libnih1 libnm-glib2 libnspr4-0d
  libnss-mdns libnss3-1d libntfs-3g75 libntfs10 libofa0 libopencore-amrnb0
  libopenexr6 libopenobex1 liborbit2 libpackagekit-glib2-12
  libpackagekit-qt-12 libpam-runtime libpangomm-1.4-1 libpaper1
  libparse-debianchangelog-perl libpciaccess0 libpcre3 libpcsclite1 libphonon4
  libpisock9 libpixman-1-0 libplasma3 libplist1 libpng12-0
  libpolkit-backend-1-0 libpolkit-qt-1-0 libpoppler-glib4 libpoppler5
  libpostproc51 libpulse-browse0 libqt4-assistant libqt4-designer libqt4-help
  libqt4-qt3support libqt4-scripttools libqt4-test libqt4-xml
  libqt4-xmlpatterns libraptor1 librasqal2 librsvg2-common libsasl2-2
  libsasl2-modules libschroedinger-1.0-0 libsdl1.2debian-alsa libselinux1
  libsensors4 libsidplay1 libsigc++-2.0-0c2a libsilcclient-1.1-3 libslang2
  libsm6 libsndfile1 libsolidcontrolifaces4 libspectre1 libss2 libssh-4
  libstartup-notification0 libstdc++6 libstlport4.6ldbl libstreamanalyzer0
  libsub-name-perl libtag1c2a libtalloc2 libtelepathy-farsight0
  libtext-charwidth-perl libunique-1.0-0 libvisual-0.4-0 libvisual-0.4-plugins
  libvorbis0a libvte9 libwebkit-1.0-2 libwebkit-1.0-common libwnck-common
  libwnck22 libwpd8c2a libwrap0 libwww-perl libx11-6 libx11-data libx264-85
  libxau6 libxaw7 libxcb-shape0 libxcb-xv0 libxcursor1 libxdamage1 libxfixes3
  libxft2 libxine1 libxine1-bin libxine1-x libxklavier16 libxml-twig-perl
  libxmu6 libxt6 libxtst6 libxvidcore4 libxxf86vm1 libzephyr4 light-themes
  linux-headers-2.6.32-25 linux-headers-2.6.32-27 linux-headers-2.6.32-29
  linux-headers-2.6.32-32 lsof ltrace make media-player-info mime-support
  min12xxw myspell-en-za nautilus net-tools openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib openoffice.org-base-core
  openoffice.org-common openoffice.org-writer openssh-client oss-compat
  oxygen-icon-theme passwd perl phonon phonon-backend-xine pkg-config
  plasma-scriptengine-javascript plymouth plymouth-label pnm2ppa policykit-1
  poppler-utils popularity-contest powermgmt-base pptp-linux pulseaudio
  pulseaudio-esound-compat python-apt python-aptdaemon-gtk python-central
  python-configglue python-couchdb python-crypto python-cups
  python-cupshelpers python-debian python-desktopcouch
  python-desktopcouch-records python-farsight python-gconf python-glade2
  python-gnomekeyring python-gobject python-gst0.10 python-gtk2
  python-gtksourceview2 python-httplib2 python-launchpadlib
  python-lazr.restfulclient python-libxml2 python-notify python-oauth
  python-openssl python-pam python-problem-report python-pygoocanvas
  python-pyinotify python-qt4 python-simplejson python-telepathy
  python-twisted-core python-twisted-names python-ubuntuone-storageprotocol
  python-uno python-wadllib python-webkit python-xapian python-xdg
  python2.6-minimal rarian-compat readline-common rtkit samba-common-bin
  screen scrollkeeper sgml-data software-properties-gtk strace syslinux
  system-config-printer-common sysvinit-utils time totem-common tsconf
  ttf-dejavu-core ttf-dejavu-extra ttf-opensymbol ubuntu-mono
  ubuntu-system-service udev unattended-upgrades unzip update-manager-kde
  upower upstart usbmuxd util-linux wbritish wodim x11-apps x11-common
  x11-xfs-utils x11-xserver-utils xauth xbitmaps xdg-user-dirs xdg-utils
  xfonts-75dpi xfonts-encodings xfonts-utils xinput xkb-data xml-core
  xorg-docs-core xserver-xorg-input-mouse xserver-xorg-video-ark
  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus
  xserver-xorg-video-geode xserver-xorg-video-i128 xserver-xorg-video-i740
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-r128 xserver-xorg-video-s3
  xserver-xorg-video-siliconmotion xserver-xorg-video-trident
  xserver-xorg-video-tseng xsltproc yelp zenity zip
0 upgraded, 496 newly installed, 0 to remove and 2 not upgraded.
2 not fully installed or removed.
Need to get 238kB/323MB of archives.
After this operation, 1,241MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main apt-utils 0.7.25.3ubuntu9.5 [238kB]
Fetched 238kB in 1s (213kB/s)     
E: Could not perform immediate configuration on 'libc6'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)


---

### Post by coffeecat on 2011-06-14
So near, yet so far! It seems to be working and then it trips up on this again:

```
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main apt-utils 0.7.25.3ubuntu9.5 [238kB]
Fetched 238kB in 1s (213kB/s)     
E: Could not perform immediate configuration on 'libc6'.Please see man 5  apt.conf under APT::Immediate-Configure for details. (2)
```I've done a bit of searching and this error seems to come up quite a bit. From what little I've read so far, there are references to circular dependencies and there are bug reports, involving debian as well. I'm just posting this quickly so that you know I haven't forgotten because I'd like to look into that error a bit more. In the meantime....

A couple of posters earlier in one of the threads suggested a hardware problem. Maybe, maybe not, but it would be remiss not to exclude this. Open Disk Utility from System > Adminitration, highlight the internal drive in the left pane and see what information there is about SMART data on the right.

Also - I was going to suggest running...

```
sudo apt-get dist-upgrade
```and/or...

```
sudo aptitude safe-upgrade
```

Both can be useful when the system gets in a pickle with dependencies, and 'apt-get dist-upgrade' **doesn't** do a distribution upgrade, contrary to popular belief and what its name might suggest. I don't believe it will do any harm to try either, but you might want to see what wildmanne39 thinks of this suggestion. I am happy for him to disagree or agree as he thinks best.

---

### Post by stevovets on 2011-06-14
okay, so in the Smart Data section I have 2 warnings:

ID 5: Reallocated Sector Count. Normalized: 195.  Worst: 195. Threshold: 140.  Value: 38 sectors.
ID 197: Current Pending Sector Count.  Normalized: 170. Worst: 150. Threshold: 0. Value: 385 sectors.

---

### Post by stevovets on 2011-06-14
for sudo apt-get dist-upgrade, I got this:

>   telepathy-gabble: Depends: libc6 (>= 2.4) but it is not installed
                    Depends: libglib2.0-0 (>= 2.23.5) but it is not installed
  telepathy-haze: Depends: libc6 (>= 2.4) but it is not installed
                  Depends: libglib2.0-0 (>= 2.22.0) but it is not installed
  telepathy-mission-control-5: Depends: libc6 (>= 2.7) but it is not installed
                               Depends: libglib2.0-0 (>= 2.23.5) but it is not installed
                               Depends: libgnome-keyring0 (>= 2.22.2) but it is not installed
  telnet: Depends: libc6 (>= 2.11) but it is not installed
          Depends: libstdc++6 (>= 4.1.1) but it is not installed
  timidity: Depends: libaudio2 but it is not installed
            Depends: libc6 (>= 2.7) but it is not installed
            Depends: libesd0 (>= 0.2.35) but it is not installed
            Depends: libice6 (>= 1:1.0.0) but it is not installed
            Depends: libpng12-0 (>= 1.2.13-4) but it is not installed
            Depends: libsm6 but it is not installed
            Depends: libvorbis0a (>= 1.1.2) but it is not installed
            Depends: libx11-6 but it is not installed
            Depends: libxaw7 but it is not installed
            Depends: libxmu6 but it is not installed
            Depends: libxt6 but it is not installed
            Recommends: freepats but it is not installed
  tk8.4: Depends: libc6 (>= 2.7) but it is not installed
         Depends: libx11-6 but it is not installed
  totem: Depends: libatk1.0-0 (>= 1.29.3) but it is not installed
         Depends: libc6 (>= 2.7) but it is not installed
         Depends: libglib2.0-0 (>= 2.23.5) but it is not installed
         Depends: libgstreamer0.10-0 (>= 0.10.26) but it is not installed
         Depends: libice6 (>= 1:1.0.0) but it is not installed
         Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
         Depends: libnautilus-extension1 (>= 1:2.29.1) but it is not installed
         Depends: libsm6 but it is not installed
         Depends: libunique-1.0-0 (>= 1.0.0) but it is not installed
         Depends: libx11-6 (>= 0) but it is not installed
         Depends: libxtst6 but it is not installed
         Depends: libxxf86vm1 but it is not installed
         Depends: gstreamer0.10-plugins-base (>= 0.10.26) but it is not installed
         Depends: gstreamer0.10-plugins-good (>= 0.10.7) but it is not installed
         Depends: gstreamer0.10-x but it is not installed
         Depends: totem-common (>= 2.30) but it is not installed
         Depends: totem-common (< 2.31) but it is not installed
         Recommends: totem-plugins (>= 2.30.2-0ubuntu1) but it is not installed
  totem-mozilla: Depends: libc6 (>= 2.4) but it is not installed
                 Depends: libglib2.0-0 (>= 2.22) but it is not installed
                 Depends: libstdc++6 (>= 4.1.1) but it is not installed
                 Depends: libx11-6 but it is not installed
                 Depends: dbus-x11 (>= 0.61) but it is not installed
                 Recommends: epiphany-browser but it is not installed or
                             www-browser
  transmission-gtk: Depends: libc6 (>= 2.11) but it is not installed
                    Depends: libcanberra-gtk0 (>= 0.2) but it is not installed
                    Depends: libcanberra0 (>= 0.2) but it is not installed
                    Depends: libglib2.0-0 (>= 2.23.5) but it is not installed
                    Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
                    Recommends: xdg-utils but it is not installed
  ttf-mscorefonts-installer: Depends: cabextract but it is not installed
                             Depends: xfonts-utils but it is not installed
                             Depends: defoma but it is not installed
                             Recommends: x-ttcidfont-conf but it is not installed
  ttf-unfonts-core: Depends: defoma but it is not installed
  tuxguitar: Depends: openjdk-6-jre but it is not installed or
                      sun-java6-jre but it is not installable or
                      sun-java5-jre but it is not installable or
                      java-gcj-compat-headless or
                      java-virtual-machine
  ubuntu-artwork: Depends: light-themes but it is not installed
  ubuntu-standard: Depends: aptitude but it is not installed
                   Depends: busybox-static but it is not installed
                   Depends: cpio but it is not installed
                   Depends: cron
                   Depends: dosfstools but it is not installed
                   Depends: ftp
                   Depends: info but it is not installed
                   Depends: iptables but it is not installed
                   Depends: language-selector-common but it is not installed
                   Depends: lsof but it is not installed
                   Depends: ltrace but it is not installed
                   Depends: mime-support but it is not installed
                   Depends: popularity-contest but it is not installed
                   Depends: strace but it is not installed
                   Depends: time but it is not installed
                   Recommends: apparmor-utils but it is not installed
                   Recommends: bash-completion but it is not installed
                   Recommends: command-not-found but it is not installed
                   Recommends: friendly-recovery but it is not installed
                   Recommends: iputils-arping but it is not installed
                   Recommends: iputils-tracepath but it is not installed
                   Recommends: irqbalance but it is not installed
                   Recommends: mlocate but it is not installed
                   Recommends: nano but it is not installed
                   Recommends: openssh-client but it is not installed
                   Recommends: plymouth but it is not installed
                   Recommends: plymouth-theme-ubuntu-text but it is not installed
                   Recommends: pppoeconf but it is not installed
                   Recommends: ufw but it is not installed
                   Recommends: w3m but it is not installed
  ubuntu-wallpapers: Depends: gconf2 (>= 2.12.1-1) but it is not installed
  ubuntuone-client: Depends: python-configglue but it is not installed
  ubuntuone-client-gnome: Depends: libatk1.0-0 (>= 1.29.3) but it is not installed
                          Depends: libc6 (>= 2.3.6-6~) but it is not installed
                          Depends: libglib2.0-0 (>= 2.23.5) but it is not installed
                          Depends: libnautilus-extension1 (>= 1:2.29.1) but it is not installed
                          Depends: liborbit2 (>= 1:2.14.10) but it is not installed
                          Depends: python-gtk2 (>= 2.10) but it is not installed
                          Depends: python-simplejson but it is not installed
  udisks: Depends: libc6 (>= 2.7) but it is not installed
          Depends: libglib2.0-0 (>= 2.23.5) but it is not installed
          Depends: libpolkit-backend-1-0 (>= 0.94) but it is not installed
          Depends: udev but it is not installed
          Recommends: policykit-1 but it is not installed
          Recommends: dosfstools but it is not installed
  uno-libs3: Depends: libc6 (>= 2.7) but it is not installed
             Depends: libstdc++6 (>= 4.1.1) but it is not installed
             Depends: libstlport4.6ldbl but it is not installed
  update-inetd: Depends: libfile-copy-recursive-perl but it is not installed
  update-manager-core: Depends: python-central (>= 0.6.11) but it is not installed
                       Depends: python-apt (>= 0.7.13.4ubuntu3) but it is not installed
  ure: Depends: libc6 (>= 2.11) but it is not installed
       Depends: libstdc++6 (>= 4.1.1) but it is not installed
       Depends: libstlport4.6ldbl but it is not installed
  usb-creator-common: Depends: python-central (>= 0.6.11) but it is not installed
                      Depends: syslinux but it is not installed
  usbutils: Depends: libc6 (>= 2.4) but it is not installed
  uuid-runtime: Depends: passwd but it is not installed
                Depends: libc6 (>= 2.4) but it is not installed
  vim-common: Depends: libc6 (>= 2.4) but it is not installed
              Recommends: vim or
                          vim-gnome but it is not installed or
                          vim-gtk but it is not installed or
                          vim-lesstif but it is not installable or
                          vim-nox but it is not installed or
                          vim-tiny but it is not installed
  vinagre: Depends: libatk1.0-0 (>= 1.29.3) but it is not installed
           Depends: libavahi-client3 (>= 0.6.16) but it is not installed
           Depends: libavahi-common3 (>= 0.6.16) but it is not installed
           Depends: libavahi-gobject0 (>= 0.6.22) but it is not installed
           Depends: libc6 (>= 2.4) but it is not installed
           Depends: libglib2.0-0 (>= 2.23.5) but it is not installed
           Depends: libgnome-keyring0 (>= 2.20.3) but it is not installed
           Depends: libgnome2-0 (>= 2.17.3) but it is not installed
           Depends: libgnutls26 (>= 2.7.14-0) but it is not installed
           Depends: liblaunchpad-integration1 (>= 0.1.17) but it is not installed
           Depends: liborbit2 (>= 1:2.14.10) but it is not installed
           Depends: libvte9 (>= 1:0.22.0) but it is not installed
           Depends: libx11-6 (>= 0) but it is not installed
           Depends: gconf2 (>= 2.10.1-2) but it is not installed
  wget: Depends: libc6 (>= 2.11) but it is not installed
  whiptail: Depends: libc6 (>= 2.4) but it is not installed
            Depends: libnewt0.52 (>= 0.52.10) but it is not installed
            Depends: libslang2 (>= 2.0.7-1) but it is not installed
  whois: Depends: libc6 (>= 2.4) but it is not installed
  wireless-crda: Depends: udev but it is not installed
  wpasupplicant: Depends: libc6 (>= 2.4) but it is not installed
                 Depends: libpcsclite1 (>= 1.5.3) but it is not installed
  x11-session-utils: Depends: libc6 (>= 2.7) but it is not installed
                     Depends: libice6 (>= 1:1.0.0) but it is not installed
                     Depends: libsm6 but it is not installed
                     Depends: libx11-6 but it is not installed
                     Depends: libxaw7 but it is not installed
                     Depends: libxmu6 but it is not installed
                     Depends: libxt6 but it is not installed
                     Depends: cpp but it is not installed
                     PreDepends: x11-common (>= 1:7.0.0) but it is not installed
  x11-utils: Depends: libc6 (>= 2.7) but it is not installed
             Depends: libfontenc1 but it is not installed
             Depends: libx11-6 (>= 0) but it is not installed
             Depends: libxaw7 but it is not installed
             Depends: libxft2 (> 2.1.1) but it is not installed
             Depends: libxmu6 but it is not installed
             Depends: libxt6 but it is not installed
             Depends: libxtst6 but it is not installed
             Depends: libxxf86vm1 but it is not installed
             Depends: cpp but it is not installed
             PreDepends: x11-common (>= 1:7.0.0) but it is not installed
  x11-xkb-utils: Depends: libc6 (>= 2.7) but it is not installed
                 Depends: libx11-6 but it is not installed
                 Depends: libxaw7 but it is not installed
                 Depends: libxmu6 but it is not installed
                 Depends: libxt6 but it is not installed
                 Depends: cpp but it is not installed
                 PreDepends: x11-common (>= 1:7.0.0) but it is not installed
  xdg-user-dirs-gtk: Depends: libc6 (>= 2.3.6-6~) but it is not installed
                     Depends: libglib2.0-0 (>= 2.12.0) but it is not installed
                     Depends: xdg-user-dirs but it is not installed
  xfonts-100dpi: Depends: xfonts-utils but it is not installed
  xfonts-base: Depends: xfonts-utils but it is not installed
  xfonts-mathml: Depends: xfonts-utils but it is not installed
  xfonts-scalable: Depends: xfonts-utils but it is not installed
  xinit: Depends: libc6 (>= 2.4) but it is not installed
         Depends: libx11-6 but it is not installed
         Depends: x11-common but it is not installed
         Depends: xauth but it is not installed
  xorg: Depends: xfonts-75dpi (>= 1:1.0.0-1) but it is not installed
        Depends: x11-apps but it is not installed
        Depends: x11-xfs-utils but it is not installed
        Depends: x11-xserver-utils but it is not installed
        Depends: xauth but it is not installed
        Depends: xfonts-utils but it is not installed
        Depends: xkb-data but it is not installed
        Depends: xorg-docs-core but it is not installed
        Depends: x11-common but it is not installed
        Depends: xinput but it is not installed
  xscreensaver-data: Depends: libc6 (>= 2.7) but it is not installed
                     Depends: libglib2.0-0 (>= 2.12.0) but it is not installed
                     Depends: libice6 (>= 1:1.0.0) but it is not installed
                     Depends: libsm6 but it is not installed
                     Depends: libx11-6 (>= 0) but it is not installed
                     Depends: libxmu6 but it is not installed
                     Depends: libxt6 but it is not installed
  xserver-common: Depends: x11-common but it is not installed
                  Depends: xkb-data but it is not installed
  xserver-xorg: Depends: libc6 (>= 2.7) but it is not installed
                Depends: xkb-data (>= 1.4) but it is not installed
  xserver-xorg-core: Depends: udev (>= 149) but it is not installed
                     Depends: libc6 (>= 2.7) but it is not installed
                     Depends: libpciaccess0 (>= 0.10.7) but it is not installed
                     Depends: libpixman-1-0 (>= 0.15.16) but it is not installed
                     Depends: libxau6 but it is not installed
  xserver-xorg-input-evdev: Depends: libc6 (>= 2.7) but it is not installed
  xserver-xorg-input-synaptics: Depends: udev but it is not installed
                                Depends: libc6 (>= 2.4) but it is not installed
                                Depends: libpciaccess0 but it is not installed
                                Depends: libpixman-1-0 but it is not installed
                                Depends: libx11-6 (>= 0) but it is not installed
  xserver-xorg-input-vmmouse: Depends: libc6 (>= 2.7) but it is not installed
                              Depends: xserver-xorg-input-mouse but it is not installed
                              Depends: udev but it is not installed
  xserver-xorg-input-wacom: Depends: libc6 (>= 2.7) but it is not installed
                            Depends: libx11-6 (>= 0) but it is not installed
  xserver-xorg-video-all: Depends: xserver-xorg-video-ark but it is not installed
                          Depends: xserver-xorg-video-ati but it is not installed
                          Depends: xserver-xorg-video-chips but it is not installed
                          Depends: xserver-xorg-video-cirrus but it is not installed
                          Depends: xserver-xorg-video-geode but it is not installed
                          Depends: xserver-xorg-video-i128 but it is not installed
                          Depends: xserver-xorg-video-i740 but it is not installed
                          Depends: xserver-xorg-video-intel but it is not installed
                          Depends: xserver-xorg-video-mga but it is not installed
                          Depends: xserver-xorg-video-neomagic but it is not installed
                          Depends: xserver-xorg-video-nouveau but it is not installed
                          Depends: xserver-xorg-video-nv but it is not installed
                          Depends: xserver-xorg-video-s3 but it is not installed
                          Depends: xserver-xorg-video-siliconmotion but it is not installed
                          Depends: xserver-xorg-video-trident but it is not installed
                          Depends: xserver-xorg-video-tseng but it is not installed
                          Depends: x11-common but it is not installed
  xserver-xorg-video-apm: Depends: libc6 (>= 2.4) but it is not installed
  xserver-xorg-video-fbdev: Depends: libc6 (>= 2.1.3) but it is not installed
  xserver-xorg-video-openchrome: Depends: libc6 (>= 2.4) but it is not installed
                                 Depends: libx11-6 (>= 0) but it is not installed
  xserver-xorg-video-radeon: Depends: libc6 (>= 2.7) but it is not installed
                             Depends: libpciaccess0 (>= 0.10.2) but it is not installed
                             Depends: libpixman-1-0 but it is not installed
  xserver-xorg-video-rendition: Depends: libc6 (>= 2.4) but it is not installed
  xserver-xorg-video-s3virge: Depends: libc6 (>= 2.1.3) but it is not installed
  xserver-xorg-video-savage: Depends: libc6 (>= 2.3.4) but it is not installed
  xserver-xorg-video-sis: Depends: libc6 (>= 2.7) but it is not installed
  xserver-xorg-video-sisusb: Depends: libc6 (>= 2.7) but it is not installed
  xserver-xorg-video-tdfx: Depends: libc6 (>= 2.1.3) but it is not installed
  xserver-xorg-video-v4l: Depends: libc6 (>= 2.4) but it is not installed
  xserver-xorg-video-vesa: Depends: libc6 (>= 2.1.3) but it is not installed
  xserver-xorg-video-vmware: Depends: libc6 (>= 2.4) but it is not installed
  xserver-xorg-video-voodoo: Depends: libc6 (>= 2.1.3) but it is not installed
  xterm: Depends: xbitmaps but it is not installed
         Depends: libc6 (>= 2.11) but it is not installed
         Depends: libice6 (>= 1:1.0.0) but it is not installed
         Depends: libx11-6 (>= 0) but it is not installed
         Depends: libxaw7 but it is not installed
         Depends: libxft2 (> 2.1.1) but it is not installed
         Depends: libxmu6 but it is not installed
         Depends: libxt6 but it is not installed
  xulrunner-1.9.2: Depends: libatk1.0-0 (>= 1.29.3) but it is not installed
                   Depends: libc6 (>= 2.11) but it is not installed
                   Depends: libglib2.0-0 (>= 2.23.5) but it is not installed
                   Depends: libnspr4-0d (>= 4.7.3-0ubuntu1~) but it is not installed
                   Depends: libnss3-1d (>= 3.12.6) but it is not installed
                   Depends: libpixman-1-0 (>= 0.11.2) but it is not installed
                   Depends: libstartup-notification0 (>= 0.10) but it is not installed
                   Depends: libstdc++6 (>= 4.1.1) but it is not installed
                   Depends: libx11-6 (>= 0) but it is not installed
                   Depends: libxt6 but it is not installed
  zlib1g: Depends: libc6 (>= 2.4) but it is not installed
E: Unmet dependencies. Try using -f.


for sudo-aptitude safe-upgrade, I got this:
> doops@doops:~$ sudo aptitude safe-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
open: 81; closed: 355; defer: 595; conflict: 1                                 oResolving dependencies...
open: 68; closed: 389; defer: 681; conflict: 1                                 .Resolving dependencies...
open: 67; closed: 441; defer: 787; conflict: 1                                 .Resolving dependencies...
Resolving dependencies...
open: 15; closed: 1065; defer: 1818; conflict: 1                               OResolving dependencies...
Resolving dependencies...
open: 14; closed: 1186; defer: 2096; conflict: 1                               oResolving dependencies...
Resolving dependencies...
The following NEW packages will be installed:
  apport{a} apt-utils{a} aptdaemon{a} aptitude{a} aspell{a} avahi-daemon{a} 
  bash{a} bash-completion{a} binutils{a} bogofilter-bdb{a} brltty{a} 
  bsdmainutils{a} busybox-initramfs{a} busybox-static{a} ca-certificates{a} 
  ca-certificates-java{a} cabextract{a} cheese-common{a} 
  compiz-fusion-plugins-main{a} compiz-gnome{a} 
  compizconfig-backend-gconf{a} console-terminus{a} couchdb-bin{a} cpio{a} 
  cpp{a} cron{a} cups{a} dbus-x11{a} debconf-english{a} defoma{a} 
  dhcp3-common{a} docbook-xml{a} dosfstools{a} dpkg{a} e2fsprogs{a} 
  eject{a} erlang-crypto{a} erlang-runtime-tools{a} espeak-data{a} 
  findutils{a} firefox{a} fontconfig-config{a} foomatic-db{a} 
  foomatic-db-engine{a} foomatic-filters{a} freepats{a} ftp{a} 
  fuse-utils{a} gcc-4.4-base{a} gconf-defaults-service{a} gconf2{a} 
  ghostscript{a} ghostscript-cups{a} gksu{a} gnome-about{a} 
  gnome-desktop-data{a} gnome-panel-data{a} gnome-session-bin{a} 
  gnome-terminal-data{a} gnupg{a} gnupg-curl{a} groff-base{a} 
  gstreamer0.10-gnonlin{a} gstreamer0.10-plugins-base{a} 
  gstreamer0.10-plugins-good{a} gstreamer0.10-pulseaudio{a} 
  gstreamer0.10-tools{a} gstreamer0.10-x{a} gvfs{a} gzip{a} 
  hunspell-en-ca{a} icedtea-6-jre-cacao{a} info{a} initscripts{a} 
  insserv{a} iptables{a} iputils-ping{a} iputils-tracepath{a} iso-codes{a} 
  kbd{a} kdebase-runtime-data{a} kdelibs-data{a} kdelibs5-data{a} 
  kdepimlibs5{a} language-pack-gnome-en{a} language-selector-common{a} 
  launchpad-integration{a} libaa1{a} libaccess-bridge-java{a} 
  libaccess-bridge-java-jni{a} libacl1{a} libarchive1{a} libatk1.0-0{a} 
  libatk1.0-data{a} libaudio2{a} libavahi-client3{a} 
  libavahi-common-data{a} libavahi-common3{a} libavahi-core6{a} 
  libavahi-gobject0{a} libavformat52{a} libbeagle1{a} libblkid1{a} 
  libbonoboui2-common{a} libboost-program-options1.40.0{a} 
  libbrasero-media0{a} libbrlapi0.5{a} libbsd0{a} libbz2-1.0{a} libc-bin{a} 
  libc6{a} libc6-i686{a} libcaca0{a} libcairo-perl{a} libcamel1.2-14{a} 
  libcanberra-gtk0{a} libcanberra0{a} libcap2{a} libcdparanoia0{a} 
  libclucene0ldbl{a} libcompizconfig0{a} libcouchdb-glib-1.0-2{a} 
  libcroco3{a} libcryptui0{a} libcupscgi1{a} libcupsimage2{a} 
  libcupsppdc1{a} libcurl3{a} libcwidget3{a} libdatrie1{a} libdb4.8{a} 
  libdbusmenu-gtk1{a} libdbusmenu-qt2{a} libdc1394-22{a} 
  libdevkit-power-gobject1{a} libdjvulibre-text{a} libdjvulibre21{a} 
  libdrm-intel1{a} libdrm-nouveau1{a} libdvdnav4{a} libebackend1.2-0{a} 
  libedata-book1.2-2{a} libedata-cal1.2-6{a} libedataserverui1.2-8{a} 
  libedit2{a} libept0{a} libesd0{a} libexiv2-6{a} libfaac0{a} libfaad2{a} 
  libfile-copy-recursive-perl{a} libfontenc1{a} libfs6{a} libgadu3{a} 
  libgail18{a} libgcj-bc{a} libgcj-common{a} libgdata-google1.2-1{a} 
  libgdata1.2-1{a} libglade2.0-cil{a} libglib2.0-0{a} libglib2.0-cil{a} 
  libglibmm-2.4-1c2a{a} libglitz1{a} libgmime-2.4-2{a} libgnome-keyring0{a} 
  libgnome-media0{a} libgnome-vfs2.0-cil{a} libgnome2-0{a} 
  libgnome2.24-cil{a} libgnomecanvas2-common{a} libgnomekbd-common{a} 
  libgnomeui-common{a} libgnomevfs2-0{a} libgnutls26{a} libgomp1{a} 
  libgphoto2-2{a} libgphoto2-port0{a} libgpm2{a} libgsl0ldbl{a} 
  libgstreamer0.10-0{a} libgtk2-perl{a} libgtk2.0-bin{a} 
  libgtkhtml3.14-19{a} libgtksourceview2.0-0{a} 
  libgtksourceview2.0-common{a} libgupnp-1.0-3{a} libgutenprint2{a} 
  libgweather-common{a} libhpmud0{a} libhtml-parser-perl{a} 
  libhtml-tagset-perl{a} libhyphen0{a} libice6{a} libicu42{a} libid3tag0{a} 
  libido-0.1-0{a} libiec61883-0{a} libijs-0.35{a} libilmbase6{a} 
  libindicate4{a} libindicator0{a} libio-string-perl{a} libiptcdata0{a} 
  libjasper1{a} libkate1{a} libkrb5-3{a} liblaunchpad-integration1{a} 
  liblcms1{a} libldap-2.4-2{a} liblircclient0{a} liblocale-gettext-perl{a} 
  liblockfile1{a} liblouis-data{a} liblouis0{a} liblualib50{a} liblzma1{a} 
  libmad0{a} libmeanwhile1{a} libmetacity-private0{a} libmimic0{a} 
  libmjpegtools-1.9{a} libmng1{a} libmodplug0c2{a} libmono-addins0.2-cil{a} 
  libmono-cairo2.0-cil{a} libmono-corlib2.0-cil{a} 
  libmono-i18n-west2.0-cil{a} libmono-security2.0-cil{a} 
  libmono-sharpzip2.84-cil{a} libmono-sqlite2.0-cil{a} 
  libmono-system-web2.0-cil{a} libmono-system2.0-cil{a} libmp3lame0{a} 
  libmpeg2-4{a} libmusicbrainz4c2a{a} libmysqlclient16{a} 
  libnautilus-extension1{a} libncursesw5{a} libnet-dbus-perl{a} 
  libnewt0.52{a} libnih-dbus1{a} libnih1{a} libnm-glib2{a} libnspr4-0d{a} 
  libnss-mdns{a} libnss3-1d{a} libntfs-3g75{a} libntfs10{a} libofa0{a} 
  libopencore-amrnb0{a} libopenexr6{a} libopenobex1{a} liborbit2{a} 
  libpackagekit-glib2-12{a} libpackagekit-qt-12{a} libpam-runtime{a} 
  libpangomm-1.4-1{a} libpaper1{a} libparse-debianchangelog-perl{a} 
  libpciaccess0{a} libpcre3{a} libpcsclite1{a} libphonon4{a} libpisock9{a} 
  libpixman-1-0{a} libplasma3{a} libplist1{a} libpng12-0{a} 
  libpolkit-backend-1-0{a} libpolkit-qt-1-0{a} libpoppler-glib4{a} 
  libpoppler5{a} libpostproc51{a} libpulse-browse0{a} libqt4-assistant{a} 
  libqt4-designer{a} libqt4-help{a} libqt4-qt3support{a} 
  libqt4-scripttools{a} libqt4-test{a} libqt4-xml{a} libqt4-xmlpatterns{a} 
  libraptor1{a} librasqal2{a} librsvg2-common{a} libsasl2-2{a} 
  libsasl2-modules{a} libschroedinger-1.0-0{a} libsdl1.2debian-all{a} 
  libselinux1{a} libsensors4{a} libsidplay1{a} libsigc++-2.0-0c2a{a} 
  libsilcclient-1.1-3{a} libslang2{a} libsm6{a} libsndfile1{a} 
  libspectre1{a} libss2{a} libssh-4{a} libstartup-notification0{a} 
  libstdc++6{a} libstlport4.6ldbl{a} libstreamanalyzer0{a} 
  libsub-name-perl{a} libtag1c2a{a} libtalloc2{a} libtelepathy-farsight0{a} 
  libtext-charwidth-perl{a} libunique-1.0-0{a} libvisual-0.4-0{a} 
  libvisual-0.4-plugins{a} libvorbis0a{a} libvte9{a} libwebkit-1.0-2{a} 
  libwebkit-1.0-common{a} libwnck-common{a} libwnck22{a} libwpd8c2a{a} 
  libwrap0{a} libwww-perl{a} libx11-6{a} libx11-data{a} libx264-85{a} 
  libxau6{a} libxaw7{a} libxcursor1{a} libxdamage1{a} libxfixes3{a} 
  libxft2{a} libxklavier16{a} libxml-twig-perl{a} libxmu6{a} libxt6{a} 
  libxtst6{a} libxvidcore4{a} libxxf86vm1{a} libzephyr4{a} light-themes{a} 
  linux-headers-2.6.32-25{a} linux-headers-2.6.32-27{a} 
  linux-headers-2.6.32-29{a} linux-headers-2.6.32-32{a} lsof{a} ltrace{a} 
  make{a} media-player-info{a} mime-support{a} min12xxw{a} myspell-en-za{a} 
  nautilus{a} net-tools{a} openjdk-6-jre{a} openjdk-6-jre-headless{a} 
  openjdk-6-jre-lib{a} openoffice.org-base-core{a} openoffice.org-common{a} 
  openoffice.org-writer{a} openssh-client{a} oss-compat{a} 
  oxygen-icon-theme{a} p7zip-full{a} passwd{a} perl{a} phonon{a} 
  phonon-backend-null{a} pkg-config{a} plasma-scriptengine-javascript{a} 
  plymouth{a} plymouth-label{a} pnm2ppa{a} policykit-1{a} poppler-utils{a} 
  popularity-contest{a} powermgmt-base{a} pptp-linux{a} pulseaudio{a} 
  pulseaudio-esound-compat{a} python-apt{a} python-aptdaemon-gtk{a} 
  python-central{a} python-configglue{a} python-couchdb{a} python-crypto{a} 
  python-cups{a} python-cupshelpers{a} python-debian{a} 
  python-desktopcouch{a} python-desktopcouch-records{a} python-farsight{a} 
  python-gconf{a} python-glade2{a} python-gnomekeyring{a} python-gobject{a} 
  python-gst0.10{a} python-gtk2{a} python-gtksourceview2{a} 
  python-httplib2{a} python-launchpadlib{a} python-lazr.restfulclient{a} 
  python-libxml2{a} python-notify{a} python-oauth{a} python-openssl{a} 
  python-pam{a} python-problem-report{a} python-pygoocanvas{a} 
  python-pyinotify{a} python-qt4{a} python-simplejson{a} 
  python-telepathy{a} python-twisted-core{a} python-twisted-names{a} 
  python-ubuntuone-storageprotocol{a} python-uno{a} python-wadllib{a} 
  python-webkit{a} python-xapian{a} python-xdg{a} python2.6-minimal{a} 
  rarian-compat{a} readline-common{a} rtkit{a} samba-common-bin{a} 
  screen{a} sgml-data{a} software-properties-gtk{a} strace{a} syslinux{a} 
  system-config-printer-common{a} sysvinit-utils{a} time{a} totem-common{a} 
  tsconf{a} ttf-dejavu-core{a} ttf-dejavu-extra{a} ttf-opensymbol{a} 
  ubuntu-mono{a} ubuntu-system-service{a} udev{a} unattended-upgrades{a} 
  update-manager-kde{a} upower{a} upstart{a} usbmuxd{a} util-linux{a} 
  wbritish{a} wodim{a} x11-apps{a} x11-common{a} x11-xfs-utils{a} 
  x11-xserver-utils{a} xauth{a} xbitmaps{a} xdg-user-dirs{a} xdg-utils{a} 
  xfonts-75dpi{a} xfonts-encodings{a} xfonts-utils{a} xinput{a} xkb-data{a} 
  xml-core{a} xorg-docs-core{a} xserver-xorg-input-mouse{a} 
  xserver-xorg-video-ark{a} xserver-xorg-video-ati{a} 
  xserver-xorg-video-chips{a} xserver-xorg-video-cirrus{a} 
  xserver-xorg-video-geode{a} xserver-xorg-video-i128{a} 
  xserver-xorg-video-i740{a} xserver-xorg-video-intel{a} 
  xserver-xorg-video-mach64{a} xserver-xorg-video-mga{a} 
  xserver-xorg-video-neomagic{a} xserver-xorg-video-nouveau{a} 
  xserver-xorg-video-nv{a} xserver-xorg-video-r128{a} 
  xserver-xorg-video-s3{a} xserver-xorg-video-siliconmotion{a} 
  xserver-xorg-video-trident{a} xserver-xorg-video-tseng{a} xsltproc{a} 
  yelp{a} zenity{a} 
The following packages will be REMOVED:
  audacity-data{u} clamav{u} clamav-freshclam{u} grub-common{u} 
  krosspython{u} ktorrent-data{u} libclamav6{u} libflac++6{u} 
  libsolidcontrol4{u} libtommath0{u} libwxbase2.8-0{u} libwxgtk2.8-0{u} 
  libxcb-shm0{u} libxine1-console{u} libxine1-misc-plugins{u} os-prober{u} 
  pidgin-data{u} 
The following packages will be upgraded:
  apt apt-transport-https 
The following partially installed packages will be configured:
  flashplugin-installer sysv-rc 
The following packages are RECOMMENDED but will NOT be installed:
  ubuntu-keyring 
2 packages upgraded, 486 newly installed, 17 to remove and 0 not upgraded.
Need to get 3,523kB/322MB of archives. After unpacking 1,161MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main apt 0.7.25.3ubuntu9.5 [1,811kB]
Get:2 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main debconf-english 1.5.28ubuntu4 [894B]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main apt-transport-https 0.7.25.3ubuntu9.5 [81.1kB]
Get:4 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main libsdl1.2debian-all 1.2.14-4ubuntu1.1 [216kB]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe p7zip-full 9.04~dfsg.1-1 [1,404kB]
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe phonon-backend-null 4:4.4.0-0ubuntu2 [10.3kB]
Fetched 3,523kB in 10s (332kB/s)                                                
E: Could not perform immediate configuration on 'libc6'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file '/var/lib/dpkg/status' near line 18945 package 'mawk':
 EOF during value of field `Description' (missing final newline)
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

---

### Post by wildmanne39 on 2011-06-14
> **coffeecat said:**
> So near, yet so far! It seems to be working and then it trips up on this again:

```
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main apt-utils 0.7.25.3ubuntu9.5 [238kB]
Fetched 238kB in 1s (213kB/s)     
E: Could not perform immediate configuration on 'libc6'.Please see man 5  apt.conf under APT::Immediate-Configure for details. (2)
```I've done a bit of searching and this error seems to come up quite a bit. From what little I've read so far, there are references to circular dependencies and there are bug reports, involving debian as well. I'm just posting this quickly so that you know I haven't forgotten because I'd like to look into that error a bit more. In the meantime....

A couple of posters earlier in one of the threads suggested a hardware problem. Maybe, maybe not, but it would be remiss not to exclude this. Open Disk Utility from System > Adminitration, highlight the internal drive in the left pane and see what information there is about SMART data on the right.

Also - I was going to suggest running...

```
sudo apt-get dist-upgrade
```and/or...

```
sudo aptitude safe-upgrade
```

Both can be useful when the system gets in a pickle with dependencies, and 'apt-get dist-upgrade' **doesn't** do a distribution upgrade, contrary to popular belief and what its name might suggest. I don't believe it will do any harm to try either, but you might want to see what wildmanne39 thinks of this suggestion. I am happy for him to disagree or agree as he thinks best.
Hi, I was going to suggest the sudo apt-get dist-upgrade but looking at my ubuntu book I took it to mean it would do a distribution upgrade, I have never seen the safe upgrade before, I am learning more from the masters every day. Thank for helping, I am going to let you continue since I reached my limit. I appreciate your effort very much.):P

---

### Post by coffeecat on 2011-06-14
Two things.

This doesn't look good to me:

> **stevovets said:**
> okay, so in the Smart Data section I have 2 warnings:

ID 5: Reallocated Sector Count. Normalized: 195.  Worst: 195. Threshold: 140.  Value: 38 sectors.
ID 197: Current Pending Sector Count.  Normalized: 170. Worst: 150. Threshold: 0. Value: 385 sectors.

@wildmanne39, what do you think?

The second is that googling this problem, some people solved this by forcing the installation of the libc6 package with 'sudo dpkg -i --force-depends *name-of-package*'.

I think the time may have come to try that, although it is not without its own risks. It could cause further problems - I really don't know. But tbh I think the time has come for extreme measures. If it was my system I would try the dpkg force option knowing that I might have to re-install. Then, if the dpkg force worked, I would monitor the hard drive situation in case it is failing. But it must be your choice - I can only suggest.

First things first. Make sure all your personal data is properly backed up. Double-reason: if you want to try the force option and your HD may be failing.

Next: post the output of:

```
ls /var/cache/apt/archives/libc6*
```We need the exact filename of the downloaded package for the dpkg command.

---

### Post by wildmanne39 on 2011-06-14
> **coffeecat said:**
> Two things.

This doesn't look good to me:



@wildmanne39, what do you think?

The second is that googling this problem, some people solved this by forcing the installation of the libc6 package with 'sudo dpkg -i --force-depends *name-of-package*'.

I think the time may have come to try that, although it is not without its own risks. It could cause further problems - I really don't know. But tbh I think the time has come for extreme measures. If it was my system I would try the dpkg force option knowing that I might have to re-install. Then, if the dpkg force worked, I would monitor the hard drive situation in case it is failing. But it must be your choice - I can only suggest.

First things first. Make sure all your personal data is properly backed up. Double-reason: if you want to try the force option and your HD may be failing.

Next: post the output of:

```
ls /var/cache/apt/archives/libc6*
```We need the exact filename of the downloaded package for the dpkg command.Hi, yes I thought that looked like there may have been some data lost on the hard drive. Thanks again, we will all learn from this experience.

---

### Post by stevovets on 2011-06-14
> doops@doops:~$ ls /var/cache/apt/archives/libc6*
/var/cache/apt/archives/libc6_2.11.1-0ubuntu7.8_i386.deb
/var/cache/apt/archives/libc6-i686_2.11.1-0ubuntu7.8_i386.deb


If it comes down to it, I guess I'll have to try it.  My computer is pretty old, so I suppose it wouldnt surprise me to see the hardware go on it.  Though I'm too much of a noob to not be surprised by everything hah.

Worst case scenario is I get a new HD

---

### Post by coffeecat on 2011-06-14
At the moment it's complaining about libc6, not libc6-i686, so let's concentrate on just that first one for now. I'm hoping that this is down to circular dependency - more than one of the google hits with your error message were said to be because of this. A circular dependency is where package A depends on package B, and won't install without B being installed first, but B depends on A and... You get the drift. By forcing the installation, you break the circle. Or at least that's the theory.

From a terminal...

```
cd /var/cache/apt/archives
sudo dpkg -i --force-depends libc6_2.11.1-0ubuntu7.8_i386.deb
```You will probably get a lot of error messages and moaning about dependencies from that, but hopefully it will install libc6. Now...

```
sudo apt-get -f install
```... and hope for the best. :?

> **wildmanne39 said:**
> I am going to let you continue since I reached my limit. I appreciate your effort very much.):P

Thanks, but I can assure you I am past my limit. :| This is not an everyday situation and one has to rely on extrapolating from earlier experience and what comes up from google. I'll keep my fingers crossed for stevovets.

---

### Post by stevovets on 2011-06-14
> doops@doops:~$ cd /var/cache/apt/archives
doops@doops:/var/cache/apt/archives$ sudo dpkg -i --force-depends libc6_2.11.1-0ubuntu7.8_i386.deb
dpkg: parse error, in file '/var/lib/dpkg/status' near line 18945 package 'mawk':
 EOF during value of field `Description' (missing final newline)
doops@doops:/var/cache/apt/archives$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libsolidcontrolifaces4 clamav libwxgtk2.8-0 clamav-freshclam audacity-data
  libflac++6 clamav-base libclamav6 pidgin-data krosspython libwxbase2.8-0
  os-prober libsolidcontrol4 ktorrent-data libtommath0 grub-common
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  apport apt-utils aptdaemon aptitude arora aspell avahi-daemon bash
  bash-completion binutils bogofilter-bdb brltty bsdmainutils
  busybox-initramfs busybox-static ca-certificates ca-certificates-java
  cabextract cheese-common clamav-base compiz-fusion-plugins-main compiz-gnome
  compizconfig-backend-gconf console-terminus couchdb-bin cpio cpp cron cups
  dbus-x11 debconf-i18n defoma dhcp3-common docbook-xml dosfstools dpkg
  e2fsprogs eject erlang-crypto erlang-runtime-tools espeak-data findutils
  firefox fontconfig-config foomatic-db foomatic-db-engine foomatic-filters
  freepats ftp fuse-utils gcc-4.4-base gconf-defaults-service gconf2
  ghostscript ghostscript-cups gksu gnome-about gnome-desktop-data
  gnome-panel-data gnome-session-bin gnome-terminal-data gnupg gnupg-curl
  groff-base gstreamer0.10-gnonlin gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools
  gstreamer0.10-x gvfs gzip hunspell-en-ca icedtea-6-jre-cacao info
  initscripts insserv iptables iputils-ping iputils-tracepath iso-codes kbd
  kdebase-runtime-data kdelibs-data kdelibs5-data kdepimlibs5
  language-pack-gnome-en language-selector-common launchpad-integration libaa1
  libaccess-bridge-java libaccess-bridge-java-jni libacl1 libarchive1
  libatk1.0-0 libatk1.0-data libaudio2 libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-core6 libavahi-gobject0 libavformat52 libbeagle1
  libblkid1 libbonoboui2-common libboost-program-options1.40.0
  libbrasero-media0 libbrlapi0.5 libbsd0 libbz2-1.0 libc-bin libc6 libc6-i686
  libcaca0 libcairo-perl libcamel1.2-14 libcanberra-gtk0 libcanberra0 libcap2
  libcdparanoia0 libclucene0ldbl libcompizconfig0 libcouchdb-glib-1.0-2
  libcroco3 libcryptui0 libcupscgi1 libcupsimage2 libcupsppdc1 libcurl3
  libcwidget3 libdatrie1 libdb4.8 libdbusmenu-gtk1 libdbusmenu-qt2
  libdc1394-22 libdevkit-power-gobject1 libdjvulibre-text libdjvulibre21
  libdrm-intel1 libdrm-nouveau1 libdvdnav4 libebackend1.2-0 libedata-book1.2-2
  libedata-cal1.2-6 libedataserverui1.2-8 libedit2 libept0 libesd0 libexiv2-6
  libfaac0 libfaad2 libfile-copy-recursive-perl libfontenc1 libfs6 libgadu3
  libgail18 libgcj-bc libgcj-common libgdata-google1.2-1 libgdata1.2-1
  libglade2.0-cil libglib2.0-0 libglib2.0-cil libglibmm-2.4-1c2a libglitz1
  libgmime-2.4-2 libgnome-keyring0 libgnome-media0 libgnome-vfs2.0-cil
  libgnome2-0 libgnome2.24-cil libgnomecanvas2-common libgnomekbd-common
  libgnomeui-common libgnomevfs2-0 libgnutls26 libgomp1 libgphoto2-2
  libgphoto2-port0 libgpm2 libgsl0ldbl libgstreamer0.10-0 libgtk2-perl
  libgtk2.0-bin libgtkhtml3.14-19 libgtksourceview2.0-0
  libgtksourceview2.0-common libgupnp-1.0-3 libgutenprint2 libgweather-common
  libhpmud0 libhtml-parser-perl libhtml-tagset-perl libhyphen0 libice6
  libicu42 libid3tag0 libido-0.1-0 libiec61883-0 libijs-0.35 libilmbase6
  libindicate4 libindicator0 libio-string-perl libiptcdata0 libjasper1
  libkate1 libkrb5-3 liblaunchpad-integration1 liblcms1 libldap-2.4-2
  liblircclient0 liblocale-gettext-perl liblockfile1 liblouis-data liblouis0
  liblualib50 liblzma1 libmad0 libmeanwhile1 libmetacity-private0 libmimic0
  libmjpegtools-1.9 libmng1 libmodplug0c2 libmono-addins0.2-cil
  libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-i18n-west2.0-cil
  libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil
  libmono-system-web2.0-cil libmono-system2.0-cil libmp3lame0 libmpeg2-4
  libmusicbrainz4c2a libmysqlclient16 libnautilus-extension1 libncursesw5
  libnet-dbus-perl libnewt0.52 libnih-dbus1 libnih1 libnm-glib2 libnspr4-0d
  libnss-mdns libnss3-1d libntfs-3g75 libntfs10 libofa0 libopencore-amrnb0
  libopenexr6 libopenobex1 liborbit2 libpackagekit-glib2-12
  libpackagekit-qt-12 libpam-runtime libpangomm-1.4-1 libpaper1
  libparse-debianchangelog-perl libpciaccess0 libpcre3 libpcsclite1 libphonon4
  libpisock9 libpixman-1-0 libplasma3 libplist1 libpng12-0
  libpolkit-backend-1-0 libpolkit-qt-1-0 libpoppler-glib4 libpoppler5
  libpostproc51 libpulse-browse0 libqt4-assistant libqt4-designer libqt4-help
  libqt4-qt3support libqt4-scripttools libqt4-test libqt4-xml
  libqt4-xmlpatterns libraptor1 librasqal2 librsvg2-common libsasl2-2
  libsasl2-modules libschroedinger-1.0-0 libsdl1.2debian-alsa libselinux1
  libsensors4 libsidplay1 libsigc++-2.0-0c2a libsilcclient-1.1-3 libslang2
  libsm6 libsndfile1 libsolidcontrolifaces4 libspectre1 libss2 libssh-4
  libstartup-notification0 libstdc++6 libstlport4.6ldbl libstreamanalyzer0
  libsub-name-perl libtag1c2a libtalloc2 libtelepathy-farsight0
  libtext-charwidth-perl libunique-1.0-0 libvisual-0.4-0 libvisual-0.4-plugins
  libvorbis0a libvte9 libwebkit-1.0-2 libwebkit-1.0-common libwnck-common
  libwnck22 libwpd8c2a libwrap0 libwww-perl libx11-6 libx11-data libx264-85
  libxau6 libxaw7 libxcb-shape0 libxcb-xv0 libxcursor1 libxdamage1 libxfixes3
  libxft2 libxine1 libxine1-bin libxine1-x libxklavier16 libxml-twig-perl
  libxmu6 libxt6 libxtst6 libxvidcore4 libxxf86vm1 libzephyr4 light-themes
  linux-headers-2.6.32-25 linux-headers-2.6.32-27 linux-headers-2.6.32-29
  linux-headers-2.6.32-32 lsof ltrace make media-player-info mime-support
  min12xxw myspell-en-za nautilus net-tools openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib openoffice.org-base-core
  openoffice.org-common openoffice.org-writer openssh-client oss-compat
  oxygen-icon-theme passwd perl phonon phonon-backend-xine pkg-config
  plasma-scriptengine-javascript plymouth plymouth-label pnm2ppa policykit-1
  poppler-utils popularity-contest powermgmt-base pptp-linux pulseaudio
  pulseaudio-esound-compat python-apt python-aptdaemon-gtk python-central
  python-configglue python-couchdb python-crypto python-cups
  python-cupshelpers python-debian python-desktopcouch
  python-desktopcouch-records python-farsight python-gconf python-glade2
  python-gnomekeyring python-gobject python-gst0.10 python-gtk2
  python-gtksourceview2 python-httplib2 python-launchpadlib
  python-lazr.restfulclient python-libxml2 python-notify python-oauth
  python-openssl python-pam python-problem-report python-pygoocanvas
  python-pyinotify python-qt4 python-simplejson python-telepathy
  python-twisted-core python-twisted-names python-ubuntuone-storageprotocol
  python-uno python-wadllib python-webkit python-xapian python-xdg
  python2.6-minimal rarian-compat readline-common rtkit samba-common-bin
  screen scrollkeeper sgml-data software-properties-gtk strace syslinux
  system-config-printer-common sysvinit-utils time totem-common tsconf
  ttf-dejavu-core ttf-dejavu-extra ttf-opensymbol ubuntu-mono
  ubuntu-system-service udev unattended-upgrades unzip update-manager-kde
  upower upstart usbmuxd util-linux wbritish wodim x11-apps x11-common
  x11-xfs-utils x11-xserver-utils xauth xbitmaps xdg-user-dirs xdg-utils
  xfonts-75dpi xfonts-encodings xfonts-utils xinput xkb-data xml-core
  xorg-docs-core xserver-xorg-input-mouse xserver-xorg-video-ark
  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus
  xserver-xorg-video-geode xserver-xorg-video-i128 xserver-xorg-video-i740
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-r128 xserver-xorg-video-s3
  xserver-xorg-video-siliconmotion xserver-xorg-video-trident
  xserver-xorg-video-tseng xsltproc yelp zenity zip
Suggested packages:
  aptitude-doc-en aptitude-doc debtags aspell-doc spellutils bash-doc
  binutils-doc pax db4.7-util brltty-speechd vacation gnome-themes couchdb
  cpp-doc exim4 postfix mail-transport-agent anacron checksecurity cups-bsd
  cups-ppdc hplip xpdf-korean xpdf-japanese xpdf-chinese-traditional
  xpdf-chinese-simplified cups-pdf smbclient defoma-doc x-ttcidfont-conf
  dfontmgr libfont-freetype-perl docbook docbook-dsssl docbook-xsl
  docbook-defguide gpart e2fsck-static cdtool setcd erlang erlang-manpages
  erlang-doc-html mlocate locate slocate firefox-gnome-support kmozillahelper
  latex-xft-fonts hplip-cups m2300w openprinting-ppds-extra cjet
  foomatic-db-hpijs foomatic-db-gutenprint foomatic-gui ghostscript-x
  gnupg-doc groff less hunspell texinfo-doc-nonfree bootchart traceroute
  isoquery konqueror nas glibc-doc libcanberra-pulse libcwidget-dev libdvdcss2
  esound-clients esound monodoc-gtk2.0-manual libgnomevfs2-bin
  libgnomevfs2-extra gnutls-bin gphoto2 gtkam gpm gsl-ref-psdoc gsl-doc-pdf
  gsl-doc-info gsl-ref-html gstreamer0.10-plugins libgtk2-perl-doc
  libgtkhtml3.14-dbg gutenprint-locales libdata-dump-perl libjasper-runtime
  krb5-doc krb5-user liblcms-utils lirc libmono-i18n2.0-cil
  libmono-winforms2.0-cil libhtml-template-perl libxml-simple-perl pcscd
  jpilot pilot-link kpilot gnome-pilot evolution claws-mail sylpheed
  raptor-utils libsasl2-modules-otp libsasl2-modules-ldap libsasl2-modules-sql
  libsasl2-modules-gssapi-mit libsasl2-modules-gssapi-heimdal sidplay-base
  xsidplay libspectre1-dbg libcrypt-ssleay-perl libio-socket-ssl-perl gxine
  xine-ui libxine1-doc libxine-doc libxine1-ffmpeg libunicode-map8-perl
  libunicode-string-perl xml-twig-tools make-doc gnome-app-install
  sun-java6-fonts ttf-sazanami-gothic ttf-kochi-gothic ttf-sazanami-mincho
  ttf-kochi-mincho ttf-telugu-fonts ttf-oriya-fonts ttf-kannada-fonts
  ttf-bengali-fonts openoffice.org-base openoffice.org-style-industrial
  openoffice.org-style-hicontrast openoffice.org-style-tango
  openoffice.org-style-crystal openoffice.org-style-oxygen openoffice.org-gcj
  openoffice.org-filter-binfilter openoffice.org-java-common libpam-ssh
  keychain openssh-blacklist openssh-blacklist-extra libterm-readline-gnu-perl
  libterm-readline-perl-perl phonon-backend-gstreamer phonon-backend-vlc
  phonon-backend-mplayer kcm-phonon-xine magicfilter apsfilter pavumeter paman
  paprefs python-apt-dbg python-apt-doc python-crypto-dbg python-gnome2-doc
  python-gtk2-doc python-gobject-dbg python-gst0.10-dev python-gst0.10-dbg
  python-numpy libgtksourceview2.0-dev python-libxml2-dbg python-openssl-doc
  python-openssl-dbg python-pam-dbg python-pyinotify-doc python-qt4-dbg
  python-tk python-qt3 python-wxgtk2.8 python-wxgtk2.6 python-profiler
  xapian-doc perlsgml doc-html-w3 opensp sash watershed bsd-mailx
  util-linux-locales cdrkit-doc mesa-utils nickle cairo-5c exo-utils debhelper
  xorg-docs firmware-linux ttf-dejavu
Recommended packages:
  iceweasel www-browser xserver-xorg-video-cyrix xserver-xorg-video-nsc
The following NEW packages will be installed:
  apport apt-utils aptdaemon aptitude arora aspell avahi-daemon bash
  bash-completion binutils bogofilter-bdb brltty bsdmainutils
  busybox-initramfs busybox-static ca-certificates ca-certificates-java
  cabextract cheese-common clamav-base compiz-fusion-plugins-main compiz-gnome
  compizconfig-backend-gconf console-terminus couchdb-bin cpio cpp cron cups
  dbus-x11 debconf-i18n defoma dhcp3-common docbook-xml dosfstools dpkg
  e2fsprogs eject erlang-crypto erlang-runtime-tools espeak-data findutils
  firefox fontconfig-config foomatic-db foomatic-db-engine foomatic-filters
  freepats ftp fuse-utils gcc-4.4-base gconf-defaults-service gconf2
  ghostscript ghostscript-cups gksu gnome-about gnome-desktop-data
  gnome-panel-data gnome-session-bin gnome-terminal-data gnupg gnupg-curl
  groff-base gstreamer0.10-gnonlin gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gstreamer0.10-pulseaudio gstreamer0.10-tools
  gstreamer0.10-x gvfs gzip hunspell-en-ca icedtea-6-jre-cacao info
  initscripts insserv iptables iputils-ping iputils-tracepath iso-codes kbd
  kdebase-runtime-data kdelibs-data kdelibs5-data kdepimlibs5
  language-pack-gnome-en language-selector-common launchpad-integration libaa1
  libaccess-bridge-java libaccess-bridge-java-jni libacl1 libarchive1
  libatk1.0-0 libatk1.0-data libaudio2 libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-core6 libavahi-gobject0 libavformat52 libbeagle1
  libblkid1 libbonoboui2-common libboost-program-options1.40.0
  libbrasero-media0 libbrlapi0.5 libbsd0 libbz2-1.0 libc-bin libc6 libc6-i686
  libcaca0 libcairo-perl libcamel1.2-14 libcanberra-gtk0 libcanberra0 libcap2
  libcdparanoia0 libclucene0ldbl libcompizconfig0 libcouchdb-glib-1.0-2
  libcroco3 libcryptui0 libcupscgi1 libcupsimage2 libcupsppdc1 libcurl3
  libcwidget3 libdatrie1 libdb4.8 libdbusmenu-gtk1 libdbusmenu-qt2
  libdc1394-22 libdevkit-power-gobject1 libdjvulibre-text libdjvulibre21
  libdrm-intel1 libdrm-nouveau1 libdvdnav4 libebackend1.2-0 libedata-book1.2-2
  libedata-cal1.2-6 libedataserverui1.2-8 libedit2 libept0 libesd0 libexiv2-6
  libfaac0 libfaad2 libfile-copy-recursive-perl libfontenc1 libfs6 libgadu3
  libgail18 libgcj-bc libgcj-common libgdata-google1.2-1 libgdata1.2-1
  libglade2.0-cil libglib2.0-0 libglib2.0-cil libglibmm-2.4-1c2a libglitz1
  libgmime-2.4-2 libgnome-keyring0 libgnome-media0 libgnome-vfs2.0-cil
  libgnome2-0 libgnome2.24-cil libgnomecanvas2-common libgnomekbd-common
  libgnomeui-common libgnomevfs2-0 libgnutls26 libgomp1 libgphoto2-2
  libgphoto2-port0 libgpm2 libgsl0ldbl libgstreamer0.10-0 libgtk2-perl
  libgtk2.0-bin libgtkhtml3.14-19 libgtksourceview2.0-0
  libgtksourceview2.0-common libgupnp-1.0-3 libgutenprint2 libgweather-common
  libhpmud0 libhtml-parser-perl libhtml-tagset-perl libhyphen0 libice6
  libicu42 libid3tag0 libido-0.1-0 libiec61883-0 libijs-0.35 libilmbase6
  libindicate4 libindicator0 libio-string-perl libiptcdata0 libjasper1
  libkate1 libkrb5-3 liblaunchpad-integration1 liblcms1 libldap-2.4-2
  liblircclient0 liblocale-gettext-perl liblockfile1 liblouis-data liblouis0
  liblualib50 liblzma1 libmad0 libmeanwhile1 libmetacity-private0 libmimic0
  libmjpegtools-1.9 libmng1 libmodplug0c2 libmono-addins0.2-cil
  libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-i18n-west2.0-cil
  libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil
  libmono-system-web2.0-cil libmono-system2.0-cil libmp3lame0 libmpeg2-4
  libmusicbrainz4c2a libmysqlclient16 libnautilus-extension1 libncursesw5
  libnet-dbus-perl libnewt0.52 libnih-dbus1 libnih1 libnm-glib2 libnspr4-0d
  libnss-mdns libnss3-1d libntfs-3g75 libntfs10 libofa0 libopencore-amrnb0
  libopenexr6 libopenobex1 liborbit2 libpackagekit-glib2-12
  libpackagekit-qt-12 libpam-runtime libpangomm-1.4-1 libpaper1
  libparse-debianchangelog-perl libpciaccess0 libpcre3 libpcsclite1 libphonon4
  libpisock9 libpixman-1-0 libplasma3 libplist1 libpng12-0
  libpolkit-backend-1-0 libpolkit-qt-1-0 libpoppler-glib4 libpoppler5
  libpostproc51 libpulse-browse0 libqt4-assistant libqt4-designer libqt4-help
  libqt4-qt3support libqt4-scripttools libqt4-test libqt4-xml
  libqt4-xmlpatterns libraptor1 librasqal2 librsvg2-common libsasl2-2
  libsasl2-modules libschroedinger-1.0-0 libsdl1.2debian-alsa libselinux1
  libsensors4 libsidplay1 libsigc++-2.0-0c2a libsilcclient-1.1-3 libslang2
  libsm6 libsndfile1 libsolidcontrolifaces4 libspectre1 libss2 libssh-4
  libstartup-notification0 libstdc++6 libstlport4.6ldbl libstreamanalyzer0
  libsub-name-perl libtag1c2a libtalloc2 libtelepathy-farsight0
  libtext-charwidth-perl libunique-1.0-0 libvisual-0.4-0 libvisual-0.4-plugins
  libvorbis0a libvte9 libwebkit-1.0-2 libwebkit-1.0-common libwnck-common
  libwnck22 libwpd8c2a libwrap0 libwww-perl libx11-6 libx11-data libx264-85
  libxau6 libxaw7 libxcb-shape0 libxcb-xv0 libxcursor1 libxdamage1 libxfixes3
  libxft2 libxine1 libxine1-bin libxine1-x libxklavier16 libxml-twig-perl
  libxmu6 libxt6 libxtst6 libxvidcore4 libxxf86vm1 libzephyr4 light-themes
  linux-headers-2.6.32-25 linux-headers-2.6.32-27 linux-headers-2.6.32-29
  linux-headers-2.6.32-32 lsof ltrace make media-player-info mime-support
  min12xxw myspell-en-za nautilus net-tools openjdk-6-jre
  openjdk-6-jre-headless openjdk-6-jre-lib openoffice.org-base-core
  openoffice.org-common openoffice.org-writer openssh-client oss-compat
  oxygen-icon-theme passwd perl phonon phonon-backend-xine pkg-config
  plasma-scriptengine-javascript plymouth plymouth-label pnm2ppa policykit-1
  poppler-utils popularity-contest powermgmt-base pptp-linux pulseaudio
  pulseaudio-esound-compat python-apt python-aptdaemon-gtk python-central
  python-configglue python-couchdb python-crypto python-cups
  python-cupshelpers python-debian python-desktopcouch
  python-desktopcouch-records python-farsight python-gconf python-glade2
  python-gnomekeyring python-gobject python-gst0.10 python-gtk2
  python-gtksourceview2 python-httplib2 python-launchpadlib
  python-lazr.restfulclient python-libxml2 python-notify python-oauth
  python-openssl python-pam python-problem-report python-pygoocanvas
  python-pyinotify python-qt4 python-simplejson python-telepathy
  python-twisted-core python-twisted-names python-ubuntuone-storageprotocol
  python-uno python-wadllib python-webkit python-xapian python-xdg
  python2.6-minimal rarian-compat readline-common rtkit samba-common-bin
  screen scrollkeeper sgml-data software-properties-gtk strace syslinux
  system-config-printer-common sysvinit-utils time totem-common tsconf
  ttf-dejavu-core ttf-dejavu-extra ttf-opensymbol ubuntu-mono
  ubuntu-system-service udev unattended-upgrades unzip update-manager-kde
  upower upstart usbmuxd util-linux wbritish wodim x11-apps x11-common
  x11-xfs-utils x11-xserver-utils xauth xbitmaps xdg-user-dirs xdg-utils
  xfonts-75dpi xfonts-encodings xfonts-utils xinput xkb-data xml-core
  xorg-docs-core xserver-xorg-input-mouse xserver-xorg-video-ark
  xserver-xorg-video-ati xserver-xorg-video-chips xserver-xorg-video-cirrus
  xserver-xorg-video-geode xserver-xorg-video-i128 xserver-xorg-video-i740
  xserver-xorg-video-intel xserver-xorg-video-mach64 xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nouveau xserver-xorg-video-nv
  xserver-xorg-video-r128 xserver-xorg-video-s3
  xserver-xorg-video-siliconmotion xserver-xorg-video-trident
  xserver-xorg-video-tseng xsltproc yelp zenity zip
0 upgraded, 496 newly installed, 0 to remove and 2 not upgraded.
2 not fully installed or removed.
Need to get 0B/323MB of archives.
After this operation, 1,241MB of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Could not perform immediate configuration on 'libc6'.Please see man 5 apt.conf under APT::Immediate-Configure for details. (2)
doops@doops:/var/cache/apt/archives$ 


hmmm....not exactly what I had expected to see

---

### Post by coffeecat on 2011-06-14
> **stevovets said:**
> hmmm....not exactly what I had expected to see

Well...

```
doops@doops:~$ cd /var/cache/apt/archives
doops@doops:/var/cache/apt/archives$ sudo dpkg -i --force-depends libc6_2.11.1-0ubuntu7.8_i386.deb
dpkg: parse error, in file '/var/lib/dpkg/status' near line 18945 package 'mawk':
 EOF during value of field `Description' (missing final newline)
```libc6 didn't even start to install, which is why you got the same "E: Could not perform immediate configuration on 'libc6" at the end of the output for apt-get -f install. Something has gone wrong with /var/lib/dpkg/status which I'm fairly sure you have dealt with before.

We are trying to hit a rapidly moving target. Sadly, a failing drive is getting much more likely as a cause of all this.

It's getting late-ish here and my sense quotient is beginning to deteriorate fast. That's the difficulty with working across time-zones. See what wildmanne39 thinks of this latest. I'll check in again in the morning here.

---

### Post by wildmanne39 on 2011-06-14
Hi, the disk utility does not say the drive is failing does it? I am going to do some research and see if I can find an answer.

---

### Post by coffeecat on 2011-06-14
> **wildmanne39 said:**
> Hi, the disk utility does not say the drive is failing does it? 

From what stevovets said it I think it was only a warning, not a "failure imminent" message - perhaps stevovets could confirm this. What concerns me is that there are a fair few re-allocated or pending sectors. Not all pending sectors get reallocated but if data is corrupted because of a failing  sector which is subsequently reallocated then I guess it's possible for the corrupted data to appear on the new sector. This could possibly be why problems keep recurring.

I'm not convinced that the drive is failing - yet - but the data looks concerning enough to keep in mind.

---

### Post by wildmanne39 on 2011-06-14
@coffeecat
Hi, I got the same impression that the drive was not failing at least not yet. Thank you I appreciate the help very much. I think I found a solution, if the instructions are easy enough to follow.
@stevovets
These instructions I found with google and several people have used them to fix this problem, I am just going to paste them here.

"Go to cd /var/cache/apt/archives and very carefully, do a dpkg -i of the problematic package.

I myself have done tonight this:

sudo dpkg -i dpkg_1.15.8.4ubuntu3_amd64.deb libbz2-1.0_1.0.5-4ubuntu1_amd64.deb libselinux1_2.0.94-1_amd64.deb coreutils_8.5-1ubuntu3_amd64.deb libacl1_2.2.49-3_amd64.deb libattr1_1%3a2.4.44-2_amd64.deb

Of course, your package versions should be different, or we'll have found a bug at Ubuntu's side.

Then do the same command with your hopefully small set of .debs with the option --force-depends.

Play alternating with the two commands to get everything installed and configured, and you'll be ready to go.

Now, I've got the same error with another package, did the same again, and now my system is working." Where it says package put the one you are having trouble with in its place.

---

### Post by stevovets on 2011-06-14
> Quote:
                                                                      Originally Posted by **wildmanne39**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10939613#post10939613")                 
                 *Hi, the disk utility does not say the drive is failing does it?*
                                 
From what stevovets said it I think it was only a warning, not a  "failure imminent" message - perhaps stevovets could confirm this.

as far as I can tell, there are no "failure imminent" messages.  SMART status says " Disk has a few bad sectors" and there are those two Warnings in the SMART data.

wildemanne39 - I might need that dumbed down just a little bit, haha...  I'm just kinda confused as to where I put the package that I need in the code and how to write that out.

---

### Post by wildmanne39 on 2011-06-14
> **stevovets said:**
> as far as I can tell, there are no "failure imminent" messages.  SMART status says " Disk has a few bad sectors" and there are those two Warnings in the SMART data.

wildemanne39 - I might need that dumbed down just a little bit, haha...  I'm just kinda confused as to where I put the package that I need in the code and how to write that out.
Hi, the first part is the same that coffeecat told you to do.
```
cd /var/cache/apt/archives
sudo dpkg -i --force-depends libc6_2.11.1-0ubuntu7.8_i386.deb
``` Then the command that says sudo dpkg -i --force-depends use that in the terminal with each of the other packages in the /var/cache/apt/archives folder, you can view the contents by typing ls while you are in that directory. After you run the first command then run this
```
sudo apt-get -f install
``` and run each command on each package then go to the next package in the list.

---

### Post by Rubi1200 on 2011-06-14
If you haven't done so already, backup all your important data now!

If SMART is reporting a few bad sectors that is not a good sign and a total failure is likely not far off.

Finally, if the commands coffeecat and wildmanne39 gave you to force the install of those packages doesn't work, I would attempt a file-system check to try and see if it makes a difference.

From the LiveCD run this command:

 
```
sudo e2fsck -f -y -v /dev/sdXY
```change XY to reflect the actual Ubuntu partition e.g. sda1. Do not run this on the drive but only the partition!

If you need help determining which is the right partition then get on the LiveCD and post the output of > sudo fdisk -l

---

### Post by stevovets on 2011-06-15
wildemann: does that mean im going to have to take every package it lists and run the command?  There's a very extensive list of packages it reads out when I open that folder.

---

### Post by wildmanne39 on 2011-06-15
> **stevovets said:**
> wildemann: does that mean im going to have to take every package it lists and run the command?  There's a very extensive list of packages it reads out when I open that folder.Hi, I know I looked at my list and that is what the instructions say.

---

### Post by jocko on 2011-06-15
Hi,

Your error message indicates that something is wrong with your /var/lib/dpkg/status (I'm guessing from your problems that the file is truncated, making apt think that a lot of already installed packages are not installed).
There *should* be a backup of that file, so you *should* be able to recover like this:

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
```**Edit:** I see you have already tried this, which actually solved one problem (that the original  /var/lib/dpkg/status was corrupted) but replaced it with a new problem...
So it seems you had several corrupted files: Something in  /var/lib/apt/lists/, your original /var/lib/dpkg/status and its backup in /var/lib/dpkg/status-old...
I'm not sure if it's possible to fix a truncated /var/lib/dpkg/status, but maybe all the info is still there except for one faulty line that messes it up? You could post the file here to let someone have a look at it to see if it's possible to fix...

The reason for several corrupted files related to apt/dpkg could simply be that you lost power or the dpkg system crashed during an install, corrupting the files that were being written at that moment, but it could also be that your hard drive is failing (but then you would expect other random files being corrupted as well).

---

### Post by wildmanne39 on 2011-06-15
Hi, Let me know if you tried those commands one at a time on each file. I understand if you do not want too, that seems like a lot of work. The only other thing to do is to reformat and install again, or buy a new hard drive and then reinstall, you can back up your home folder so you do not lose anything that you want to keep.

---

### Post by stevovets on 2011-06-15
when I try to force any of those files it gives me this:

> doops@doops:~$ sudo dpkg -i --force-libcwidget3_0.5.13-1ubuntu1_i386.deb
[sudo] password for doops: 
dpkg: unknown force/refuse option `libcwidget3_0.5.13-1ubuntu1_i386.deb'

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) 
[*].

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
doops@doops:~$ 





I'm starting to think it might just be worth it to reformat.  Though, if my hard drive is beginning to fail, that might be kinda wearing it out, no?  If I were to reformat, what should I look for afterwards to see if the hard drive is still in fair shape?

---

### Post by wildmanne39 on 2011-06-15
> **stevovets said:**
> when I try to force any of those files it gives me this:



I'm starting to think it might just be worth it to reformat.  Though, if my hard drive is beginning to fail, that might be kinda wearing it out, no?  If I were to reformat, what should I look for afterwards to see if the hard drive is still in fair shape?
Hi, you use disk utility again after you have your system back up and running and make sure there are no more bad sectors then the last time you looked. When you reformat it will try to fix the errors if it can, if not it will block them so no more data gets placed there to get corrupted.

---

### Post by coffeecat on 2011-06-16
> **stevovets said:**
> when I try to force any of those files it gives me this:

```
doops@doops:~$ sudo dpkg -i --force-libcwidget3_0.5.13-1ubuntu1_i386.deb
[sudo] password for doops: 
dpkg: unknown force/refuse option `libcwidget3_0.5.13-1ubuntu1_i386.deb'
```

You made a typing error. There should be a space between the --force option and libcwidget, not a hyphen.

However I agree with wildmanne39. I believe the time for re-installation has come. The fact that you have at one time seemingly fixed one dpkg associated file, only for it to resurface as a problem later - as jocko describes - suggests that there is widespread file corruption. 

> **stevovets said:**
> I'm starting to think it might just be worth it to reformat.  Though, if my hard drive is beginning to fail, that might be kinda wearing it out, no?

No more than simply using it. Reformatting merely writes a new filesystem; it doesn't overwrite the whole partition or drive. 

> **stevovets said:**
>  If I were to reformat, what should I look for afterwards to see if the hard drive is still in fair shape?

You need to check the SMART data regularly to see if the bad/reallocated/pending sector counts are increasing.

In summary, my impression: You have spent a very long time trying to fix problems only for them to recur. It will be quicker to re-install. However, the drive may be failing so be prepared for the possibility of a fresh install to fail, and separate backups of personal files is essential.

---

### Post by stevovets on 2011-06-16
jeez, i can't even put the ubuntu iso on my external without getting that input/output error.  I'll have to do it later with my brother's laptop.  I'll keep you guys posted on my progress.  Thanks again for all the help!

---

### Post by wildmanne39 on 2011-06-16
> **stevovets said:**
> jeez, i can't even put the ubuntu iso on my external without getting that input/output error.  I'll have to do it later with my brother's laptop.  I'll keep you guys posted on my progress.  Thanks again for all the help!Hi, yes please let us know how it goes and if you encounter different problems and need help you should start a new thread with a title of that problem but we will cross our finger all will go well.

Coffeecat thank you for help and keeping a check on this situation. I appreciate it very much.

---

### Post by stevovets on 2011-06-17
Hey guys.  Just to let you know, I now have 11.04 running on my desktop.  Seems that in Disk Utility, the Smart DATA still says I have Reallocated Sector Count and Current Pending Sector Count warnings.  However, the OS seems to be running without flaw.

---

### Post by coffeecat on 2011-06-17
Glad to hear you got Ubuntu re-installed OK. Let's hope those sector counts don't go up. But at least you know if they do what the problem is.

How do you like 11.04? Were you able to get the Unity desktop with your hardware? If you did and you're needing some help finding your way around the Unity desktop, there are a couple of links in my sig you might find useful.

Good luck!

---

### Post by wildmanne39 on 2011-06-17
> **stevovets said:**
> Hey guys.  Just to let you know, I now have 11.04 running on my desktop.  Seems that in Disk Utility, the Smart DATA still says I have Reallocated Sector Count and Current Pending Sector Count warnings.  However, the OS seems to be running without flaw.Hi, thats great enjoy ubuntu and keep a check on your bad sectors, also make sure in update manager that you set your settings for update not to include prerelease updates your computer will run better that way.

---

