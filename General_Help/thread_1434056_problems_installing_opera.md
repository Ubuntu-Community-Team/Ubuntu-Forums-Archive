---
title: "problems installing opera"
date: 2010-03-19
forum: General Help
---

### Post by cody on 2010-03-19
So, i've just installed ubuntu and wanted to give it a go. However trying to download and installing my favorite browser i get an error: Error: Dependency is not satisfiable: libqt3-mt (>= 3.3.4)   im downloading the default package, and ran the package install thingy. 

i googled around trying to find a solution, but i found mostly for older versions of ubuntu and dont know if they apply to my problem. I also tried some tips i found running a command with something like sudo apt-get install libqt3-mt. then i end up with this response: 
E: Couldn't find package libqt3-mt

any help apreciated :)

---

### Post by UCSBGauchosRock on 2010-03-19
It is possibly missing software sources. Here is what to do:

1.Open Synaptic Package Manager-->Settings-->Repositories or... Menu-->System-->Administration-->Software Sources.
2.Check every box and every repository.
3.Close and hit Reload.
4.Try Installing Opera again.

---

