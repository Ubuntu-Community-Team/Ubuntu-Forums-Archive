---
title: "Installation of packages thru software centre in 10.04"
date: 2010-07-08
forum: General Help
---

### Post by reklan on 2010-07-08
Afternoon,

I have a small problem with install software from the Ubuntu Software centre..

I have tried to install a number of packages that are listed in the "Provided by Ubuntu" Section.

I click "Install" provide password and authenticate, then wait a few seconds.. I then get the following error and the install fails.

"Requires installation of untrusted packages"

" The action would require the installation of packages from unauthenticated source"

I get the chance to click on details, but there is only the one package in there.. the one trying to be installed..

Help!

---

### Post by reklan on 2010-07-09
little bump....

---

### Post by reklan on 2010-07-09
update...  wiped installation and re-installed..  

Software center started to install things correctly...  Update manager then advised that updates were available.. downloaded and installed all the updates.....

after updates.. the message above re-appeared.. 

Anyone??

---

### Post by oldos2er on 2010-07-09
"Requires installation of untrusted packages" means you're missing a gpg authentication key for one or more repositories. 

[https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Authentication%20Tab)

---

### Post by reklan on 2010-07-15
Sorry for delay in replying.. been away from a pc for 5 days..

Many thanks for this.. this sorted it...  although i had the ubuntu ones in.. i removed them and re-added..

problem solved.

---

### Post by jwm93k on 2010-10-07
Hi, Help me understand this. I still l have the problem. Updating didn't help. Removing and adding the checks in the preferences didn't help, and links to tell me I need keys doesn't help when I don't know what a keys I need.
Why is this happening to fresh install. There is quite a rash of these similar issues which means something changed. One listing suggested it started after an update.
Not only do I want to know how to fix it, but what caused it and how do we prevent this from happening again?

---

### Post by oldos2er on 2010-10-07
If you run ```
sudo apt-get update
``` in a terminal, it should tell you which repos are missing keys.

---

### Post by DanPerecky on 2010-10-07
Hi. I am having the same problem with the Software Center - install pkg panel. Pkgs start to install, then just abort. sw updates seem to work fine, but that's it. 

Installed Ubuntu 10.04 yesterday.

running ```
sudo apt-get update
``` may have triggered the Update Manager to start (unless it's just a coincidence).
Terminal response from 'apt-get update' follows:
```
sudo apt-get update
[sudo] password for dan: 
Get:1 http://security.ubuntu.com lucid-security Release.gpg [198B]             
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Get:2 http://us.archive.ubuntu.com lucid Release.gpg [189B]
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Get:3 http://security.ubuntu.com lucid-security Release [38.5kB]
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Get:4 http://us.archive.ubuntu.com lucid-updates Release.gpg [198B]
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release
Get:5 http://us.archive.ubuntu.com lucid-updates Release [44.7kB]            
Get:6 http://security.ubuntu.com lucid-security/main Packages [88.9kB]         
Hit http://us.archive.ubuntu.com lucid/main Packages                           
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages           
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Get:7 http://security.ubuntu.com lucid-security/restricted Packages [14B]
Get:8 http://security.ubuntu.com lucid-security/main Sources [31.8kB]
Get:9 http://us.archive.ubuntu.com lucid-updates/main Packages [326kB]
Get:10 http://security.ubuntu.com lucid-security/restricted Sources [14B]
Get:11 http://security.ubuntu.com lucid-security/universe Packages [43.5kB]
Get:12 http://security.ubuntu.com lucid-security/universe Sources [11.4kB]     
Get:13 http://security.ubuntu.com lucid-security/multiverse Packages [1,994B]  
Get:14 http://security.ubuntu.com lucid-security/multiverse Sources [656B]     
Get:15 http://us.archive.ubuntu.com lucid-updates/restricted Packages [3,240B] 
Get:16 http://us.archive.ubuntu.com lucid-updates/main Sources [127kB]         
Get:17 http://us.archive.ubuntu.com lucid-updates/restricted Sources [1,443B]  
Get:18 http://us.archive.ubuntu.com lucid-updates/universe Packages [131kB]    
Get:19 http://us.archive.ubuntu.com lucid-updates/universe Sources [52.6kB]    
Get:20 http://us.archive.ubuntu.com lucid-updates/multiverse Packages [6,703B] 
Get:21 http://us.archive.ubuntu.com lucid-updates/multiverse Sources [3,242B]  
Fetched 914kB in 11s (81.7kB/s)                                                
Reading package lists... Done
```

I'm wondering if the above update may correct some problem or other.... This computer is required to be rebooted to have the new software loaded....

---

### Post by DanPerecky on 2010-10-07
...rebooted...

[U]installing a calculator program (qalculate-kde) as a test- 
[/U]

[LIST]
[*]The message 'required to install non-trusted pkgs' did not appear.
[*]the two semi-circe green arrows revolved for a while and the 'In Progress(1)' text/label was displayed next to it.
[*]it was 'installing' for 10 minutes. I finally aborted it.
[/LIST]
thank you....

---

### Post by jwm93k on 2010-10-08
@oldos2er:
So I run Cmd-Line update and look for lines that didn't work. Then what?

---

### Post by DanPerecky on 2010-10-08
[SIZE=2]I don't know if this will help... my problem was solved by reviewing the documentation on the page given by the link in the above post for the **Synaptic Package Manager**.... accessible via: System | Administration | Synaptic[/SIZE]  :)
-----------------------------------------------------------------------------------------------------
F.Y.I....
It looked like the Ubuntu SW Center app did actually download the qalculate-kde calculator app (twice- two entries in Accessories), but it froze when attempting to download the Wine pkg. Perhaps Ubuntu SW Center it is not ready for prime time yet? :(

---

### Post by oldos2er on 2010-10-10
> **jwm93k said:**
> @oldos2er:
So I run Cmd-Line update and look for lines that didn't work. Then what?

Visit the link in post #4. If you need more help, just ask.

---

