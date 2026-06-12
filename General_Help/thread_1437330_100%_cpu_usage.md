---
title: "100% cpu usage"
date: 2010-03-23
forum: General Help
---

### Post by BlueEyedTree on 2010-03-23
I currently have a Q9650 in my computer. 2 out of the 4 cores are stuck at 100%. I ran the "top". The following commands were shown to be using all the cpu. This is what the command shows.
         (user)                                                                                        (cpu usage)            (process)
 2359 boinc     39  19  191m 186m 1228 R  101  4.6 182:03.48 einstein_S5GCE_    
 2044 boinc     39  19  178m 173m 1228 R   99  4.3 404:18.44  einstein_S5GCE_




Im wondering what this boinc command is. And what this einstein command is.... as well as how i can stop it.

---

### Post by l.billon on 2010-03-23
HI!
Boinc uses the non-used CPU cycles for science!

[http://fr.wikipedia.org/wiki/Berkeley_Open_Infrastructure_for_Network_Computing]("http://www.google.fr/url?q=http://fr.wikipedia.org/wiki/Berkeley_Open_Infrastructure_for_Network_Computing")

---

### Post by Revolutionary101 on 2010-03-23
The BOINC command is something from the cloud computing program BOINC ([http://boinc.berkeley.edu/](http://boinc.berkeley.edu/)). You might have installed it and it is using unneeded resources. If you want to remove it type this into terminal:

```
sudo apt-get remove boinc
```

Also you may be able to modify the preferences so it uses less or it doesn't use any while you are using the computer.

---

