---
title: "GPG Question"
date: 2009-07-30
forum: General Help
---

### Post by dragon84 on 2009-07-30
hi guys, i have just installed vlc and i installed it using terminal using [http://www.ubuntugeek.com/howto-install-vlc-media-player-1-0-0-in-ubuntu.html](http://www.ubuntugeek.com/howto-install-vlc-media-player-1-0-0-in-ubuntu.html) as a guide. i came across this command "sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7613768D" and it has got me thinking. what does this command actually do? does the key get stored in your keyring for future use or does it get removed after installing the program? what would happen if one day i typed "sudo apt-key adv --recv-keys --keyserver keyserver.dodgysite.com 12345678" and stored the dodgy site's key got stored? will i be able to remove the key?:confused:

all help is appreciated.

Thanks

---

### Post by sisco311 on 2009-07-30
Hi and welcome to the forums!

> **dragon84 said:**
> what does this command actually do?


downloads the public key 

> **dragon84 said:**
> 
does the key get stored in your keyring for future use or does it get removed after installing the program?


yes, it's stored. the public key is used to authenticate downloaded packages.


> **dragon84 said:**
> 
what would happen if one day i typed "sudo apt-key adv --recv-keys --keyserver keyserver.dodgysite.com 12345678" and stored the dodgy site's key got stored?


don't do it. :)

don't add new keys and do not install packages from untrusted sources.  

> **dragon84 said:**
> 
will i be able to remove the key?:confused:


yes, you can use the apt-key command.

to list the keys:
```
sudo apt-key list
```
to remove a key:
```
sudo apt-get del keyid
```
i.e.
```
sisco@acme:~$sudo apt-key list
/etc/apt/trusted.gpg
--------------------
pub   1024D/437D05B5 2004-09-12
uid                  Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
sub   2048g/79164387 2004-09-12

pub   1024D/FBB75451 2004-12-30
uid                  Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>

pub   1024R/**12345678** 2009-04-04
uid                  dodgysite.com malwares :evil: 
sisco@acme:~$sudo apt-key del 12345678
OK
```

for more info, please read the man page:
```
man apt-key
```

and the community documentation:
[uhelp]community/SecureApt[/uhelp]

EDIT: if you prefer the GUI to manage the keys, then go to *System -> Administration -> Software Sources -> Authentication tab*

---

### Post by dragon84 on 2009-07-30
wow, thanks for the quick reply. solved all my issues. thanks heaps:D

---

