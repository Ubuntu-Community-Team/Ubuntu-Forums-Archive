---
title: "QT Upgrade and Environment Variables"
date: 2006-03-30
forum: General Help
---

### Post by ep_ on 2006-03-30
I have Breezy, QT version 4.0 is already installed. Need to upgrade, hence  I downloaded the QT 4.1.2 source tar ball from the kind folks at Trolltech.  No errors on the build, it installed  into /usr/local/Trolltech/Qt-4.1.2

2 questions. Per the instructions I need to extend the environment varibles in the following manner.

      PATH=/usr/local/Trolltech/Qt-4.1.2/bin:$PATH
       export PATH

First question, how do I do this?  It does not look like it belongs in the bash.bashrc file as there is nothing in this file which looks similar and indicates the path of my already installed version 4.0

Also, unless you guys and gals advise against it,  I'd like to remove the old QT (seems like a waste).  IIRC, I installed the old version via apt-get.  Which of the following packages can I uninstall without screwing things up?  Or can I just delete the old directory?  Ya hoo!
[LIST]
[*]libqt4-core
[*]libqt4-debug
[*]libqt4-designer
[*]libqt4-dev
[*]libqt4-gui
[*]libqt4-qt3support
[*]libqt4-sql
[/LIST]

TIA -ep

---

### Post by ep_ on 2006-03-30
Sorry, I meant to post this in "programmer talk" if some moderator wants to move it.

---

