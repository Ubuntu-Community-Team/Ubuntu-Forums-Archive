---
title: "Cannot remove wine"
date: 2006-05-07
forum: General Help
---

### Post by Blutack on 2006-05-07
Heyho, back when I was (even more of) a nube I compiled wine 9.6 and then later 9.10 without removing 9.6.  Even more stupidly I appear to have removed the original folder with the makefile in it.  I now get errors about wine server mismatches...I just want to get rid and apt-get it instead.  (Wish I'd known about checkinstall back then..)
3 questions then..
Is a copy of the folder with the makefile in it copied somewhere other than the home on install?  If so I can just cd to that and run make clean, yes?
If not if I compile and install a newer version of wine and then make clean that will it remove the 2 previous?
Finally if all else fails can I recompile 9.6 and 9.10 and instead of running make install after make just run make clean?
many thanks

---

### Post by louis_nichols on 2006-05-07
well... installing a deb of a certain version and uninstalling it later is unfortunatelly not a guarantee to remove all files belonging to previous versions.

Fortunatelly, though, to uninstall a make-install-ed package, all you need is to do is re-extract the source tarball, then run ./configure and then make uninstall (make clean is a different thing), without make before that - so you're avoiding compilation. Fingers crossed there, as not all makefiles have the uninstall option.

Hope it works for you. Good Luck!

---

### Post by Blutack on 2006-05-08
Excellent!Wine does have a make uninstall script.
Thanks

---

### Post by louis_nichols on 2006-05-08
[QUOTE=Blutack]Excellent!Wine does have a make uninstall script.
Thanks[/QUOTE]

Glad to hear it! Does it do the trick? Are you able to install a deb and have it work as it should? I'm curious...

---

### Post by Blutack on 2006-05-18
Eeek!  I now cannot remember what versions of wine I compiled!  Is there an easy way to check?  This what I did.
```

blutack@icebox:~$ wine --version
Wine 0.9.9

```
If I then try and run a windows program (i.e switch)  and then type
```

blutack@icebox:~$ wine --version
wine client error:b: version mismatch 188/229.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

```
How can I find the version of the wineserver?
I am also compiling cedega source at the moment, but I won't checkinstall until I've shifted off all the other wines.  Any ideas?  Sorry about the time I've taken to get back to you but I'm trying not to use my comp to much.  Linux is more addictive than crack.

---

### Post by louis_nichols on 2006-05-18
[QUOTE=Blutack]
 Linux is more addictive than crack.[/QUOTE]
 Oh, boy! Do I know what you mean with that one!!! ](*,)  I just can't get away from it! And to think of all the things (some of them extremely important) I should be oing instead... :)

So, about your problem, there is this:

```
myself@home:~$ wineserver -v
Wine 0.9.9

```

Hope it helps. Although I must confess that if indeed you get out of this command something different from what wine --version shows, I don't know what might be done.

Did you first uninstall the wine compiled package and then installed the deb? Or did you install the deb on top of the compiled package, and then ran the uninstall script?

---

### Post by Blutack on 2006-05-23
I didn't install a deb at all.  I compiled and installed one version and a program didn't work, so I compiled and installed a newer version.  (Don't question my logic, it seemed a good idea at the time).  I had a kinda wooly hope it would upgrade the existing one.  What I really want to do is remove both compiled versons completely and install a deb package instead, as I'm trying to move away from source installs (too difficult to remove...).
I've done wine -v and it comes out with wine 0.9.9.  I then run a wine program, and if after a run wine -v I get a version mismatch error.
If you don't use it checkinstall is awesome by the way.
Many Thanks
Blutack

---

### Post by louis_nichols on 2006-05-25
[QUOTE=Blutack]I didn't install a deb at all.  I compiled and installed one version and a program didn't work, so I compiled and installed a newer version.  (Don't question my logic, it seemed a good idea at the time).  I had a kinda wooly hope it would upgrade the existing one.  What I really want to do is remove both compiled versons completely and install a deb package instead, as I'm trying to move away from source installs (too difficult to remove...).
I've done wine -v and it comes out with wine 0.9.9.  I then run a wine program, and if after a run wine -v I get a version mismatch error.
If you don't use it checkinstall is awesome by the way.
Many Thanks
Blutack[/QUOTE]

well... here's an idea: reinstall both versions via make+make-install, then uninstall each of them via make uninstall (I guess you don't need any particular order of doing things here). It might look a little like shooting birds with a canon, but this way you're guaranteed to have a wine-files-free system at the end. so you can start fresh with a deb.

---

### Post by Blutack on 2006-06-04
The plot thickens...made and uninstalled wine 0.9.9 successfully.  Now when I do wine --v I get 20050725...I don't even remember installing that.  Will download and remove.  Wonder how many there are..
Many thanks

---

### Post by Blutack on 2006-06-06
Update - wine 20050725 is not available anywhere!  It was also not installed as a package.  Its rather mysterious actually, as in 2005 I was still growling at XP...

---

