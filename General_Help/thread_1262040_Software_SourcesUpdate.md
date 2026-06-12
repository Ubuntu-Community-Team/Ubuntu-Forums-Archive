---
title: "Software Sources/Update"
date: 2009-09-08
forum: General Help
---

### Post by RealG187 on 2009-09-08
I have a question. So if I goto "System --> Administration --> Software Sources" and then close it and it asks me to renew my software sources, does that have the same effect as "sudo aptitude update"

Becuase if I am using a [local repository]("http://bestwikiever.wikidot.com/ubuntu:local-repository") and put new files in (Right now I am using "/home/mpg/rep" and the source, and it's a symlink so I can use any folder, but if I make it sym link somewhere else I have to refresh and I currently use "Software Sources" to do that, could I do it from the terminal if I used "sudo aptitude update"?

---

### Post by Joeb454 on 2009-09-09
From what I'm aware - refresh software sources is the same as sudo apt-get update from a terminal :)

So to answer your question simply - yes, you can do it from the terminal if you want

---

### Post by RealG187 on 2009-09-09
I thought so, when I did the intructions in [your thread]("http://ubuntuforums.org/showthread.php?t=785263"), I skipped that part because I was sure I just did it, but it's good to know I can do it the other way around too, before I would have to goto software sources and uncheck and check something (to change my sources so it asks me to refresh) and close it, but it's good to know I can use that command, since I would be in the terminal anyways to type in "apt-get install"

[http://ubuntuforums.org/showthread.php?t=1261519](http://ubuntuforums.org/showthread.php?t=1261519)

---

