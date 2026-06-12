---
title: "Constantly have to run apt-get update"
date: 2012-03-02
forum: General Help
---

### Post by gordonaw on 2012-03-02
(Disclaimer: I apologize in advanced if this is posted elsewhere. I searched and couldn't find any similar situations)
 
OS Ubuntu 11.10
Hardware Toshiba Laptop
Network Connection Casual Wireless
 
Whenever I try to install a new package, either with apt-get install or with the Ubuntu Software Center, I am unable to do so until I run an apt-get update command. Apt-get install will tell me the package cannot be authenticated and asks if I want to procedd without verification. If I try to install through the Software Center it prompts me for credentials and then tells me it can't connect and to check my internet connection. Once I run an apt-get update (which btw runs without errors) both of the previous methods start working fine.
 
I've tried apt-get clean. I've tried clearing out the cached repository info and reloading with an apt-get update. I never get any errors during update, and the install methods only seem to work AFTER I've done the update.
 
Must I run an apt-get update every time I want to install new hardware? I ask because I've never seen it in print that apt-get update is requried before apt-get install. However I have seen people mention that they will run a command like apt-get update && apt-get install (package).
 
I'm fairly new to linux and Ubuntu so if anyone can help I'd be very appreciative.
 
Thanks!
 
Andrew

---

### Post by dcstar on 2012-03-03
> **gordonaw said:**
> 
........
I'm fairly new to linux and Ubuntu so if anyone can help I'd be very appreciative.


[LIST=1]
[*]You should not **ever** need to use the command line to do these things, people have spent years providing GUI tools do do it.
[*]What else has been done at command line level that has broken this function that seems to work well for everyone else?
[/LIST]

---

### Post by gordonaw on 2012-03-03
Even when I use the GUI it fails out with an error message telling me it can't connect and to check my internet connection. However I haven't tried using synaptic at this point so I could try that and report back.

---

### Post by snowpine on 2012-03-03
You must run **apt-get update** to refresh your package list before you install an app, this is normal. Software Center does this "behind the scenes" for you. :)

---

### Post by matt_symes on 2012-03-03
Hi

> Apt-get install will tell me the package cannot be authenticated and asks if I want to procedd without verification. If I try to install through the Software Center it prompts me for credentials and then tells me it can't connect and to check my internet connection.

It sounds like you may be missing a GPG package key.

dcstart is correct when he states you do not need to use the terminal to install software. It's very easy to cause problems with the package management system. It's also too easy to follow an outdated or even just plain wrong tutorial on the internet.

I think all new users to Ubuntu should the GUI when ever possible.

That being said, the terminal is a great way to get diagnostic information into a forum so we'll use it.

Open a terminal and type

```
sudo apt-get update
```

Copy and paste the results back here between code tags like this

[noparse]```
results
```[/noparse]

to get formatting like this.

```
results
```

Kind regards

---

### Post by gordonaw on 2012-03-05
Thank you everyone for your help. Below I've pasted the result of an "apt-get update" after I can't install new packages in Ubuntu Software Center or via the command line. As per usual for me as soon as I've updated I can successfully install new software. Also I noticed as soon as I ran the apt-get update my Update Manager immediately notified me of new updates. One last question in the results below what does HIT vs GET vs IGN signify? Thanks again! 

```
Ign http://download.virtualbox.org oneiric InRelease
Ign http://download.virtualbox.org natty InRelease
Ign http://download.virtualbox.org maverick InRelease
Ign http://download.virtualbox.org lucid InRelease
Ign http://security.ubuntu.com oneiric-security InRelease
Ign http://ppa.launchpad.net natty InRelease
Ign http://download.virtualbox.org karmic InRelease
Ign http://us.archive.ubuntu.com oneiric InRelease
Ign http://archive.canonical.com oneiric InRelease
Ign http://download.virtualbox.org hardy InRelease
Hit http://security.ubuntu.com oneiric-security Release.gpg
Ign http://download.virtualbox.org squeeze InRelease
Hit http://ppa.launchpad.net natty Release.gpg
Ign http://download.virtualbox.org lenny InRelease
Ign http://us.archive.ubuntu.com oneiric-updates InRelease
Get:1 http://archive.canonical.com oneiric Release.gpg [198 B]
Hit http://download.virtualbox.org oneiric Release.gpg
Hit http://security.ubuntu.com oneiric-security Release
Hit http://download.virtualbox.org natty Release.gpg
Hit http://ppa.launchpad.net natty Release
Hit http://download.virtualbox.org maverick Release.gpg
Ign http://us.archive.ubuntu.com oneiric-backports InRelease
Get:2 http://archive.canonical.com oneiric Release [5,922 B]
Hit http://download.virtualbox.org lucid Release.gpg
Hit http://security.ubuntu.com oneiric-security/main Sources
Hit http://download.virtualbox.org karmic Release.gpg
Hit http://ppa.launchpad.net natty/main Sources
Hit http://us.archive.ubuntu.com oneiric Release.gpg
Hit http://download.virtualbox.org hardy Release.gpg
Get:3 http://archive.canonical.com oneiric/partner i386 Packages [3,935 B]
Hit http://download.virtualbox.org squeeze Release.gpg
Hit http://security.ubuntu.com oneiric-security/restricted Sources
Hit http://download.virtualbox.org lenny Release.gpg
Hit http://ppa.launchpad.net natty/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates Release.gpg
Hit http://download.virtualbox.org oneiric Release
Hit http://download.virtualbox.org natty Release
Ign http://archive.canonical.com oneiric/partner TranslationIndex
Hit http://security.ubuntu.com oneiric-security/universe Sources
Hit http://download.virtualbox.org maverick Release
Ign http://ppa.launchpad.net natty/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports Release.gpg
Hit http://download.virtualbox.org lucid Release
Hit http://security.ubuntu.com oneiric-security/multiverse Sources
Hit http://download.virtualbox.org karmic Release
Hit http://us.archive.ubuntu.com oneiric Release
Hit http://download.virtualbox.org hardy Release
Hit http://download.virtualbox.org squeeze Release
Hit http://security.ubuntu.com oneiric-security/main i386 Packages
Hit http://download.virtualbox.org lenny Release
Hit http://download.virtualbox.org oneiric/contrib i386 Packages
Ign http://download.virtualbox.org oneiric/contrib TranslationIndex
Hit http://security.ubuntu.com oneiric-security/restricted i386 Packages
Hit http://download.virtualbox.org natty/contrib i386 Packages
Ign http://download.virtualbox.org natty/contrib TranslationIndex
Hit http://download.virtualbox.org maverick/contrib i386 Packages
Hit http://security.ubuntu.com oneiric-security/universe i386 Packages
Hit http://download.virtualbox.org maverick/non-free i386 Packages
Ign http://download.virtualbox.org maverick/contrib TranslationIndex
Hit http://security.ubuntu.com oneiric-security/multiverse i386 Packages
Ign http://download.virtualbox.org maverick/non-free TranslationIndex
Hit http://download.virtualbox.org lucid/contrib i386 Packages
Hit http://download.virtualbox.org lucid/non-free i386 Packages
Hit http://security.ubuntu.com oneiric-security/main TranslationIndex
Ign http://download.virtualbox.org lucid/contrib TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates Release
Ign http://download.virtualbox.org lucid/non-free TranslationIndex
Hit http://download.virtualbox.org karmic/contrib i386 Packages
Hit http://security.ubuntu.com oneiric-security/multiverse TranslationIndex
Hit http://download.virtualbox.org karmic/non-free i386 Packages
Ign http://download.virtualbox.org karmic/contrib TranslationIndex
Hit http://security.ubuntu.com oneiric-security/restricted TranslationIndex
Ign http://download.virtualbox.org karmic/non-free TranslationIndex
Hit http://download.virtualbox.org hardy/contrib i386 Packages
Hit http://download.virtualbox.org hardy/non-free i386 Packages
Hit http://security.ubuntu.com oneiric-security/universe TranslationIndex
Ign http://archive.canonical.com oneiric/partner Translation-en_US
Ign http://download.virtualbox.org hardy/contrib TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports Release
Ign http://download.virtualbox.org hardy/non-free TranslationIndex
Hit http://download.virtualbox.org squeeze/contrib i386 Packages
Ign http://ppa.launchpad.net natty/main Translation-en_US
Hit http://security.ubuntu.com oneiric-security/main Translation-en
Ign http://archive.canonical.com oneiric/partner Translation-en
Hit http://download.virtualbox.org squeeze/non-free i386 Packages
Ign http://download.virtualbox.org squeeze/contrib TranslationIndex
Ign http://download.virtualbox.org squeeze/non-free TranslationIndex
Hit http://security.ubuntu.com oneiric-security/multiverse Translation-en
Ign http://ppa.launchpad.net natty/main Translation-en
Hit http://download.virtualbox.org lenny/contrib i386 Packages
Hit http://us.archive.ubuntu.com oneiric/main Sources
Hit http://download.virtualbox.org lenny/non-free i386 Packages
Hit http://security.ubuntu.com oneiric-security/restricted Translation-en
Ign http://download.virtualbox.org lenny/contrib TranslationIndex
Ign http://download.virtualbox.org lenny/non-free TranslationIndex
Hit http://security.ubuntu.com oneiric-security/universe Translation-en
Ign http://extras.ubuntu.com oneiric InRelease
Hit http://extras.ubuntu.com oneiric Release.gpg
Hit http://us.archive.ubuntu.com oneiric/restricted Sources
Hit http://extras.ubuntu.com oneiric Release
Hit http://us.archive.ubuntu.com oneiric/universe Sources
Hit http://extras.ubuntu.com oneiric/main Sources
Hit http://extras.ubuntu.com oneiric/main i386 Packages
Ign http://extras.ubuntu.com oneiric/main TranslationIndex
Ign http://extras.ubuntu.com oneiric/main Translation-en_US
Ign http://extras.ubuntu.com oneiric/main Translation-en
Ign http://download.virtualbox.org oneiric/contrib Translation-en_US
Ign http://download.virtualbox.org oneiric/contrib Translation-en
Ign http://download.virtualbox.org natty/contrib Translation-en_US
Ign http://download.virtualbox.org natty/contrib Translation-en
Ign http://download.virtualbox.org maverick/contrib Translation-en_US
Ign http://download.virtualbox.org maverick/contrib Translation-en
Ign http://download.virtualbox.org maverick/non-free Translation-en_US
Ign http://download.virtualbox.org maverick/non-free Translation-en
Ign http://download.virtualbox.org lucid/contrib Translation-en_US
Ign http://download.virtualbox.org lucid/contrib Translation-en
Ign http://download.virtualbox.org lucid/non-free Translation-en_US
Ign http://download.virtualbox.org lucid/non-free Translation-en
Ign http://download.virtualbox.org karmic/contrib Translation-en_US
Ign http://download.virtualbox.org karmic/contrib Translation-en
Ign http://download.virtualbox.org karmic/non-free Translation-en_US
Ign http://download.virtualbox.org karmic/non-free Translation-en
Ign http://download.virtualbox.org hardy/contrib Translation-en_US
Ign http://download.virtualbox.org hardy/contrib Translation-en
Ign http://download.virtualbox.org hardy/non-free Translation-en_US
Ign http://download.virtualbox.org hardy/non-free Translation-en
Ign http://download.virtualbox.org squeeze/contrib Translation-en_US
Ign http://download.virtualbox.org squeeze/contrib Translation-en
Ign http://download.virtualbox.org squeeze/non-free Translation-en_US
Ign http://download.virtualbox.org squeeze/non-free Translation-en
Ign http://download.virtualbox.org lenny/contrib Translation-en_US
Ign http://download.virtualbox.org lenny/contrib Translation-en
Ign http://download.virtualbox.org lenny/non-free Translation-en_US
Ign http://download.virtualbox.org lenny/non-free Translation-en
Hit http://us.archive.ubuntu.com oneiric/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/main Sources
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Sources
Hit http://us.archive.ubuntu.com oneiric-updates/universe Sources
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric-updates/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/main Sources
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Sources
Hit http://us.archive.ubuntu.com oneiric-backports/universe Sources
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Sources
Hit http://us.archive.ubuntu.com oneiric-backports/main i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com oneiric-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com oneiric-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com oneiric/main Translation-en
Hit http://us.archive.ubuntu.com oneiric/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-updates/universe Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/main Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com oneiric-backports/universe Translation-en
Fetched 10.1 kB in 1min 8s (146 B/s)
Reading package lists...
```

---

### Post by snowpine on 2012-03-05
Your software sources are a mess, you are pulling in repos for several different Ubuntu and Debian releases. It is quite likely your system is irreparably broken, however, you could try creating a new sources.list and repairing your system that way. Start with just the official Ubuntu repos for your correct release, and build up from there.

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by matt_symes on 2012-03-05
Hi

> One last question in the results below what does HIT vs GET vs IGN signify?

As snowpine is handling your main problem very well, i'll deal with this question.

HIT - means it needs to update the package information system for the repository.
IGN - means ingore. It does not need to update the package information on your system as nothing has changed between the server and your local PC.
GET - means it's getting the package information for that repository.

When you update your system using apt-get update, it will only get updates for a repository when the package state on your system is different than what's on the server (i.e something's changed on the server and it has new or updated packages)

This is done to save bandwidth. It checks to see if the packages have changes by checking to see hash value for the packages information on your local machine are different than on the server.

The hash it downloads from the server each time you update are a lot smaller than downloading the entire package status information.

I'm pretty sure this is correct. Someone will correct me if i am wrong.

Kind regards

---

### Post by gordonaw on 2012-03-05
I've cleaned up my sources.list and removed all the VirtualBox references to older Ubuntu and Debian distros. The Software Center seems to work better and remains stable over a reboot and a hibernate. If it does come back is there a method I can use (other than an OS reinstall) to reset the package manager?
 
Again thank you all for your assistance!

---

### Post by gordonaw on 2012-03-06
Update: It's been 24 hours and everything still seems to be running great. So why would the Virtualbox distros for older Ubuntu distros and some Debian distros have made the update manager go all haywire? 
 
Thanks everyone for all your help!

---

