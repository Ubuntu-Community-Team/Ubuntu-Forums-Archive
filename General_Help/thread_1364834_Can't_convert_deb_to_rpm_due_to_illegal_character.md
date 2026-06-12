---
title: "Can't convert deb to rpm due to illegal character"
date: 2009-12-26
forum: General Help
---

### Post by isaacj87 on 2009-12-26
I'm trying to convert a deb (docky in particular) into an rpm. I'm attempting to do this with alien, but it keeps spitting back an error about an illegal character (~). Here's the output:

```
alien -r -v docky_2.0_bzr1002-0karmic1~dockycore1_amd64.deb                               
Warning: alien is not running as root!                  
Warning: Ownerships of files in the generated packages will probably be wrong.                                        
        dpkg-deb --info docky_2.0_bzr1002-0karmic1~dockycore1_amd64.deb control 2>/dev/null                           
        dpkg-deb --info docky_2.0_bzr1002-0karmic1~dockycore1_amd64.deb control 2>/dev/null                           
        dpkg-deb --info docky_2.0_bzr1002-0karmic1~dockycore1_amd64.deb conffiles 2>/dev/null                         
        dpkg-deb --fsys-tarfile docky_2.0_bzr1002-0karmic1~dockycore1_amd64.deb | tar tf -                            
        dpkg-deb --info docky_2.0_bzr1002-0karmic1~dockycore1_amd64.deb postinst 2>/dev/null                          
        dpkg-deb --info docky_2.0_bzr1002-0karmic1~dockycore1_amd64.deb postrm 2>/dev/null                            
        dpkg-deb --info docky_2.0_bzr1002-0karmic1~dockycore1_amd64.deb preinst 2>/dev/null                           
        dpkg-deb --info docky_2.0_bzr1002-0karmic1~dockycore1_amd64.deb prerm 2>/dev/null                             
        mkdir docky-2.0~bzr1002
        chmod 755 docky-2.0~bzr1002
        dpkg-deb -x docky_2.0_bzr1002-0karmic1~dockycore1_amd64.deb docky-2.0~bzr1002
        rpm --showrc
        cd docky-2.0~bzr1002; rpmbuild --buildroot=/home/isaac/Source/docky-2.0~bzr1002 -bb --target x86_64 docky-2.0~bzr1002-1.spec 2>&1
Package build failed. Here's the log of the command (cd docky-2.0~bzr1002; rpmbuild --buildroot=/home/isaac/Source/docky-2.0~bzr1002 -bb --target x86_64 docky-2.0~bzr1002-1.spec):
error: line 3: Illegal char '~' in: Version: 2.0~bzr1002
Building target platforms: x86_64
Building for target x86_64
        find docky-2.0~bzr1002 -type d -exec chmod 755 {} ;
        rm -rf docky-2.0~bzr1002
```

What should I do about this?

---

### Post by Woody1987 on 2009-12-26
remove the ~ in the filename. So docky_2.0_bzr1002-0karmic1~dockycore1_amd64.deb becomes docky_2.0_bzr1002-0karmic1dockycore1_amd64.deb

---

### Post by isaacj87 on 2009-12-27
> **Woody1987 said:**
> remove the ~ in the filename. So docky_2.0_bzr1002-0karmic1~dockycore1_amd64.deb becomes docky_2.0_bzr1002-0karmic1dockycore1_amd64.deb

I've already tried that. It doesn't have anything to do with the actual filename of the deb, but the control file in the deb.

Any other suggestions?

---

### Post by isaacj87 on 2009-12-27
Well, I solved my own problem. I downloaded the source file off of the Docky launchpad site and created a deb. Then took that deb and created an RPM. It bit of work, but it works.

If anybody would like a copy of the rpm, I'll happily share it. I'm running KDE 4.4 b2 on OpenSUSE 11.2 so it's hard for me to find a package Docky.

---

