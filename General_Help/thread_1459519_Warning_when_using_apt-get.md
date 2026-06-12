---
title: "Warning when using apt-get"
date: 2010-04-21
forum: General Help
---

### Post by Velvet Karuda Leopard on 2010-04-21
Hello.

Whenever I use Aptitude in my terminal I get a warning I would like to get rid of.

It is a GPG warning:

```
skybrigidrain@Alexi:~$ sudo apt-get update
Get:1 http://packages.medibuntu.org karmic Release.gpg [197B]
Ign http://packages.medibuntu.org karmic/free Translation-en_US      
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US  
Hit http://security.ubuntu.com karmic-security Release.gpg           
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release.gpg                  
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US       
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Get:2 http://packages.medibuntu.org karmic Release [9,237B]          
Hit http://security.ubuntu.com karmic-security Release
Ign http://packages.medibuntu.org karmic Release
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release                      
Hit http://security.ubuntu.com karmic-security/main Packages                   
Hit http://packages.medibuntu.org karmic/free Packages               
Hit http://us.archive.ubuntu.com karmic-updates Release
Hit http://security.ubuntu.com karmic-security/restricted Packages             
Hit http://security.ubuntu.com karmic-security/main Sources          
Hit http://security.ubuntu.com karmic-security/restricted Sources    
Hit http://security.ubuntu.com karmic-security/universe Packages     
Hit http://packages.medibuntu.org karmic/non-free Packages           
Hit http://us.archive.ubuntu.com karmic/main Packages                
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Fetched 198B in 1s (126B/s)
Reading package lists... Done
W: GPG error: http://packages.medibuntu.org karmic Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

```

That is the output of a simple apt-get update.

What is this warning and how do I fix it?

---

### Post by nothingspecial on 2010-04-21
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add – && sudo apt-get update
```

---

### Post by Velvet Karuda Leopard on 2010-04-21
```
skybrigidrain@Alexi:~$ wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add – && sudo apt-get update
[sudo] password for skybrigidrain: 
gpg: can't open `–': No such file or directory

```

---

### Post by lisati on 2010-04-21
Side note: some people have noticed a problem with medibuntu over the last few days. [http://ubuntuforums.org/showpost.php?p=9154428&postcount=9](http://ubuntuforums.org/showpost.php?p=9154428&postcount=9)

---

### Post by wojox on 2010-04-21
Here's what I usually run:

```
gpg --keyserver pgpkeys.mit.edu --recv-key  2EBC26B60C5A2783
```

```
gpg -a --export 2EBC26B60C5A2783 | sudo apt-key add -
```

---

### Post by Velvet Karuda Leopard on 2010-04-21
Alright, that last deal fixed it.  Not sure why it was trying to open '-` for.

```
skybrigidrain@Alexi:~$ wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add – && sudo apt-get update
[sudo] password for skybrigidrain: 
gpg: can't open `–': No such file or directory
skybrigidrain@Alexi:~$ gpg --keyserver pgpkeys.mit.edu --recv-key  2EBC26B60C5A2783
gpg: requesting key 0C5A2783 from hkp server pgpkeys.mit.edu
gpg: key 0C5A2783: public key "Medibuntu Packaging Team <admin@lists.medibuntu.org>" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1
skybrigidrain@Alexi:~$ gpg -a --export 2EBC26B60C5A2783 | sudo apt-key add -
OK
skybrigidrain@Alexi:~$ sudo apt-get update
Get:1 http://packages.medibuntu.org karmic Release.gpg [197B]
Ign http://packages.medibuntu.org karmic/free Translation-en_US      
Ign http://packages.medibuntu.org karmic/non-free Translation-en_US  
Hit http://us.archive.ubuntu.com karmic Release.gpg                  
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US       
Hit http://security.ubuntu.com karmic-security Release.gpg           
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Get:2 http://packages.medibuntu.org karmic Release [9,237B]          
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release                      
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://security.ubuntu.com karmic-security Release               
Hit http://packages.medibuntu.org karmic/free Packages
Hit http://us.archive.ubuntu.com karmic-updates Release
Hit http://security.ubuntu.com karmic-security/main Packages                   
Hit http://packages.medibuntu.org karmic/non-free Packages           
Hit http://us.archive.ubuntu.com karmic/main Packages
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://security.ubuntu.com karmic-security/restricted Packages
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Fetched 198B in 1s (121B/s)
Reading package lists... Done
skybrigidrain@Alexi:~$ 

```

Yes.  I had already went through some steps to fix the medibuntu hicup.  It had to do with a DNS IP swich in /etc/host file.  I had to do that before I could watch my beloved Alien legacy DVDs.

---

