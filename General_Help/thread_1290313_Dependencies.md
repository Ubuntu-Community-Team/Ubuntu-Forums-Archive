---
title: "Dependencies"
date: 2009-10-13
forum: General Help
---

### Post by DonkeyDragon on 2009-10-13
After some time using Ubuntu I started wondering, where are all program dependencies located? And can programs look for dependencies elsewhere?

---

### Post by Intrepid Ibex on 2009-10-13
Well the dependencies are other packages/programs themselves =).

But e.g. if you install same-named package from somewhere else where it should be installed (usually the official repos), you might get errors regarding missing files.

Maybe someone is more enthusiast at explaining all this, though I'm really surprised at how many users move from windows to ubuntu - maybe it isn't so bad distro after all, even though I myself don't like it that much ;).

**E:** It might be helpful for you to know that in Windows world e.g. Direct-X is a dependency of Counter-Strike: Source ^^... just like Flash Player would be a "opt. (optional) dependency" for Mozilla Firefox.

---

### Post by Lars Noodén on 2009-10-13
Debian-based distros like Ubuntu use the APT package management system, just like Fedora derivatives use RPM.  Inside the [package](http://www.linuxplanet.com/linuxplanet/tutorials/6546/1/) is, obviously, the pieces of program itself and its configuration.  Also in the package is metadata, in the '[control file]("http://www.ibm.com/developerworks/linux/library/l-debpkg.html")' regarding the package's needs.

**apt-cache** with the option **depends** can look up in the package manager's database the control file for a package and tell you what it immediately depends on.  

```
$ apt-cache depends apache2
apache2
 |Depends: apache2-mpm-worker
 |Depends: apache2-mpm-prefork
 |Depends: apache2-mpm-event
  Depends: apache2-mpm-itk
  Depends: apache2.2-common
4 apt-cache depends wakeonlan
wakeonlan
  Depends: perl
  Depends: perl-modules
```

If you want the dependencies of the dependencies to the nth degree, then you can add '**--recurse**' to the mix:

```

$ apt-cache --recurse depends wakeonlan
wakeonlan                                         
  Depends: perl                                   
  Depends: perl-modules                           
perl-modules                                      
  Depends: perl                                   
  Conflicts: <libansicolor-perl>                  
  Conflicts: <libarchive-tar-perl>                
  Conflicts: <libattribute-handlers-perl>         
  Conflicts: libcgi-pm-perl                       
  Conflicts: <libcpan-plus-perl>                  
  Conflicts: <libcpanplus-perl>                   
  Conflicts: libextutils-cbuilder-perl            
  Conflicts: libextutils-parsexs-perl             
  Conflicts: libfile-temp-perl                    
  Conflicts: <libi18n-langtags-perl>              
  Conflicts: libio-zlib-perl                      
  Conflicts: <liblocale-codes-perl>               
  Conflicts: <liblocale-maketext-perl>            
  Conflicts: <liblocale-maketext-simple-perl>     
  Conflicts: <libmath-bigint-perl>                
  Conflicts: libmodule-build-perl                 
  Conflicts: libmodule-corelist-perl              
  Conflicts: libmodule-load-conditional-perl      
  Conflicts: <libmodule-load-perl>                
  Conflicts: libmodule-pluggable-perl             
  Conflicts: <libnet-perl>                        
  Conflicts: <libnet-ping-perl>                   
  Conflicts: <libparams-check-perl>               
  Conflicts: libpod-escapes-perl                  
  Conflicts: <libpod-parser-perl>                 
  Conflicts: libpod-simple-perl                   
  Conflicts: libtest-harness-perl                 
  Conflicts: libtest-simple-perl                  
  Conflicts: <libversion-perl>                    
  Conflicts: podlators-perl                       
  Replaces: <libansicolor-perl>                   
    perl-modules                                  
  Replaces: <libarchive-tar-perl>                 
    perl-modules                                  
  Replaces: <libattribute-handlers-perl>          
    perl-modules                                  
  Replaces: libcgi-pm-perl                        
    perl-modules                                  
  Replaces: <libcpan-plus-perl>                   
    perl-modules                                  
  Replaces: <libcpanplus-perl>                    
    perl-modules                                  
  Replaces: libextutils-cbuilder-perl             
    perl-modules
  Replaces: libextutils-parsexs-perl
    perl-modules
  Replaces: libfile-temp-perl
    perl-modules
  Replaces: <libi18n-langtags-perl>
    perl-modules
  Replaces: libio-zlib-perl
    perl-modules
  Replaces: <liblocale-codes-perl>
    perl-modules
  Replaces: <liblocale-maketext-perl>
    perl-modules
  Replaces: <liblocale-maketext-simple-perl>
    perl-modules
  Replaces: <libmath-bigint-perl>
    perl-modules
  Replaces: libmodule-build-perl
    perl-modules
  Replaces: libmodule-corelist-perl
    perl-modules
  Replaces: libmodule-load-conditional-perl
    perl-modules
  Replaces: <libmodule-load-perl>
    perl-modules
  Replaces: libmodule-pluggable-perl
    perl-modules
  Replaces: <libnet-perl>
    perl-modules
  Replaces: <libnet-ping-perl>
    perl-modules
  Replaces: <libparams-check-perl>
    perl-modules
  Replaces: libpod-escapes-perl
    perl-modules
  Replaces: <libpod-parser-perl>
    perl-modules
  Replaces: libpod-simple-perl
    perl-modules
  Replaces: libtest-harness-perl
    perl-modules
  Replaces: libtest-simple-perl
    perl-modules
  Replaces: <libversion-perl>
    perl-modules
  Replaces: podlators-perl
    perl-modules

```

Conversely, **rdepends** will tell you which packages depend on the package in question.

---

### Post by DonkeyDragon on 2009-10-13
Thanks, that helped quite a bit.

So next part.. Can I tell the program where to look for these dependencies, or is that already decided, when the program gets compiled?

Or is it on case by case basis?

For example, I found that most of the dependencies reside in /usr/lib due to the help of you two. Could I for example move some of the files in there, and then still have a given program find the files it needs?

I know it's not recommended, but as an example I could move some file from /usr/lib to /lib. Would there be some way of telling programs to look for that file in /lib instead of /usr/lib?

---

### Post by vinutux on 2009-10-13
> **DonkeyDragon said:**
> Thanks, that helped quite a bit.

So next part.. Can I tell the program where to look for these dependencies, or is that already decided, when the program gets compiled?

Or is it on case by case basis?

For example, I found that most of the dependencies reside in /usr/lib due to the help of you two. Could I for example move some of the files in there, and then still have a given program find the files it needs?

I know it's not recommended, but as an example I could move some file from /usr/lib to /lib. Would there be some way of telling programs to look for that file in /lib instead of /usr/lib?

[B][COLOR="Red"]
[http://en.wikipedia.org/wiki/Dependency_hell]("http://en.wikipedia.org/wiki/Dependency_hell")[/COLOR][/B]

---

### Post by DonkeyDragon on 2009-10-13
Yeah well, dependency hell is kind of what I want to avoid.

Right now I'm just experimenting with it. Currently running Ubuntu 9.04, and will be reinstalling tomorrow. So really, I don't mind ending up with a messed up system. I just want to try out how to handle it.

So, is it doable in Ubuntu, or is it just for OS's like Arch Linux, PC-BSD and such?

---

### Post by Lars Noodén on 2009-10-14
> **DonkeyDragon said:**
> Thanks, that helped quite a bit.

So next part.. Can I tell the program where to look for these dependencies, or is that already decided, when the program gets compiled?

Or is it on case by case basis?


It's decided as the package is made, which usually involved compilation.  
See various articles about using 'source packages' in Debian or Ubuntu. e.g.
[http://www.debian-administration.org/articles/20](http://www.debian-administration.org/articles/20)

Or building 

> **DonkeyDragon said:**
> 
For example, I found that most of the dependencies reside in /usr/lib due to the help of you two. Could I for example move some of the files in there, and then still have a given program find the files it needs?


No, almost certainly not.  The filesystem doesn't track the objects that way.  One thing that would become more complex is read-write-execute permissions.  

> **DonkeyDragon said:**
> 
I know it's not recommended, but as an example I could move some file from /usr/lib to /lib. Would there be some way of telling programs to look for that file in /lib instead of /usr/lib?

Recompile the program or re-build the package to do that.  When building, there are almost always options to put the resulting files in specific targets.  (see 'make' and 'gmake')

They're like bees, go to a point and return.  Move the target or the home, they're lost.  Not like spiders with a string to follow back.

---

