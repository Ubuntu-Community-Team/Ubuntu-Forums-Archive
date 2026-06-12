---
title: "weird character when install app"
date: 2012-06-15
forum: General Help
---

### Post by redtea20 on 2012-06-15
Hi,

I installed Ubuntu 12.04 from CD, with default setup. Here is the strange problem.

When I install an application, some weird characters appear. Could this be font problem? Which font is missing? Sorry, I am new in Ubuntu and learning.

lzhao-linux:/home/lzhao/Downloads/Komodo-IDE-7.0.2-70257-linux-x86_64> ./install.sh -I ~/Komodo-IDE-702/
./INSTALLDIR/lib/python/bin/python: 1: ./INSTALLDIR/lib/python/bin/python: &#65533;: not found         
./INSTALLDIR/lib/python/bin/python: 1: ./INSTALLDIR/lib/python/bin/python: : not found          
./INSTALLDIR/lib/python/bin/python: 1: ./INSTALLDIR/lib/python/bin/python: &#65533;@@: not found       
./INSTALLDIR/lib/python/bin/python: 1: ./INSTALLDIR/lib/python/bin/python: CE&#65533;&#65533;                 
                                                                               :&#65533;               
                                                                                 2b&#65533;&#65533;&#65533;K&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;qXj&#65533;: not found
./INSTALLDIR/lib/python/bin/python: 1: ./INSTALLDIR/lib/python/bin/python: &#65533;&#65533;&#65533;                  
                                                                              &#65533;&#65533;&#65533;&#65533;&#65533;: not found  
./INSTALLDIR/lib/python/bin/python: 1: ./INSTALLDIR/lib/python/bin/python: &#65533;8=                  
                                                                              &#65533;&#65533;                
                                                                                : not found                                
./INSTALLDIR/lib/python/bin/python: 1: ./INSTALLDIR/lib/python/bin/python: &#65533;&#65533;&#65533;&#65533;
                                                                               : not found
./INSTALLDIR/lib/python/bin/python: 1: ./INSTALLDIR/lib/python/bin/python: &#65533;
                                                                            : not found
./INSTALLDIR/lib/python/bin/python: 1: ./INSTALLDIR/lib/python/bin/python: ELF: not found
./INSTALLDIR/lib/python/bin/python: 1: ./INSTALLDIR/lib/python/bin/python: &#65533;
                                                                            : not found
./INSTALLDIR/lib/python/bin/python: 1: ./INSTALLDIR/lib/python/bin/python: H&#65533;&#65533;s&#65533;&#65533;&#65533;&#65533;H&#65533;&#65533;&#65533;5&#65533;: not found
./INSTALLDIR/lib/python/bin/python: 1: ./INSTALLDIR/lib/python/bin/python: H&#65533;&#65533;H&#65533;X&#65533;H&#65533;: not found
./INSTALLDIR/lib/python/bin/python: 1: ./INSTALLDIR/lib/python/bin/python: I&#65533;&#65533;&#65533;A&#65533;&#65533;&#65533;Ð&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;L&#65533;d$&#65533;L&#65533;l$&#65533;L&#65533;%s: not found

> uname -a
Linux ..... 3.2.18 #1 SMP Thu May 31 19:19:02 PDT 2012 i686 i686 i386 GNU/Linux

graphic card
2:00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)


This has happened to another app. When I open that app, the text are full of strange characters.

Thanks
Larry

---

### Post by David Andersson on 2012-06-15
> **redtea20 said:**
> 
I installed Ubuntu 12.04 from CD, with default setup. Here is the strange problem.

When I install an application, some weird characters appear. Could this be font problem? Which font is missing?

...

This has happened to another app. When I open that app, the text are full of strange characters.


The install script use a python interpreter that is packaged with Komodo. It seems your system thinks the python interpreter (a compiled program) is a script (maybe python text). I do not think it is a font problem.

What is your locale?
```
locale
```

Can you run the python packaged with Komodo?
```
./INSTALLDIR/lib/python/bin/python
quit()
```
It should output
> Python 2.6.5 (r265:79063, Apr 16 2010, 14:15:55) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 

Remove the ~/Komodo-IDE-702 directory and try again with this command. (It will use unix standard locale)
```
rm -r ~/Komodo-IDE-702
LC_ALL=C LANG=C LANGUAGE=C ./install.sh -I ~/Komodo-IDE-702/
```

---

### Post by redtea20 on 2012-06-18
Thanks David, I used another Komodo version, the problem magically gone. I don't know what's going on.

---

