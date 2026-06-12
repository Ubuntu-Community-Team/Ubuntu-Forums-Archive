---
title: "Problems Upgrading to evolution 2.30 on 10.04 lts"
date: 2011-12-09
forum: General Help
---

### Post by adwmd03 on 2011-12-09
Hello

I am using ubuntu 10.04 lts. I am attempting to upgrade to evolution 2.30 because 2.28 does not support push/pull. I have searched around and found instructions to do this. My problem is I get an error when trying to add repository via the following command: sudo add-apt-repository ppa:jacob/evo230

the error I get is: Error: can't find signing_key_fingerprint at [https://launchpad.net/api/1.0/~jacob/+archive/evo230](https://launchpad.net/api/1.0/~jacob/+archive/evo230)

Can someone help me figure this out or point me in the right direction to upgrade evolution to a version that support imap+ aka push/pull.

Thank you!

---

### Post by BC59 on 2011-12-09
Try this. 

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

You have to enable Backports. Then upgrade to see if Evolution is upgraded to the latest version.

---

### Post by adwmd03 on 2011-12-09
I already have backports enabled. Any other ideas?

the following link is what I am trying to do to update evolution: [http://www.jsimmons.co.uk/2011/08/19/using-imap-with-evolution-on-ubuntu-10-04-lts/](http://www.jsimmons.co.uk/2011/08/19/using-imap-with-evolution-on-ubuntu-10-04-lts/)

---

### Post by BC59 on 2011-12-09
Let's see if you can avoid the problem with the key

run the command in a terminal:

```
sudo add-apt-repository ppa:jacob/evo230
```

then will see in the last sentence NO_PUBKEYE [COLOR="blue"]xxxxxx[/COLOR].
Copy the given number of the key [COLOR="Blue"]xxxxx[/COLOR] and run:

```
gpg --keyserver keyserver.ubuntu.com --recv [COLOR="blue"]xxxxxxx[/COLOR]
```

and 

```
gpg --export --armor [COLOR="blue"]xxxxxx[/COLOR] | sudo apt-key add -
```

finally

```
sudo apt-get update && sudo apt-get upgrade
```

or

```
sudo apt-get update && sudo apt-get install --reinstall evolution
```

---

### Post by adwmd03 on 2011-12-09
below is the error i get when trying to run "sudo add-apt-repository ppa:jacob/evo230

adwmd03@moose:~$ sudo add-apt-repository ppa:jacob/evo230
Error: can't find signing_key_fingerprint at [https://launchpad.net/api/1.0/~jacob/+archive/evo230](https://launchpad.net/api/1.0/~jacob/+archive/evo230)

It does not attempt to download/do anything. It is acting like the repository does not exist. I have looked high and low and cannot find anything on how to fix the error....

---

### Post by BC59 on 2011-12-09
In that case try to add the PPA directly to the sources.list 

first do a backup:

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

then run:

```
gksudo gedit /etc/apt/sources.list
```

then add these two lines

> deb [http://evolution-kolab.sourceforge.net/ubuntu](http://evolution-kolab.sourceforge.net/ubuntu) lucid main
deb [http://ppa.launchpad.net/jacob/evo230/ubuntu](http://ppa.launchpad.net/jacob/evo230/ubuntu) lucid main


finally try to see if the repository is working:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by adwmd03 on 2011-12-09
adwmd03@moose:~$ gksudo gedit /etc/apt/sources.list
adwmd03@moose:~$ sudo apt-get update && sudo apt-get upgrade
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                            
Ign [http://ppa.launchpad.net/jacob/evo230/ubuntu/](http://ppa.launchpad.net/jacob/evo230/ubuntu/) lucid/main Translation-en_US             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                                         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US                      
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                                  
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US               
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US         
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                             
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                                 
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US                  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release.gpg         
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US           
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                                      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                           
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_US            
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages    
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                     
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-backports/universe Packages
W: Failed to fetch [http://ppa.launchpad.net/jacob/evo230/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/jacob/evo230/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.
adwmd03@moose:~$

---

### Post by adwmd03 on 2011-12-09
above is what I get when I attempted to add the ppa directly to the source list. Does anything stick out to you?

---

### Post by BC59 on 2011-12-09
You have to undo the changes, the ppa is out.

The only solution could be to download the 2.30 from the sourceforge site and install it manually.

---

### Post by BC59 on 2011-12-09
The address is here if you dare to do it:

[http://evolution-kolab.sourceforge.net/ubuntu/dists/lucid/main/](http://evolution-kolab.sourceforge.net/ubuntu/dists/lucid/main/)

---

### Post by adwmd03 on 2011-12-09
are there any guides on how to manually install something like this?

---

### Post by BC59 on 2011-12-10
There is a guide:

Locate the right packages in the evolution-kolab package repository: 
[http://evolution-kolab.sourceforge.net/ubuntu/dists/lucid/main/](http://evolution-kolab.sourceforge.net/ubuntu/dists/lucid/main/)

Required files (32bit):
evolution-kolab_0.2.0_i386.deb 
libcurl3-nss_7.19.7-1ubuntu2~6.gbpaa10b9_i386.deb 
libcurl3_7.19.7-1ubuntu2~6.gbpaa10b9_i386.deb 
Optional files (32bit):
curl_7.19.7-1ubuntu2~6.gbpaa10b9_i386.deb 
evolution-kolab-dev_0.2.0_i386.deb 
libcurl3-dbg_7.19.7-1ubuntu2~6.gbpaa10b9_i386.deb 
libcurl3-gnutls_7.19.7-1ubuntu2~6.gbpaa10b9_i386.deb 
libcurl4-gnutls-dev_7.19.7-1ubuntu2~6.gbpaa10b9_i386.deb 
libcurl4-nss-dev_7.19.7-1ubuntu2~6.gbpaa10b9_i386.deb 
libcurl4-openssl-dev_7.19.7-1ubuntu2~6.gbpaa10b9_i386.deb 

Required files (64bit):
evolution-kolab_0.2.0_amd64.deb 
libcurl3-nss_7.19.7-1ubuntu2~6.gbpaa10b9_amd64.deb 
libcurl3_7.19.7-1ubuntu2~6.gbpaa10b9_amd64.deb 
Optional files (64bit):
curl_7.19.7-1ubuntu2~6.gbpaa10b9_amd64.deb 
evolution-kolab-dev_0.2.0_amd64.deb 
libcurl3-dbg_7.19.7-1ubuntu2~6.gbpaa10b9_amd64.deb 
libcurl3-gnutls_7.19.7-1ubuntu2~6.gbpaa10b9_amd64.deb 
libcurl4-gnutls-dev_7.19.7-1ubuntu2~6.gbpaa10b9_amd64.deb
libcurl4-nss-dev_7.19.7-1ubuntu2~6.gbpaa10b9_amd64.deb 
libcurl4-openssl-dev_7.19.7-1ubuntu2~6.gbpaa10b9_amd64.deb

Create a new directory 
```
sudo mkdir /usr/src/evolution-kolab/
```
```
gksudo nautilus
``` and download the necessary files (.debs) for your architecture in the directory.

```
sudo cd /usr/src/evolution-kolab/
```

```
sudo dpkg -i *.deb
```

 
Good luck

---

