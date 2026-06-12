---
title: "error when trying apt-get update?"
date: 2009-10-19
forum: General Help
---

### Post by insanity99 on 2009-10-19
i get this error:
```
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FCA4A9D8F45955CE
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://deb.opera.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F9A2F76A9D1A0061

W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
neil@ubuntu:~$ 

```

---

### Post by MelDJ on 2009-10-19
you must add the gpg key for that source. follow this: [http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu](http://blog.launchpad.net/ppa/adding-a-ppas-key-to-ubuntu)

---

### Post by insanity99 on 2009-10-19
do i need the key from  here? 
[http://deb.opera.com/opera/dists/stable/Release](http://deb.opera.com/opera/dists/stable/Release)

because i added that just now and im still getting the error.

EDIT: i added .key to the end and now the error messege is:
neil@ubuntu:~$ sudo apt-get update
[sudo] password for neil: 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Translation-en_GB                 
Get: 1 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg [307B]                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_GB                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_GB                
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_GB            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Translation-en_GB           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Translation-en_GB             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Translation-en_GB 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release.gpg          
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_GB
Get: 2 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [65.9kB]            
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release                                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty Release                                
Hit [http://deb.opera.com](http://deb.opera.com) stable Release.gpg                                    
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Translation-en_GB                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages                            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates Release              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources                             
Hit [http://deb.opera.com](http://deb.opera.com) stable Release                              
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Packages          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/main Sources                 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/restricted Sources           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Packages            
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/universe Sources             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Packages
Ign [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://deb.opera.com](http://deb.opera.com) stable/non-free Packages
Fetched 308B in 0s (601B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FCA4A9D8F45955CE
W: You may want to run apt-get update to correct these problems
neil@ubuntu:~$

---

### Post by MelDJ on 2009-10-19
i think its from this [http://deb.opera.com/](http://deb.opera.com/)

---

### Post by insanity99 on 2009-10-19
yeah i copied this 
-----BEGIN PGP PUBLIC KEY BLOCK-----
Version: GnuPG v1.4.1 (GNU/Linux)

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
=wGGg
-----END PGP PUBLIC KEY BLOCK-----

---

### Post by MelDJ on 2009-10-19
try this? [http://www.go2linux.org/opera-from-repository-for-ubuntu-or-debian](http://www.go2linux.org/opera-from-repository-for-ubuntu-or-debian)

---

