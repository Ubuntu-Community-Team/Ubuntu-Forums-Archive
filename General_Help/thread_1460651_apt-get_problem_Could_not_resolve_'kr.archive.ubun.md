---
title: "apt-get problem: Could not resolve 'kr.archive.ubuntu.com'"
date: 2010-04-23
forum: General Help
---

### Post by zugvogel on 2010-04-23
Hello,
I have a strange problem with apt-get.
I run "sudo apt-get update" and get the errors:

```

Err http://kr.archive.ubuntu.com karmic Release.gpg                         
  Could not resolve 'kr.archive.ubuntu.com'
Err http://kr.archive.ubuntu.com karmic/main Translation-en_US              
  Could not resolve 'kr.archive.ubuntu.com'
Err http://kr.archive.ubuntu.com karmic/restricted Translation-en_US
  Could not resolve 'kr.archive.ubuntu.com'
Err http://kr.archive.ubuntu.com karmic/universe Translation-en_US
  Could not resolve 'kr.archive.ubuntu.com'
Err http://kr.archive.ubuntu.com karmic/multiverse Translation-en_US
  Could not resolve 'kr.archive.ubuntu.com'
Err http://kr.archive.ubuntu.com karmic-updates Release.gpg
  Could not resolve 'kr.archive.ubuntu.com'
Err http://kr.archive.ubuntu.com karmic-updates/main Translation-en_US
  Could not resolve 'kr.archive.ubuntu.com'
Err http://kr.archive.ubuntu.com karmic-updates/restricted Translation-en_US
  Could not resolve 'kr.archive.ubuntu.com'
Err http://kr.archive.ubuntu.com karmic-updates/universe Translation-en_US
  Could not resolve 'kr.archive.ubuntu.com'
Err http://kr.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
  Could not resolve 'kr.archive.ubuntu.com'
Err http://security.ubuntu.com karmic-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com karmic-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com karmic-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com karmic-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err http://security.ubuntu.com karmic-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://kr.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg  Could not resolve 'kr.archive.u
buntu.com'

W: Failed to fetch http://kr.archive.ubuntu.com/ubuntu/dists/karmic/main/i18n/Translation-en_US.bz2  Could not r
esolve 'kr.archive.ubuntu.com'

W: Failed to fetch http://kr.archive.ubuntu.com/ubuntu/dists/karmic/restricted/i18n/Translation-en_US.bz2  Could
 not resolve 'kr.archive.ubuntu.com'

W: Failed to fetch http://kr.archive.ubuntu.com/ubuntu/dists/karmic/universe/i18n/Translation-en_US.bz2  Could n
ot resolve 'kr.archive.ubuntu.com'

W: Failed to fetch http://kr.archive.ubuntu.com/ubuntu/dists/karmic/multiverse/i18n/Translation-en_US.bz2  Could
 not resolve 'kr.archive.ubuntu.com'

W: Failed to fetch http://kr.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release.gpg  Could not resolve 'kr.a
rchive.ubuntu.com'

W: Failed to fetch http://kr.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/i18n/Translation-en_US.bz2  Cou
ld not resolve 'kr.archive.ubuntu.com'

W: Failed to fetch http://kr.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/i18n/Translation-en_US.bz
2  Could not resolve 'kr.archive.ubuntu.com'

W: Failed to fetch http://kr.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/i18n/Translation-en_US.bz2 
 Could not resolve 'kr.archive.ubuntu.com'

W: Failed to fetch http://kr.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/i18n/Translation-en_US.bz
2  Could not resolve 'kr.archive.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/Release.gpg  Could not resolve 'secur
ity.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/main/i18n/Translation-en_US.bz2  Coul
d not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/restricted/i18n/Translation-en_US.bz2
  Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2  
Could not resolve 'security.ubuntu.com'

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/multiverse/i18n/Translation-en_US.bz2
  Could not resolve 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.


```

I can't figure out what's wrong.
Some more information about the set-up:
1. The computer can connect to the internet - actually, I'm doing this over ssh from a computer on the other side of the world.
2. An almost-identical computer with the same setup connected to the same ethernet switch as the above computer has a very different result:

```

Hit http://kr.archive.ubuntu.com karmic Release.gpg
Ign http://kr.archive.ubuntu.com karmic/main Translation-en_US                 
Ign http://kr.archive.ubuntu.com karmic/restricted Translation-en_US           
Ign http://kr.archive.ubuntu.com karmic/universe Translation-en_US             
Ign http://kr.archive.ubuntu.com karmic/multiverse Translation-en_US           
Hit http://kr.archive.ubuntu.com karmic-updates Release.gpg                    
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Ign http://kr.archive.ubuntu.com karmic-updates/main Translation-en_US         
Ign http://kr.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://kr.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://kr.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://kr.archive.ubuntu.com karmic Release
Hit http://kr.archive.ubuntu.com karmic-updates Release                        
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com karmic-security Release                         
Hit http://kr.archive.ubuntu.com karmic/main Packages                          
Hit http://kr.archive.ubuntu.com karmic/restricted Packages                    
Hit http://security.ubuntu.com karmic-security/main Packages                   
Hit http://kr.archive.ubuntu.com karmic/main Sources       
Hit http://security.ubuntu.com karmic-security/restricted Packages
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://kr.archive.ubuntu.com karmic/restricted Sources
Hit http://kr.archive.ubuntu.com karmic/universe Packages                      
Hit http://security.ubuntu.com karmic-security/universe Sources                
Hit http://security.ubuntu.com karmic-security/multiverse Packages             
Hit http://security.ubuntu.com karmic-security/multiverse Sources              
Hit http://kr.archive.ubuntu.com karmic/universe Sources                       
Hit http://kr.archive.ubuntu.com karmic/multiverse Packages
Hit http://kr.archive.ubuntu.com karmic/multiverse Sources 
Hit http://kr.archive.ubuntu.com karmic-updates/main Packages
Hit http://kr.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://kr.archive.ubuntu.com karmic-updates/main Sources
Hit http://kr.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://kr.archive.ubuntu.com karmic-updates/universe Packages
Hit http://kr.archive.ubuntu.com karmic-updates/universe Sources
Hit http://kr.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://kr.archive.ubuntu.com karmic-updates/multiverse Sources
Reading package lists... Done                              

```

which makes me wonder if it's a software problem rather than a hardware one. I've looked around the internet for a solution but can't find the exact same problem I'm having. If anyone can help I'd appreciate it! Thanks in advance.

---

### Post by dcstar on 2010-04-23
> **zugvogel said:**
> Hello,
I have a strange problem with apt-get.
I run "sudo apt-get update" and get the errors:

```

..........
  **Could not resolve** 'security.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.


```

I can't figure out what's wrong.

which makes me wonder if it's a software problem rather than a hardware one. I've looked around the internet for a solution but can't find the exact same problem I'm having. If anyone can help I'd appreciate it! Thanks in advance.

The error means that computer cannot do DNS lookups of that site. Check the DNS functionality.

---

### Post by zugvogel on 2010-04-23
Thank you! I edited /etc/resolv.conf to ensure that it matches the computer that does work (by adding an extra line) and it works. But, once I restart, it falls back to the non-working version. There is a comment line saying "# Generated by NetworkManager" in the first line - is NetworkManager resetting it upon reboot? How can I prevent this?

Thanks!

---

### Post by polki@mac.com on 2010-04-23
Try setting it Network Manager.

---

### Post by zugvogel on 2010-04-25
Well, I understand how to access this through a GUI but the connection's too slow to run a gnome-session over ssh - is there a command-line way to set things in the NetworkManager? I tried just running "sudo NetworkManager", but nothing happens.

Thanks.

---

### Post by dcstar on 2010-04-25
> **zugvogel said:**
> Well, I understand how to access this through a GUI but the connection's too slow to run a gnome-session over ssh - is there a command-line way to set things in the NetworkManager? I tried just running "sudo NetworkManager", but nothing happens.

Thanks.

Remove the network manager package and manually set the /etc/network/interfaces file.

---

