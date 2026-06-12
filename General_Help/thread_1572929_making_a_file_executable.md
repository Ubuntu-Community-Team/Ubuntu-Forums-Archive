---
title: "making a file executable"
date: 2010-09-11
forum: General Help
---

### Post by emanresu on 2010-09-11
i installed "littler" from Synaptic. it's a front end for R, for those curious. it's not in my start menu. i searched for the app and don't know where it is. assuming i can find it, how do i set things up so that i can run it from a listing in the start menu? sorry to be so basic, but i mean from locating this app to getting it to start to making it available in the start menu, how would i do this, please?

---

### Post by mowglinz on 2010-09-12
I'm not familiar with R or littler however aptitude lists it as a command line interface.
```
$ apt-cache search littler
littler - GNU R scripting and command-line front-end
r-cran-getopt - GNU R package providing command-line parsing functionality
```I expect you'll need to run it inside a terminal (Applications -> Accessories -> Terminal)
The manual page for R can be found [here]("http://manpages.ubuntu.com/manpages/lucid/man1/r.1.html").

More generally if you've installed something and can't find the executable you should use the 'which' command in a terminal.
```
$ which gnome-terminal
/usr/bin/gnome-terminal
```If you want to make a file you own executable then use the 'chmod' command in a terminal.
```
$ chmod +x myfile
```

---

