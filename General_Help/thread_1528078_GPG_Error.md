---
title: "GPG Error"
date: 2010-07-10
forum: General Help
---

### Post by sh_nabih on 2010-07-10
Hi all,

I am new to Ubuntu and I got a problem with updates. I am using Ubuntu 10.04 and when I used the command 'sudo apt-get update' I got the following:

[CODE][Get:1 http://packages.medibuntu.org lucid Release.gpg [197B]
Ign http://packages.medibuntu.org/ lucid/free  Translation-en_US                
Get:2 http://archive.canonical.com lucid Release.gpg  [189B]                    
Ign http://archive.canonical.com/ubuntu/ lucid/partner  Translation-en_US      
Get:3 http://archive.canonical.com lucid Release [8,215B]            
Ign http://packages.medibuntu.org/ lucid/non-free Translation-en_US
Get:4 http://archive.ubuntu.com lucid Release.gpg  [189B]                       
Ign http://archive.ubuntu.com/ubuntu/ lucid/main  Translation-en_US             
Ign http://archive.ubuntu.com/ubuntu/ lucid/restricted  Translation-en_US       
Ign http://archive.ubuntu.com/ubuntu/ lucid/universe  Translation-en_US         
Ign http://archive.ubuntu.com/ubuntu/ lucid/multiverse  Translation-en_US       
Err http://archive.canonical.com lucid  Release                                 
  
Get:5 http://archive.ubuntu.com lucid-updates Release.gpg [189B]       
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/main  Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/restricted  Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/universe  Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-updates/multiverse  Translation-en_US
Hit http://packages.medibuntu.org lucid Release
Hit http://archive.ubuntu.com lucid-security Release.gpg
Ign http://packages.medibuntu.org lucid  Release                            
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/main  Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/restricted  Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/universe  Translation-en_US
Ign http://archive.ubuntu.com/ubuntu/ lucid-security/multiverse  Translation-en_US
Hit http://packages.medibuntu.org lucid/free Packages
Get:6 http://archive.ubuntu.com lucid Release [57.2kB]
Ign http://archive.ubuntu.com lucid  Release                                    
Hit http://packages.medibuntu.org lucid/non-free  Packages                      
Get:7 http://archive.ubuntu.com lucid-updates Release  [44.7kB]                 
Err http://archive.ubuntu.com lucid-updates Release
  
Hit http://archive.ubuntu.com lucid-security Release
Hit http://archive.ubuntu.com lucid/main  Packages                          
Hit http://archive.ubuntu.com lucid/restricted Packages
Hit http://archive.ubuntu.com lucid/restricted Sources
Hit http://archive.ubuntu.com lucid/main Sources
Hit http://archive.ubuntu.com lucid/multiverse Sources
Hit http://archive.ubuntu.com lucid/universe Sources
Hit http://archive.ubuntu.com lucid/universe Packages
Hit http://archive.ubuntu.com lucid/multiverse Packages
Hit http://archive.ubuntu.com lucid-security/main Packages
Hit http://archive.ubuntu.com lucid-security/restricted Packages
Hit http://archive.ubuntu.com lucid-security/restricted Sources
Hit http://archive.ubuntu.com lucid-security/main Sources
Hit http://archive.ubuntu.com lucid-security/multiverse Sources
Hit http://archive.ubuntu.com lucid-security/universe Sources
Hit http://archive.ubuntu.com lucid-security/universe Packages
Hit http://archive.ubuntu.com lucid-security/multiverse Packages
Fetched 767B in 4s (166B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is  not updated and the previous index files will be used.GPG error:  http://archive.canonical.com lucid Release: The following signatures  were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing  Key <ftpmaster@ubuntu.com>

W: GPG error: http://packages.medibuntu.org lucid Release: The following  signatures couldn't be verified because the public key is not  available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: http://archive.ubuntu.com lucid Release: The following  signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive  Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is  not updated and the previous index files will be used.GPG error:  http://archive.ubuntu.com lucid-updates Release: The following  signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive  Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch  http://archive.canonical.com/ubuntu/dists/lucid/Release  

W: Failed to fetch  http://archive.ubuntu.com/ubuntu/dists/lucid-updates/Release  

W: Some index files failed to download, they have been ignored, or old  ones used instead.]

and when I tried '/etc/apt/sources.list'
I got the following even though I have entered my password to run the update:
[CODE][bash: /etc/apt/sources.list: Permission denied]

I also have changed servers and chose the best server, but it did not work.
Could anybody help me to fix this?
Thank you

---

### Post by NertSkull on 2010-07-10
It looks like you added some repositories but didn't add the signatures as well.  I'm still pretty new as well, but usually there are signatures that you need to import as well when adding a new repository so that synaptic knows the download is valid (i'm sure I explained that horribly).

For example it looks like you tried to add medibuntu.  Did you follow the instructions here

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

If you look in the install commands they give, there is a an install keyring that medibuntu does for you.

For other things you have to individually import the authentication key (can be done in synaptic, or add software resources).

Hope that at least kind of points you in a decent direction.

Also, when you get your sources list from the command line, are you sure synaptic is closed.  I've gotten that error before when its still open.  Ubuntu can't have to repository managers open at the same time, i.e. if you try to install something from the command line, synaptic needs to be closed as well.

---

### Post by sh_nabih on 2010-07-10
I have followed what is written in medibuntu help page and I have tried it, now. But I still get the same. do you have any other suggestions?

---

