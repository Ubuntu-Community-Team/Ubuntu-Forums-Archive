---
title: "Ubuntu 10.04: Acetoneiso Broken Packages Help"
date: 2011-03-03
forum: General Help
---

### Post by SexySara on 2011-03-03
Can not for the life of me get this working. Moreover, I can't find the right files without having to install dependencies on top of dependencies. Any suggestions?
```

~$ sudo apt-get install acetoneisoReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  acetoneiso: Depends: fuseiso but it is not installable
              Depends: libqt4-gui but it is not installable
              Depends: cdrdao but it is not installable
              Depends: p7zip-full but it is not installable
              Depends: gnupg-agent but it is not installable
              Depends: gnupg2 but it is not installable
              Depends: pinentry-qt4 but it is not installable
E: Broken packages
~$ 


```

---

### Post by iheartubuntu on 2011-03-03
Thats strange! Have you tried just installing it from the Ubuntu Software Center?

Ive always installed it from there and never had a problem. Not sure if it would make a diff, but maybe you need the Ubuntu Restricted Extras also installed?

---

### Post by SexySara on 2011-03-03
Yah I tried the Software center and I get the same error. I have the restricted extras installed as well. I think my repositories are all messed up. You know how to set my repositories to the default settings?

[SIZE=2]**EDIT:::**[/SIZE]
It was a repository issue, but I got everything resolved now :). [This Link]("http://ubuntuforums.org/showthread.php?t=1699512") is what was wrong. Everything is okay now.

---

