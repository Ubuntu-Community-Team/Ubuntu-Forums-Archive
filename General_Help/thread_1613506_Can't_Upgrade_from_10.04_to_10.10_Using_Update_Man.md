---
title: "Can't Upgrade from 10.04 to 10.10 Using Update Manager"
date: 2010-11-04
forum: General Help
---

### Post by scythe01 on 2010-11-04
The upgrade button in update manager does not appear. I already installed necessary updates and changed the settings to show normal releases.

Thanks

---

### Post by sanderd17 on 2010-11-04
could you run

```

sudo aptitude update

```

if there are errors, post it here, if not, run

```

sudo aptitude full-upgrade

```

to upgrade your distro (if you are ready for it: backups ...).

---

### Post by Lancro on 2010-11-04
```
update-manager -d
```

---

### Post by scythe01 on 2010-11-04
> **sanderd17 said:**
> could you run

```

sudo aptitude update

```

if there are errors, post it here, if not, run

```

sudo aptitude full-upgrade

```

to upgrade your distro (if you are ready for it: backups ...).

I can check for updates using update manager but the problem is that the upgrade button to 10.10 does not appears
If I run
```

sudo aptitude update

```

Ign [http://dl.google.com](http://dl.google.com) stable Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                              
Ign [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main Translation-en_PH        
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid Release.gpg                        
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_PH
Ign [http://dl.google.com](http://dl.google.com) stable Release       
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid Release 
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_PH
Ign [http://dl.google.com](http://dl.google.com) stable/main Packages                              
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                    
Ign [http://dl.google.com](http://dl.google.com) stable/main Packages                              
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_PH
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                     
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_PH  
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                    
Err [http://dl.google.com](http://dl.google.com) stable/main Packages                              
  407  Proxy Authentication Required
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_PH     
Ign [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                          
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates Release.gpg
Err [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages
  407  Proxy Authentication Required
Err [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources
  407  Proxy Authentication Required
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_PH
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_PH
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_PH
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-security Release.gpg
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_PH
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_PH
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_PH
Ign [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_PH
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid Release
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates Release
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-security Release
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid/main Packages 
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid/restricted Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid/universe Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-security/main Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-security/restricted Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-security/universe Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-security/multiverse Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid/main Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid/restricted Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid/universe Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid/multiverse Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates/main Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates/restricted Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates/universe Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates/multiverse Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-security/main Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-security/restricted Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-security/universe Packages
Ign [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-security/multiverse Packages
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid/main Packages
  407  Proxy Authentication Required
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid/restricted Packages
  407  Proxy Authentication Required
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid/universe Packages
  407  Proxy Authentication Required
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid/multiverse Packages
  407  Proxy Authentication Required
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates/main Packages
  407  Proxy Authentication Required
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates/restricted Packages
  407  Proxy Authentication Required
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates/universe Packages
  407  Proxy Authentication Required
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-updates/multiverse Packages
  407  Proxy Authentication Required
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-security/main Packages
  407  Proxy Authentication Required
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-security/restricted Packages
  407  Proxy Authentication Required
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-security/universe Packages
  407  Proxy Authentication Required
Err [http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) lucid-security/multiverse Packages
  407  Proxy Authentication Required
Reading package lists... Done

These will appear even though I already set the network proxy settings and applies it system-wide

---

### Post by sanderd17 on 2010-11-06
and what happens with the second command? or with the command from Lancro?

My command is CLI based, Lancro's is GUI based, but both are equivalent.

---

### Post by @lpha on 2010-11-06
Hello sanderd17, try "update-manager -d" like Lancro suggested and everything should work. Make sure you do not type "sudo" into the command line though because other people in the forums reported that the update button won't appear if you do add it in.

---

### Post by sikander3786 on 2010-11-06
I think it is a proxy authentication problem. Please take a look at this solved thread.

[http://ubuntuforums.org/showthread.php?t=1614014](http://ubuntuforums.org/showthread.php?t=1614014)

---

### Post by YfoMp5QBh2 on 2010-11-14
Can you download the .ISO and burn it to a CD? I had this trouble so burnt 10.10 down onto a CD instead and I managed to upgrade to 10.10 from 10.04 no problem.

---

### Post by ivarn on 2010-11-14
in software sources, have you changed the distro from LTS to all distors?
In 10.04, lts is the default option.

---

