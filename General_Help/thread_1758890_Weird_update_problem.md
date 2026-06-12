---
title: "Weird update problem"
date: 2011-05-15
forum: General Help
---

### Post by Condor Cluster on 2011-05-15
Just ran update, and it automatically installed an acroread package (9.4.2 60.5Mb). Thing is I removed acroread in favour of foxit a while back.


Why would I receive updates for programs I no longer have installed?

---

### Post by TeoBigusGeekus on 2011-05-15
You have to disable/delete the repository as well.
Look in Administration>System>Software sources or, if you prefer to do it manually, edit the /etc/apt/sources.list file.

---

### Post by jerrrys on 2011-05-16
is acroread really removed?  open a terminal and enter [B]locate acroread
[/B]
or another way is [**deborphan**]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=deborphan&as_qdr=all&sa=Google+Search&lang=en#881")

be careful what you remove, you can really bork your system.  good idea to do some reading first

another way is with the purge command and don't know why this posted twice

[http://ubuntuforums.org/showthread.php?t=1145173](http://ubuntuforums.org/showthread.php?t=1145173)

---

### Post by jerrrys on 2011-05-16
is acroread really removed?  open a terminal and enter [B]locate acroread
[/B]
or another way is [**deborphan**]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=deborphan&as_qdr=all&sa=Google+Search&lang=en#881")

be careful what you remove, you can really bork your system.  good idea to do some reading first

---

