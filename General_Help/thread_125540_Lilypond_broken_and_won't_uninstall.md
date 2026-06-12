---
title: "Lilypond broken and won't uninstall"
date: 2006-02-04
forum: General Help
---

### Post by Bongzilla on 2006-02-04
Hi

I installed lilypond to my Breezy, but something went wrong and the installation didn't work out and the program didn't work. At first I didn't think much about it and tried to uninstall what it was able to install, more precisely "lilypond-data". But if I open Synaptic and try to remove it first says that the changes were done succesfully. I press ok and this text comes up: "E: lilypond-data: Package is in a very bad inconsistent state - you should" As you can see the sentence kinda stops there, which is weird. There's just no more text to it. Then I press ok again and it gives me this: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. "

Well, ok. I open Terminal and put "sudo dpkg --configure -a" and it does it's thing. I open up Synaptic again and it still shows that lilypond-data is STILL INSTALLED!

Well, it would be a small problem, but when I try to uninstall or install something new (For example I tried to uninstall KDE as it wasn't really for me) it starts to do it, but before it goes with uninstalling KDE it still tries to do something with lilypond so this text comes up: "E: /var/cache/apt/archives/lilypond-data_2.6.3-9~breezy1_all.deb: subprocess new post-removal script returned error exit status 1"

I press ok and it aborts the whole thing, doesen't uninstall KDE either, and says "Failed to apply all changes! Scroll in the terminal buffer to see what went wrong"

I open the terminal buffer and this is what it says: 
"Preconfiguring packages ...
Selecting previously deselected package lilypond-data
(Reading database ... 90072 files and directories currently installed.)
Preparing to replace lilypond-data 2.6.3-9breezy1 (using .../lilypond_data.2.6
3-9breezy1_all.deb) ...
Unpacking replacement lilypond-data ...
/var/lib/dpkg/info/lilypond-data.postrm: line 23: /usr/bin/kpsewhich: No such fi
le or directory
dpkg: warning - old post-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or direct
ory
dpkg: error processing /var/cache/apt/archives/lilypond-data_2.6.3-9breezy1_all
.dep (--unpack):
 subprocess new post-removal script returned error exit status 1
/var/lib/dpkg/tmp.ci/postrm: line 23: /usr/bin/kpsewhich: No such file or direct
ory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status1"

I had to write all that by hand so there might be a typo or two. Don't be startled. As I couldn't copy the text from the terminal buffer.

I hope someon can help me! Really bugging me out!

Thanks

---

### Post by Bongzilla on 2006-02-04
*bump*

Can't anyone help me? This is freakin' me out.

---

### Post by Bongzilla on 2006-02-04
Oh, please. Anyone? Something? Anything? This is really cripling whole Linux for me. Can't install or remove anything because of this.

---

### Post by lamego on 2006-02-04
Did you opened a terminal and executed:
```
dpkg --configure -a
```
as shown on the error log ?

---

### Post by imrumpf on 2006-02-04
Same thing happened to me....the only solution I can suggest is backup data and completly reinstall Ubuntu, and in the future don't install lilypond till something gets fixed.

I tried lilypond with a live CD of Dapper flight 3 and it actually worked just fine. So I also suggest till 6.04 comes out.

---

### Post by cutOff on 2006-02-05
[QUOTE=Bongzilla]Oh, please. Anyone? Something? Anything? This is really cripling whole Linux for me. Can't install or remove anything because of this.[/QUOTE]
Read last post -> [http://www.ubuntuforums.org/showthread.php?p=705969#post705969](http://www.ubuntuforums.org/showthread.php?p=705969#post705969)

---

### Post by dragonfyre13 on 2006-02-06
[http://ubuntuforums.org/showthread.php?p=680286#post680286](http://ubuntuforums.org/showthread.php?p=680286#post680286)

I fixed it. you should be able to follow it pretty well.

---

