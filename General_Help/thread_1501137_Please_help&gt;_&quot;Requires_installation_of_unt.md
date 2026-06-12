---
title: "Please help&gt; &quot;Requires installation of untrusted packages&quot;"
date: 2010-06-03
forum: General Help
---

### Post by maizuddin35 on 2010-06-03
Hello linuxers.  I want to install software tools from the software sources, but it ended up like this:
[IMG]http://yfrog.com/eascreenshotykp[/IMG]
is there anyone can help me out with this one?
please.

regards
adib.

---

### Post by maizuddin35 on 2010-06-04
is there anyone.?
bump

---

### Post by derekeverett on 2010-06-04
Try installing it from Synaptic Package Manager or at the command line with sudo.

That is.. if you still want it.

---

### Post by oldos2er on 2010-06-04
Can you run ```
sudo apt-get update
``` in a terminal, and post the output here?

---

### Post by pike747 on 2010-06-05
I did not ask the question but this is what happened when I did that. 

Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [189B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Get:2 [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg [189B]          
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg [189B]          
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [38.5kB]     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg                 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                             
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release [57.2kB]                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages [179kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [22.9kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [14B]    
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [8,520B]        
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [14B]      
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [6,183B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [1,297B]     
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [14B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [14B]
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages [2,096B]
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources [70.8kB]
Get:17 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources [737B]
Get:18 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages [36.1kB]
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources [9,566B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages [632B]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources [14B]
Fetched 377kB in 2s (182kB/s)                           
Reading package lists... Done


That seems to have fixed the problem for me thank you very much!
I did deduce that it had something to do with updates but they did not fully update from the GUI
The command line rules, yeah heh heh it Rules!

---

### Post by maizuddin35 on 2010-06-07
the same thing happen when i run apt-get update.

maybe i need to install it via the synaptic .hmm. is there any other ways?

---

### Post by PerfectReign on 2010-06-14
I just got this same thing...


[IMG]http://www.perfectreign.com/stuff/2010/authenticate.png[/IMG]


I try not to downgrade to the terminal but using Synaptic worked.

Why does this happen?

---

### Post by maizuddin35 on 2010-06-16
I do not know how this is happen and why this thing is happening. But maybe something is wrong in the manager itself I think, because I have problem with some application that cant be run properly such as the aptoncd , awn manager and caffeine .Do we need to reinstall ubuntu back?

---

### Post by oldos2er on 2010-06-16
You're missing GPG keys for one or more repositories. [https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab)

---

### Post by K.J. on 2010-06-16
> **oldos2er said:**
> You're missing GPG keys for one or more repositories. [https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab)

oldos2er is correct, you're missing the gpg keys. Although if you use synaptic or apt-get to install you can install without adding them.

---

### Post by luisvidal on 2010-08-30
This was very helpful, friends. Thanks

---

### Post by kishorr on 2010-09-10
> **oldos2er said:**
> Can you run ```
sudo apt-get update
``` in a terminal, and post the output here?


this gave me the solution! thanks!!!!!!

---

### Post by mamece2 on 2010-09-25
> **oldos2er said:**
> Can you run ```
sudo apt-get update
``` in a terminal, and post the output here?

this worked for me. i wish i know why :(

---

### Post by jwm93k on 2010-09-27
Hi, I just loaded from an Ubuntu DVD, fresh with the latest 10.04.1 extend version from the magazine. Load went well. I fought a bit getting a mount to work correctly and trying to connect to a Samba share on a Ubuntu system. I Figured the samba worked well an easily with Win XP, it should connect with Ubuntu better, wrong. I can see the share but can not copy any thing to it, no permissions. Any way I was just trying to install some games and I got the [COLOR="Red"]_"Requires installation of Untrusted Packages"_[/COLOR] message.  I did not have this with the initial load of 10.04 on my netbook and other PC. I wonder is this is related to the newer version with most of the updates? I find it rather annoying a fresh install can not do this normal thing that I could do before. It does not give me a good feeling at all. Being the the 10.04.1 and the magazine came out lately,(an if it is related) this issue could be a trend. I still don't know what the real fix is. I have read many posts and see different solution suggestion success. I believe it when I see it work. First I will run update and then try again. Maybe Ubuntu has a fix out there for this......
I like and prefer linux, but things like this don't help.
I would like to know why this happens. What was left out of the install, or turned off remotely or what server when down to cause this to happen.

---

### Post by jwm93k on 2010-09-27
Well, the update it self did not fix the problem alone. Then I tried the Software Center, Edit, Software Sources, Tab-Other software. Note the selected items. I unselected all and closed. Repeat to tab and reselect items again and try to down load something. I was able to download, however I get intermittent messages about failing to sync. So it is not 100% but it is better.

---

### Post by jwm93k on 2010-09-27
Hi, Disregard last entry, the error is back "Requires installation of untrusted packages". Weird it worked for one program last night and now it is back. No fix yet....

---

### Post by jwm93k on 2010-09-28
Tried the command line sugo apt-get update... No Joy... I got this on my next attempt at the Software Center: Failed to download repository information: check your internet connection::
[http://packages.medibuntu.org/dists/lucid/Release.gpg](http://packages.medibuntu.org/dists/lucid/Release.gpg)
[http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)
My internet connection is good.
Any Ideas?

---

### Post by jwm93k on 2010-10-02
Hi, My theory about the latest 10.04 disk causing this is blown. I just used a original 10.04 disk on a new install and got the same thing. I'm starting to think its not the systems it is the servers.

---

### Post by maizuddin35 on 2010-10-03
i think it just the server and maybe its about your resporitory stuffs?

---

