---
title: "Multiple package managers open...when there's not..."
date: 2009-10-30
forum: General Help
---

### Post by ColdLunch on 2009-10-30
Hey UF, slightly annoying problem here. :)

Whenever I try to open Synaptic from the System>Administration menu, I get this error message:

"Unable to get exclusive lock.   This usually means that another package management application (like apt-get or aptitute) is already running.  Please close that application first."


But the thing is, nothing else is running.  I haven't opened ANYTHING. I've tried restarting but no luck.

Any idea whats going wrong?

Thanks so much guys! :)

---

### Post by lilbill on 2009-10-30
what is the output of

```

sudo apt-get update

```
Let's see if that works.

---

### Post by ColdLunch on 2009-10-30
Here you go! :D
```

Hit http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_US          
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US    
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US      
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US    
Hit http://security.ubuntu.com karmic-security Release                         
Hit http://us.archive.ubuntu.com karmic Release.gpg
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US
Hit http://security.ubuntu.com karmic-security/main Packages
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release
Hit http://security.ubuntu.com karmic-security/restricted Packages  
Hit http://security.ubuntu.com karmic-security/main Sources         
Hit http://security.ubuntu.com karmic-security/restricted Sources   
Hit http://security.ubuntu.com karmic-security/universe Packages    
Hit http://security.ubuntu.com karmic-security/universe Sources     
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates Release
Hit http://us.archive.ubuntu.com karmic/main Packages
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/main Sources
Hit http://us.archive.ubuntu.com karmic/restricted Sources
Hit http://us.archive.ubuntu.com karmic/universe Packages
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Ign http://us.archive.ubuntu.com karmic-updates/main Packages
Ign http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Ign http://us.archive.ubuntu.com karmic-updates/universe Sources
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Ign http://us.archive.ubuntu.com karmic-updates/main Packages
Ign http://us.archive.ubuntu.com karmic-updates/restricted Packages
Ign http://us.archive.ubuntu.com karmic-updates/universe Sources
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Err http://us.archive.ubuntu.com karmic-updates/main Packages
  403  Forbidden [IP: 130.239.18.165 80]
Err http://us.archive.ubuntu.com karmic-updates/restricted Packages
  403  Forbidden [IP: 130.239.18.165 80]
Err http://us.archive.ubuntu.com karmic-updates/universe Sources
  403  Forbidden [IP: 130.239.18.165 80]
Err http://us.archive.ubuntu.com karmic-updates/multiverse Packages
  403  Forbidden [IP: 130.239.18.165 80]
W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/main/binary-i386/Packages.gz  403  Forbidden [IP: 130.239.18.165 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/restricted/binary-i386/Packages.gz  403  Forbidden [IP: 130.239.18.165 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/universe/source/Sources.gz  403  Forbidden [IP: 130.239.18.165 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/karmic-updates/multiverse/binary-i386/Packages.gz  403  Forbidden [IP: 130.239.18.165 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.


```

---

### Post by lilbill on 2009-10-30
Strange that apt works but Synaptic won't...I'm at a loss here.  Until someone else can come up with an idea you can just apt-get to manage your packages.  Sorry I'm not more help!  Here's a tutorial for apt if you need one [https://help.ubuntu.com/8.04/serverguide/C/apt-get.html]("https://help.ubuntu.com/8.04/serverguide/C/apt-get.html")

---

### Post by ColdLunch on 2009-10-30
Thanks!

Also, I've been downloading .deb files from the internet and using GDebi to install them.  Now, GDebi is telling me to close other package managers before installing so I can't use that.  Any way to install .deb files without it?

---

### Post by ColdLunch on 2009-10-30
Also, is apt working even though I had all those Failure messages at the bottom?

---

### Post by lilbill on 2009-10-30
Those errors seem to be a result of some firewall settings namely if your ISP/proxy has blocked some IPs, see:
[http://ubuntuforums.org/showthread.php?t=186455]("http://ubuntuforums.org/showthread.php?t=186455")

As for installing .deb files, the standard tool is dpkg which apt, aptitude and synaptic all interact with as well.  Here's a good reference for that:
[http://www.debianadmin.com/debianubuntu-package-management-using-dpkg.html]("http://www.debianadmin.com/debianubuntu-package-management-using-dpkg.html")

---

### Post by ColdLunch on 2009-10-30
Thanks for the links. :)I fixed it.

I ran this:
sudo dpkg --configure -a

And it worked fine again. woot.

---

### Post by lilbill on 2009-10-30
Sweet! Congrats! :D

---

