---
title: "Broken Packages"
date: 2011-08-02
forum: General Help
---

### Post by theozzlives on 2011-08-02
I installed the crappy Amarok and decided I wanted Amarok14. I installed 1.4 over the crappy one, then tried to remove the old one. I wound up not getting either and having broken packages. I tried Synaptic and also the following:
```
sudo dpkg --configure -a
```
```
sudo apt-get -f install
```
```
sudo apt-get remove amarok
```
```
sudo apt-get install amarok14
```

to no avail, I hope I didn't break my system. Help please!

Oh yeah! I also tried:
```
sudo apt-get autoremove
```

---

### Post by JC Cheloven on 2011-08-02
Maybe this:
```
sudo apt-get remove --purge amarok
sudo apt-get remove --purge amarok14
sudo apt-get autoremove
sudo apt-get install amarok14
sudo dpkg-reconfigure amarok14
```
Even better, instead of autoremove, install gtkorphan and run it. It usually does a better job.

---

### Post by theozzlives on 2011-08-02
> **JC Cheloven said:**
> Maybe this:
```
sudo apt-get remove --purge amarok
sudo apt-get remove --purge amarok14
sudo apt-get autoremove
sudo apt-get install amarok14
sudo dpkg-reconfigure amarok14
```
Even better, instead of autoremove, install gtkorphan and run it. It usually does a better job.

It won't work, I can't install anything. I think I broke my system. apt just tells me to run -f install but that don't fix anything.

---

### Post by JC Cheloven on 2011-08-04
A shot in the dark: after deleting all this, does updating your sources helps at all?:
```
sudo apt-get update
```
Quite dumb, but... who knows.

Also, try open synaptic, and go to edit -> repair broken packages
It may actually repair some broken dependencies.

---

### Post by wildmanne39 on 2011-08-05
Hi, post the outcome of 
```
sudo apt-get update
```
so we can see the error messages.
Thank you

---

### Post by theozzlives on 2011-08-05
> **wildmanne39 said:**
> Hi, post the outcome of 
```
sudo apt-get update
```
so we can see the error messages.
Thank you

it's a broken package. Synaptic reports:
> You have 1 broken package on your system!

Use the "Broken" filter to locate it.
Nonetheless I'll posy  it just to humor you.

---

### Post by theozzlives on 2011-08-05
```
Hit http://ppa.launchpad.net lucid Release.gpg
Ign http://ppa.launchpad.net/bogdanb/amarok14/ubuntu/ lucid/main Translation-en_US
Ign http://ppa.launchpad.net lucid Release.gpg                      
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://ppa.launchpad.net/ozzie/amarok14/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release     
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg           
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release                       
Ign http://ppa.launchpad.net lucid Release                                     
Hit http://us.archive.ubuntu.com lucid-updates Release               
Hit http://ppa.launchpad.net lucid/main Packages                     
Hit http://security.ubuntu.com lucid-security/main Packages          
Ign http://ppa.launchpad.net lucid/main Packages                     
Hit http://us.archive.ubuntu.com lucid/main Packages                 
Hit http://us.archive.ubuntu.com lucid/restricted Packages           
Hit http://us.archive.ubuntu.com lucid/main Sources                  
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages      
Hit http://security.ubuntu.com lucid-security/universe Sources       
Hit http://security.ubuntu.com lucid-security/multiverse Packages    
Ign http://ppa.launchpad.net lucid/main Packages                     
Hit http://us.archive.ubuntu.com lucid/multiverse Packages           
Hit http://us.archive.ubuntu.com lucid/multiverse Sources            
Hit http://security.ubuntu.com lucid-security/multiverse Sources     
Hit http://us.archive.ubuntu.com lucid-updates/main Packages         
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Err http://ppa.launchpad.net lucid/main Packages
  404  Not Found
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
W: Failed to fetch http://ppa.launchpad.net/ozzie/amarok14/ubuntu/dists/lucid/main/binary-i386/Packages.gz  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
ozzie@ozzie-netbook:~$ 

```

---

### Post by wildmanne39 on 2011-08-05
Hi, that file is not on the server, it has been removed or the name is in correct.

Open synaptic,click on settings,repositories,other software then uncheck or remove that ppa then close synaptic. 

Then run
```
sudo apt-get update
```
and you should be able to use synaptic again to install software.

---

### Post by theozzlives on 2011-08-05
> **wildmanne39 said:**
> Hi, that file is not on the server, it has been removed or the name is in correct.

Open synaptic,click on settings,repositories,other software then uncheck or remove that ppa then close synaptic. 

Then run
```
sudo apt-get update
```
and you should be able to use synaptic again to install software.

I uncecked the ppa and update is fine, but I stall have a broken package!

---

### Post by wildmanne39 on 2011-08-05
Hi, run these commands please:
```
sudo apt-get install -f install
```
```
sudo apt-get update && sudo apt-get upgrade
```
let us know if your still get errors.
Thank you

---

### Post by theozzlives on 2011-08-07
```
ozzie@ozzie-netbook:~$ sudo apt-get update && sudo apt-get upgrade
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net/tualatrix/ppa/ubuntu/ karmic/main Translation-en_US
Hit http://ppa.launchpad.net lucid Release.gpg
Hit http://security.ubuntu.com lucid-security Release.gpg
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg                   
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://ppa.launchpad.net/bogdanb/amarok14/ubuntu/ lucid/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release    
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release                       
Hit http://ppa.launchpad.net lucid Release                                     
Hit http://security.ubuntu.com lucid-security/main Packages          
Hit http://us.archive.ubuntu.com lucid-updates Release               
Hit http://ppa.launchpad.net karmic/main Packages                    
Hit http://security.ubuntu.com lucid-security/restricted Packages    
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://security.ubuntu.com lucid-security/universe Sources       
Hit http://security.ubuntu.com lucid-security/multiverse Packages    
Hit http://us.archive.ubuntu.com lucid/main Packages                 
Hit http://us.archive.ubuntu.com lucid/restricted Packages           
Hit http://us.archive.ubuntu.com lucid/main Sources                  
Hit http://us.archive.ubuntu.com lucid/restricted Sources            
Hit http://us.archive.ubuntu.com lucid/universe Packages             
Hit http://us.archive.ubuntu.com lucid/universe Sources              
Hit http://ppa.launchpad.net lucid/main Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  amarok14-engine-xine: Depends: amarok14 but it is not installed
                        Recommends: amarok14 (= 2:1.4.10-0ubuntu3~ppa5) but it is not installed
E: Unmet dependencies. Try using -f.

```

---

### Post by wildmanne39 on 2011-08-07
Hi, now that syanptic is working again rerun the commands in post #2.
Thank you

---

### Post by theozzlives on 2011-08-08
I keep getting:
> E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by govindsri on 2011-08-08
[SIZE=3]i installed timidity for sand maker but now it is showing broken packages.i also tried 
sudo apt-get -f install
sudo apt-get autoremove
sudo apt-get --purge
[COLOR=RoyalBlue]
[/COLOR][COLOR=RoyalBlue]please help me !
[/COLOR][/SIZE]

---

### Post by mc4man on 2011-08-08
When you open synaptic > click on "Status" does it not show 'broken'
If so click on and mark for removal
Otherwise try searching in synaptic for amarok14-engine-xine and remove

---

### Post by wildmanne39 on 2011-08-08
> **theozzlives said:**
> I keep getting:
Hi, I believe your hard drive is full, most likely your boot partition, run this command please:
```
df -h
```
and post the results here.
Thank you

---

### Post by theozzlives on 2011-08-08
> ozzie@ozzie-netbook:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.4G  3.3G  5.7G  37% /
none                  740M  308K  740M   1% /dev
none                  750M  332K  749M   1% /dev/shm
none                  750M   20K  750M   1% /tmp
none                  750M  304K  749M   1% /var/run
none                  750M     0  750M   0% /var/lock
none                  750M     0  750M   0% /lib/init/rw
/dev/sda3              45G  634M   42G   2% /home
//192.168.1.4/music   134G   28G  100G  22% /home/ozzie/Music
.

---

### Post by wildmanne39 on 2011-08-08
Hi, that information looks good so that is not the problem.

Have a look at this link please.
[http://allforlinux.com/2010/07/solving-e-sub-process-usrbindpkg-returned-an-error-code1/](http://allforlinux.com/2010/07/solving-e-sub-process-usrbindpkg-returned-an-error-code1/)

---

### Post by theozzlives on 2011-08-08
I got the broken package removed but now I can't install amarok14. If someone would suggest a music player that can do a recursive search of my music and play it randomly, it would be appreciated.

---

### Post by wildmanne39 on 2011-08-08
Hi, I am glad you got package manager working properly again.

I use rhythmbox it will play random, I am not sure about the recursive part, I almost never listen to music.

When your question is resolved, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

### Post by holadebob on 2011-08-08
I've been reading your posts and have wanted the same thing and my Google search turned up this command line player that is capable of random, etc. Looks really easy to use. 


[http://duopetalflower.blogspot.com/2010/07/who-inspired-me-with-commandline-mp3.html](http://duopetalflower.blogspot.com/2010/07/who-inspired-me-with-commandline-mp3.html)

---

### Post by theozzlives on 2011-08-09
It don't matter, it's just my netbook. My laptop is the important one and it's setup.

---

