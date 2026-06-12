---
title: "problem in update manager"
date: 2011-05-03
forum: General Help
---

### Post by Gladiator-prog4me on 2011-05-03
Hello 

i have install ubuntu 11.04

and when i make the update , i got this error : 

( Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources. )

when i click details , i got this : ( apt apt-transport-https apt-utils bamfdaemon evince evince-common file-roller firefox firefox-globalmenu firefox-gnome-support gir1.2-dbusmenu-glib-0.4 gir1.2-dee-0.5 gir1.2-panelapplet-3.0 gir1.2-unity-3.0 gnome-panel gnome-panel-bonobo gnome-panel-data gnome-session gnome-session-bin gnome-session-common gnome-user-guide gwibber gwibber-service gwibber-service-facebook gwibber-service-identica gwibber-service-twitter libapache2-mod-php5 libbamf0 libevdocument3 libevview3 liblircclient0 libnux-0.9-0 libnux-0.9-common liboverlay-scrollbar-0.1-0 libpanel-applet-3-0 libpanel-applet2-0 libperl5.10 libpoppler-glib6 libpoppler13 libsmbclient libsyncdaemon-1.0-1 libwbclient0 nux-tools overlay-scrollbar perl perl-base perl-modules php5 php5-cli php5-common php5-curl php5-gd php5-mysql poppler-utils python-ubuntuone-client python-ubuntuone-storageprotocol samba-common samba-common-bin smbclient ubuntuone-client ubuntuone-client-gnome unity unity-common usb-creator-common usb-creator-gtk vino xserver-xorg-video-intel )


please help me .

---

### Post by Frogs Hair on 2011-05-03
Try ```
sudo apt-get update
``` in the terminal and check to see if the sources connect . If they do , close the terminal and try the update manager again.

---

### Post by Gladiator-prog4me on 2011-05-03
> **Frogs Hair said:**
> Try ```
sudo apt-get update
``` in the terminal and check to see if the sources connect . If they do , close the terminal and try the update manager again.

Hi , i got this : 

```
mohamed@mohamed-Server:~$ sudo apt-get update
[sudo] password for mohamed: 
Ign http://extras.ubuntu.com natty InRelease                                   
Ign http://ppa.launchpad.net natty InRelease                                   
Ign http://security.ubuntu.com natty-security InRelease                        
Ign http://dl.google.com stable InRelease                                      
Ign http://eg.archive.ubuntu.com natty InRelease                               
Ign http://eg.archive.ubuntu.com natty-updates InRelease                       
Get:1 http://extras.ubuntu.com natty Release.gpg [72 B]              
Hit http://ppa.launchpad.net natty Release.gpg                                 
Get:2 http://security.ubuntu.com natty-security Release.gpg [198 B]            
Get:3 http://dl.google.com stable Release.gpg [197 B]                          
Get:4 http://eg.archive.ubuntu.com natty Release.gpg [198 B]                   
Hit http://extras.ubuntu.com natty Release                                     
Hit http://ppa.launchpad.net natty Release                                     
Err http://extras.ubuntu.com natty Release                                     
  
Get:5 http://security.ubuntu.com natty-security Release [23.2 kB]              
Err http://security.ubuntu.com natty-security Release                          
  
Get:6 http://dl.google.com stable Release [1,347 B]                            
Hit http://ppa.launchpad.net natty/main Sources                                
Get:7 http://eg.archive.ubuntu.com natty-updates Release.gpg [198 B]
Hit http://ppa.launchpad.net natty/main i386 Packages                
Ign http://ppa.launchpad.net natty/main TranslationIndex             
Get:8 http://dl.google.com stable/main i386 Packages [1,157 B]       
Hit http://eg.archive.ubuntu.com natty Release                                 
Ign http://eg.archive.ubuntu.com natty Release                                 
Ign http://dl.google.com stable/main TranslationIndex                          
Get:9 http://eg.archive.ubuntu.com natty-updates Release [27.2 kB]             
Ign http://eg.archive.ubuntu.com natty-updates Release                         
Ign http://eg.archive.ubuntu.com natty/main Sources/DiffIndex                  
Ign http://eg.archive.ubuntu.com natty/restricted Sources/DiffIndex  
Ign http://eg.archive.ubuntu.com natty/universe Sources/DiffIndex    
Ign http://eg.archive.ubuntu.com natty/multiverse Sources/DiffIndex  
Ign http://eg.archive.ubuntu.com natty/main i386 Packages/DiffIndex  
Ign http://eg.archive.ubuntu.com natty/restricted i386 Packages/DiffIndex
Ign http://eg.archive.ubuntu.com natty/universe i386 Packages/DiffIndex
Ign http://eg.archive.ubuntu.com natty/multiverse i386 Packages/DiffIndex
Ign http://eg.archive.ubuntu.com natty/main TranslationIndex                   
Ign http://eg.archive.ubuntu.com natty/multiverse TranslationIndex             
Ign http://eg.archive.ubuntu.com natty/restricted TranslationIndex             
Ign http://eg.archive.ubuntu.com natty/universe TranslationIndex               
Ign http://eg.archive.ubuntu.com natty-updates/main Sources/DiffIndex          
Ign http://eg.archive.ubuntu.com natty-updates/restricted Sources/DiffIndex
Ign http://eg.archive.ubuntu.com natty-updates/universe Sources/DiffIndex
Ign http://eg.archive.ubuntu.com natty-updates/multiverse Sources/DiffIndex
Ign http://eg.archive.ubuntu.com natty-updates/main i386 Packages/DiffIndex
Ign http://eg.archive.ubuntu.com natty-updates/restricted i386 Packages/DiffIndex
Ign http://eg.archive.ubuntu.com natty-updates/universe i386 Packages/DiffIndex
Ign http://eg.archive.ubuntu.com natty-updates/multiverse i386 Packages/DiffIndex
Ign http://eg.archive.ubuntu.com natty-updates/main TranslationIndex 
Ign http://eg.archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://eg.archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://eg.archive.ubuntu.com natty-updates/universe TranslationIndex
Hit http://eg.archive.ubuntu.com natty/main Sources                  
Hit http://eg.archive.ubuntu.com natty/restricted Sources            
Hit http://eg.archive.ubuntu.com natty/universe Sources              
Hit http://eg.archive.ubuntu.com natty/multiverse Sources            
Hit http://eg.archive.ubuntu.com natty/main i386 Packages            
Hit http://eg.archive.ubuntu.com natty/restricted i386 Packages      
Ign http://ppa.launchpad.net natty/main Translation-en_US            
Hit http://eg.archive.ubuntu.com natty/universe i386 Packages                  
Hit http://eg.archive.ubuntu.com natty/multiverse i386 Packages      
Ign http://ppa.launchpad.net natty/main Translation-en               
Hit http://eg.archive.ubuntu.com natty-updates/main Sources                    
Hit http://eg.archive.ubuntu.com natty-updates/restricted Sources              
Hit http://eg.archive.ubuntu.com natty-updates/universe Sources                
Hit http://eg.archive.ubuntu.com natty-updates/multiverse Sources              
Hit http://eg.archive.ubuntu.com natty-updates/main i386 Packages              
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://eg.archive.ubuntu.com natty-updates/restricted i386 Packages        
Hit http://eg.archive.ubuntu.com natty-updates/universe i386 Packages          
Hit http://eg.archive.ubuntu.com natty-updates/multiverse i386 Packages        
Ign http://dl.google.com stable/main Translation-en                            
Ign http://eg.archive.ubuntu.com natty/main Translation-en_US                  
Ign http://eg.archive.ubuntu.com natty/main Translation-en
Ign http://eg.archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://eg.archive.ubuntu.com natty/multiverse Translation-en
Ign http://eg.archive.ubuntu.com natty/restricted Translation-en_US
Ign http://eg.archive.ubuntu.com natty/restricted Translation-en
Ign http://eg.archive.ubuntu.com natty/universe Translation-en_US
Ign http://eg.archive.ubuntu.com natty/universe Translation-en
Ign http://eg.archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://eg.archive.ubuntu.com natty-updates/main Translation-en
Ign http://eg.archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://eg.archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://eg.archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://eg.archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://eg.archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://eg.archive.ubuntu.com natty-updates/universe Translation-en
Fetched 3,369 B in 30s (111 B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://extras.ubuntu.com natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://security.ubuntu.com natty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

W: GPG error: http://eg.archive.ubuntu.com natty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: http://eg.archive.ubuntu.com natty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/natty/Release  

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/natty-security/Release  

W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by wilee-nilee on 2011-05-03
Bottom of the apt-get the missing keys can be gotten with his command.
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID  
```

You have added 3rd party sources without the keys, and all those updates look okay as well.

When you add stuff without the key or at times a 3rd part resource is set for upgrade you may get these warnings, not much to worry about really. Just be intelligent about what you add to your source list, ie ask or research it on google.

If you want us to look at the actual source list to make sure there are no errors, run in the terminal then post the results.
```
cat /etc/apt/sources.list
```

---

### Post by Gladiator-prog4me on 2011-05-03
> **wilee-nilee said:**
> Bottom of the apt-get the missing keys can be gotten with his command.
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys KEYID  
```

You have added 3rd party sources without the keys, and all those updates look okay as well.

When you add stuff without the key or at times a 3rd part resource is set for upgrade you may get these warnings, not much to worry about really. Just be intelligent about what you add to your source list, ie ask or research it on google.

If you want us to look at the actual source list to make sure there are no errors, run in the terminal then post the results.
```
cat /etc/apt/sources.list
```


thank you :) it's working fine now 

but i see this : 

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

what's this mean ?

---

### Post by wilee-nilee on 2011-05-03
> **Gladiator-prog4me said:**
> thank you :) it's working fine now 

but i see this : 

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), [COLOR="Red"]**is another process using it?**[/COLOR]

```

what's this mean ?

With software sources, and synaptic you can have only one open while running them same with a terminal update/upgrade.

Every so often though you system will be doing a lower level behind the scenes update and you get this error as well.

---

### Post by Gladiator-prog4me on 2011-05-03
> **wilee-nilee said:**
> With software sources, and synaptic you can have only one open while running them same with a terminal update/upgrade.

Every so often though you system will be doing a lower level behind the scenes update and you get this error as well.

thank you , please i have another question , how to show the active programs , i mean the " Alt + Tab " but like mac or the picture : [http://www.ubuntugeek.com/wp-content/uploads/2010/12/ubuntu-tweak-058-02.png](http://www.ubuntugeek.com/wp-content/uploads/2010/12/ubuntu-tweak-058-02.png)

---

### Post by wilee-nilee on 2011-05-03
> **Gladiator-prog4me said:**
> thank you , please i have another question , how to show the active programs , i mean the " Alt + Tab " but like mac or the picture : [http://www.ubuntugeek.com/wp-content/uploads/2010/12/ubuntu-tweak-058-02.png](http://www.ubuntugeek.com/wp-content/uploads/2010/12/ubuntu-tweak-058-02.png)

Hmm, not sure I understand, I have hardly used the unity desktop, I actually just upgraded to Oneiric, and got back the darn side panel, lol. And the unity plugin which can resize that very panel. It now seems almost usable with the side panel shrunk down to the smallest, at least for me.

I have just used the 4 desktops and the crtl+up-down-R-L arrows to navigate between them. I don't think this answers your question though, sorry.

---

### Post by Gladiator-prog4me on 2011-05-03
> **wilee-nilee said:**
> Hmm, not sure I understand, I have hardly used the unity desktop, I actually just upgraded to Oneiric, and got back the darn side panel, lol. And the unity plugin which can resize that very panel. It now seems almost usable with the side panel shrunk down to the smallest, at least for me.

I have just used the 4 desktops and the crtl+up-down-R-L arrows to navigate between them. I don't think this answers your question though, sorry.

Oneiric >> did you mean ubuntu 11.10 ?

---

### Post by wilee-nilee on 2011-05-03
> **Gladiator-prog4me said:**
> Oneiric >> did you mean ubuntu 11.10 ?

Yeah but it is one of 5 OS on my netbook, so it is a tester, got it cloned though in case it breaks. They just started the development of it so it would be considered unstable.

---

