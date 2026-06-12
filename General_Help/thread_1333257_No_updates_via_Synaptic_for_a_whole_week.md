---
title: "No updates via Synaptic for a whole week?"
date: 2009-11-21
forum: General Help
---

### Post by CoolBreeze47 on 2009-11-21
Hi everyone

First of all, I am using Ubuntu v9.10 (Karmic Koala).

For the last 7 days there have been no updates whatsoever via the Synaptic package manager. This seems highly unusual given the fact that in the last 7-8 years I've used various Linux distros there have always been at least a few updates every couple of days - especially with new releases like Ubuntu 9.10.

Of course, I'm doing everything properly, I've not changed anything, the settings in Synaptic have not been changed, I'm using a "vanilla" install of Ubuntu 9.10, I type my root password in even after Synaptic loads...still nothing. There doesn't seem to be any glitches in Synaptic as everything appears to load and search for updates just fine.

Am I missing something or are we just experiencing a particularly slow update cycle?. Surely after a whole week there must be at least a few updates, bug fixes, security updates and the like...no?.

- Thanks, CoolBreeze

---

### Post by drs305 on 2009-11-21
First, welcome to the Ubuntu forums. Unless you've changed names recently I see this is your first post. ;-)

You say you haven't changed any settings, but you might want to review what they are set to via System, Administration, Update Manager. Click the "Settings" box in the lower left part, then select "Updates" (you can also do this via Synaptic). The first tab will show whether you are set to get only security updates or have other options enabled. It will also show how often the system checks for updates.

You could also check the dpkg log via System, Admin, Log File Viewer to see if anything has been installed recently if you have things set up to install automatically.
You can run this to get a quick summary of recent dpkg activity:
```

grep " installed" /var/log/dpkg.log | tail

```

---

### Post by mechro on 2009-11-21
I don't find that unusual. I'm running Jaunty so I'm not experiencing Karmic updatedness...

What is showing in **System > Admin... > Update Manager**?

---

### Post by mechro on 2009-11-21
> **drs305 said:**
> First, welcome to the Ubuntu forums. Unless you've changed names recently I see this is your first post. ;-)


Yeah!, that CoolBreeze46 chappy was a right pain in the... ;)

Welcome CoolBreeze47 :D

---

### Post by milenixloerdi on 2009-11-21
Hi,  I did delete two of the four software update sources and now I only have those two:  [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner (Source Code)  Can soemone please post the other two sources so that I can add them  Thanks a lot

---

### Post by drs305 on 2009-11-21
> **milenixloerdi said:**
> Hi,  I did delete two of the four software update sources and now I only have those two:  [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner (Source Code)  Can soemone please post the other two sources so that I can add them  Thanks a lot

Pick the ones you need. The first are the four (2 combined in first line) from the Ubuntu Software tab. The next are from the Updates tab. The last are security repositories:
> 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-updates multiverse


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) karmic-security multiverse


---

### Post by milenixloerdi on 2009-11-21
Thanks a lot drs305! How do I know which one I need? Can I not** add them all **under the "Other software" tab? It asked me once for authentication keys - will  need any of those for those sites?

I'd rather have as many update sites available as possible - will it be ok to add all of those you listed?

Thanks

---

### Post by drs305 on 2009-11-21
> **milenixloerdi said:**
> Thanks a lot drs305! How do I know which one I need? Can I not** add them all **under the "Other software" tab? It asked me once for authentication keys - will  need any of those for those sites?

I'd rather have as many update sites available as possible - will it be ok to add all of those you listed?

Thanks

Those are more or less the 'standard' repositories. They do not include the 'source' repositories, which generally are not needed.

You can add them by editing sources.list and they will automatically be placed in the correct tab and ticked in the proper boxes in Synaptic/Software Sources.

```

gksu gedit /etc/apt/sources.list

```
If you have third party sources such as 'partner' and 'medibuntu' you would want to keep those in the list as well. So the final list would include the ones I posted, plus your 'partner' ones and any third party ones showing up in your sources.list.

You can also build a sources.list from scratch via this site:
[http://repogen.simplylinux.ch/]("http://repogen.simplylinux.ch/")

---

### Post by milenixloerdi on 2009-11-21
Thanks again. One more thing - as I added all that you listed above, none of them appeared under my "Other Software" Tab. I copied/pasted them exactly. Are they still "in" somewhere, or I've done something wrong?

Yes, I have the medibuntu ones listed there, but anytime I click on them and reload, it says there is no "authentication" key....

---

### Post by drs305 on 2009-11-21
> **milenixloerdi said:**
> Thanks again. One more thing - as I added all that you listed above, none of them appeared under my "Other Software" Tab. I copied/pasted them exactly. Are they still "in" somewhere, or I've done something wrong?

Yes, I have the medibuntu ones listed there, but anytime I click on them and reload, it says there is no "authentication" key....

Except for 'partner' repositories, they will appear under the Ubuntu Software and Updates tabs, since these are 'core' repositories and not 3rd party ones.

To add the Medibuntu repository and automatcially add the key, run this command. It's found at [https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")
```

sudo wget http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update

```

You can learn about repositories here:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by milenixloerdi on 2009-11-21
thank you - it worked perfect :) Thanks for the links, too!

---

### Post by CoolBreeze47 on 2009-11-21
First, thank you for the information.

Secondly, let me clear something up right away. I woke up this morning and decided to open an account here because of the issue I described in my post. Prior to that post, I have not used this forum or even visited here for over a year (perhaps longer). The name I chose was completely random. I was never "CoolBreeze46" on this forum or any other forum. Frankly, I only chose the name because I could not think of anything else and it simply popped into my head at the time. I am 47 years of age - thus the number "47".

Rather than having to defend myself against whatever this other person did or did not do and being tagged or labeled with some sort of stigma, I think it best that I find another another forum to frequent. Since the two names are so strikingly similar I don't expect anyone here to believe me and to be honest, I would not believe me either. Apparently "CoolBreeze" was a poor choice of names to use.

This is probably the first time I have ever joined a forum and had to immediately begin defending myself - and against something for which I am completely innocent.

Wow.

---

### Post by mechro on 2009-11-21
Er... many, many apologies CoolBreeze. I was only joking. :oops::oops::oops:

There is no CoolBreeze46, it's just a figment of my silly imagination.

Again, apologies.

---

### Post by CoolBreeze47 on 2009-11-21
> **mechro said:**
> Er... many, many apologies CoolBreeze. I was only joking. :oops::oops::oops:

I thought that perhaps someone here had at one time used the name "CoolBreeze46" and created a stir because that's what was implied. I did not want to feel stigmatized or labeled right from the start and so I thought it best that I find another forum to use. I have no hard feeling at all toward anyone here and do not wish to cause any problems. Your not the only person who evoked the name "CoolBreeze46" so somehow I doubt this was simply a "joke". Anyway, always nice to get a warm welcome.

ATTN: Moderators, please close my account.

---

### Post by drs305 on 2009-11-21
Edited: I see mechro has already responded.

CoolBreeze47,

Sometimes humor isn't reflected in a post. I read it and thought it was pretty funny, but I have that kind of humor. 

You will find the Ubuntu forums at the top of the list when it comes to its supportive nature and genuinely positive attitudes. Sure there are the occasional posts that don't conform to the Ubuntu Code of Conduct but this place has a very positive atmosphere - especially considering many of the people coming here are experiencing problems.

Please don't let your initial reaction create a lasting impression of the Ubuntu forums.

Oh, and yeah, one more thing.


That CoolBreeze46 guy really was an ...  ;-)
j/k

---

### Post by CoolBreeze47 on 2009-11-21
How do I delete this?

---

### Post by CoolBreeze47 on 2009-11-21
Well, guess what?... I am the much feared "CoolBreeze46"!. I'm the monster who hid under your beds as children and the evil entity your parent warned you about. Soon I will take over the entire planet and implant chips in the brains of all humans so I can make compliant zombies out of them. Soon my plans will be complete and I can rule the world with an iron fist!. Muuahaahaahaa!! :twisted:

And you thought I was just here to ask a few innocent questions ;)

---

### Post by CoolBreeze47 on 2009-11-21
Everything that should be checked is checked and yet still no updates for the past week. All of the defaults plus restricted and proposed.

---

### Post by wbee on 2009-11-21
Cool Breeze(You don't look that old.:-)),

Yes,my KK 32bit,HAS had updates just two days ago.

I had a similar problem,perhaps this might help:

System>Administration>Synaptic Manager>Settings>Repositories>and then look at the screen.

"Ubuntu Software" at default has the first four items checked,*and what happened to me,the cd-rom  button was checked. If it is,uncheck it. Then "reload" and check your updates.

In "Other Software",the first box should be checked.

In "updates",the first two buttons should be checked.  On the fifth line,*if you want daily updates,make sure "daily" is selected from the menu.

I hope this solves your issue and if it does not,that someone comes along soon to resolve it.

---

### Post by mechro on 2009-11-21
In **Update Manager** settings, is **Check For Updates** set to **Daily**?

---

### Post by drs305 on 2009-11-21
> **CoolBreeze47 said:**
> Everything that should be checked is checked and yet still no updates for the past week. All of the defaults plus restricted and proposed.

Have you tried changing to a different server and refreshing the list, especially if you aren't using one of the main ones? And I assume you have tried to manually invoke an update by clicking "Check" in Update Manager?

How about running this and see what messages you get:
```

sudo apt-get update && sudo apt-get upgrade

```

---

### Post by CoolBreeze47 on 2009-11-21
No updates/upgrades and it doesn't look like I'm going to get any either...

saltydog@saltydog-desktop:~$ sudo apt-get update
[sudo] password for saltydog: 
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_US              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US          
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US                 
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed Release.gpg         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/restricted Translation-en_US
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release.gpg              
Ign [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/games Translation-en_US  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources   
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb Release                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://archive.getdeb.net](http://archive.getdeb.net) karmic-getdeb/games Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-proposed/universe Packages
Reading package lists... Done

...and...

saltydog@saltydog-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
saltydog@saltydog-desktop:~$

---

