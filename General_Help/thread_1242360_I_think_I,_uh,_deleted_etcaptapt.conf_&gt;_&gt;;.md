---
title: "I think I, uh, deleted /etc/apt/apt.conf &gt;_&gt;;"
date: 2009-08-17
forum: General Help
---

### Post by Madfoot713 on 2009-08-17
ok, so I was trying to install Tor, and I followed the instructions [here]("http://www.christianschenk.org/blog/enhancing-your-privacy-further-with-squid-and-tor/"). After I added the line he told me to add to apt.conf, I ran the aptitude lines, and I got some sort of error telling me to run apt-get update. I did that, and I still got the error. I thought maybe I did something wrong, so I opened up apt.conf again... and it was blank this time T_T. ...is this bad? <_<

---

### Post by Brandon Williams on 2009-08-17
The document you linked to is for running tor on a debian system. [Here](https://help.ubuntu.com/community/TOR) is one about running it on an ubuntu system.

The indicated change to apt.conf in the document you linked to is for debian, and will most likely cause trouble on an ubuntu system. You do not want to use it.

On ubuntu, there is no apt.conf by default, so having an empty apt.conf should not be a problem for you.

---

### Post by Jago6060 on 2009-08-17
+1 for your thread title and possibly giving yourself a heart attack for almost removing your ability to download packages :popcorn:

---

