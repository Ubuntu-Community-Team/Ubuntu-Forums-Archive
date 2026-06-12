---
title: "polipo problem :\"
date: 2009-11-29
forum: General Help
---

### Post by ronald74437 on 2009-11-29
I install polipo and decided against it, now the setting I used are messing up my ```
sudo apt-get update
```whenever i run it i get:



```
john@john-laptop:~$ sudo apt-get update
Err http://ppa.launchpad.net karmic Release.gpg
  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)
Err http://us.archive.ubuntu.com karmic Release.gpg                            
  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)
Err http://security.ubuntu.com karmic-security Release.gpg                     
  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)
Err http://us.archive.ubuntu.com karmic/main Translation-en_US                 
  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)
Err http://deb.torproject.org karmic Release.gpg                               
  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)
Err http://security.ubuntu.com karmic-security/main Translation-en_US          
  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)
Err http://packages.medibuntu.org karmic Release.gpg                           
  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)
Err http://ppa.launchpad.net karmic/main Translation-en_US                     
  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)
Err http://packages.medibuntu.org karmic/free Translation-en_US                
  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)
Err http://us.archive.ubuntu.com karmic/restricted Translation-en_US           
  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)
Err http://deb.torproject.org karmic/main Translation-en_US                    
  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)
Err http://security.ubuntu.com karmic-security/restricted Translation-en_US    
  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)
Err http://packages.medibuntu.org karmic/non-free Translation-en_US            
  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)
Err http://us.archive.ubuntu.com karmic/universe Translation-en_US             
  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)
Err http://security.ubuntu.com karmic-security/universe Translation-en_US      
  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)
Err http://us.archive.ubuntu.com karmic/multiverse Translation-en_US           
  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)
Err http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)
Err http://us.archive.ubuntu.com karmic-updates Release.gpg                    
  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)
Err http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)
Err http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)
Err http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)
Err http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)
Reading package lists... Done               
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz2  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz2  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch http://deb.torproject.org/torproject.org/dists/karmic/Release.gpg  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch http://deb.torproject.org/torproject.org/dists/karmic/main/i18n/Translation-en_US.bz2  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch http://packages.medibuntu.org/dists/karmic/Release.gpg  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch http://packages.medibuntu.org/dists/karmic/free/i18n/Translation-en_US.bz2  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch http://packages.medibuntu.org/dists/karmic/non-free/i18n/Translation-en_US.bz2  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/karmic/Release.gpg  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2  Could not connect to 192.168.0.1:8123 (192.168.0.1). - connect (111: Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
john@john-laptop:~$ 

```i do remember setting polipo up to do something with that port (8123)

i think i uninstalled it properly but not sure. and set up privoxy (using port 8118 )

1) how do i know if polipo is gone/not being used
2) how do i fix my mistake

p.s. im still learning the ways of ubuntu. i thought i could handle a simple proxy set up, but i guess not hehe

---

### Post by BenAshton24 on 2009-11-29
Try removing it with
> sudo apt-get --purge remove polipo

---

### Post by BenAshton24 on 2009-11-29
Sorry, I didn't really read your post properly :P

Simply remove the following line from "/etc/apt/apt.conf"
> Acquire::http::Proxy "http://192.168.0.1:8123";

---

### Post by ronald74437 on 2009-11-29
> **BenAshton24 said:**
> Try removing it with
ok, so its gone, and had been gone. now i know that. 

My other problem still exits, and that is how the ```
sudo apt-get update
``` command brings up all those shenanigans that i listed up top

---

### Post by Sin@Sin-Sacrifice on 2009-11-29
You actually need to remove the entries from /etc/apt/sources.list. You can also use System>Administration>Software Sources>3rd Party Sources.

---

### Post by BenAshton24 on 2009-11-29
> **ronald74437 said:**
> ok, so its gone, and had been gone. now i know that. 

My other problem still exits, and that is how the ```
sudo apt-get update
``` command brings up all those shenanigans that i listed up top

Did you try following my second post?

> **Sin@Sin-Sacrifice said:**
> You actually need to remove the entries from /etc/apt/sources.list. You can also use System>Administration>Software Sources>3rd Party Sources.

That's not the problem, when installing, the OP set apt to get things using the polipo and now that it has gone the OP can't use apt-get since there is no proxy through which to contact the repos.

---

### Post by ronald74437 on 2009-11-29
> **Sin@Sin-Sacrifice said:**
> You actually need to remove the entries from /etc/apt/sources.list. You can also use System>Administration>Software Sources>3rd Party Sources.

The only Sources i have in Other Software are for torproject, wine, and something that says  [http://packages.medubuntu.org/karmic](http://packages.medubuntu.org/karmic)    free non-free

Im not sure if you guys understand what im asking for help with. I think i messed up the pathway that the update goes through to talk with the servers (or im totally wrong) but i think its something that may be like that. how do i set up the settings so that it doesnt route itselt through the proxy that doesnt even exist anymore

---

### Post by ronald74437 on 2009-11-29
> **BenAshton24 said:**
> Sorry, I didn't really read your post properly :P

Simply remove the following line from "/etc/apt/apt.conf"

i ran ```
sudo gedit /etc/apt/apt.conf
``` and there was nothing in it :(

Now that you told me to do that though, i do remember adding that when i installed polipo

---

### Post by BenAshton24 on 2009-11-29
> **ronald74437 said:**
> i ran ```
sudo gedit /etc/apt/apt.conf
``` and there was nothing in it :(

Now that you told me to do that though, i do remember adding that when i installed polipo

Is your computer still set to use a proxy by default? 

System->Preferences->network proxy

change to "direct internet connection"

Hope this helps
Ben.

---

### Post by ronald74437 on 2009-11-29
> **BenAshton24 said:**
> Is your computer still set to use a proxy by default? 

System->Preferences->network proxy

change to "direct internet connection"

Hope this helps
Ben.
that it was :D

fixed that

restarting now :P

thanks for walking me through my newbie mistakes 


i just restarted my laptop...(im on my pc with windows) and its going through file system checks

is that normal ??!?

---

### Post by ronald74437 on 2009-11-29
Never mind, it loaded fairly quickly

just never saw that screen before

---

### Post by BenAshton24 on 2009-11-29
Yes, that's perfectly normal, Ubuntu does filesystem checks after every 30 boots.

Ben.

---

