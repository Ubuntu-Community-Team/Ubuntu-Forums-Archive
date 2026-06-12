---
title: "installed 10.10 software center and other things wont open"
date: 2011-02-02
forum: General Help
---

### Post by ima92 on 2011-02-02
hello, im still quite new into linux, I installed ubuntu 10.10 today on an old computer i had, but here seems to be some weird problem, software center, additional drivers, and updates wont open :S

with software center this is what terminal returns when i type gksudo software-center (I readed thats the command to open it from terminal):

Traceback (most recent call last):  File "/usr/bin/software-center", line 88, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 37, in <module>
    from softwarecenter.db.application import Application, DebFileApplication
  File "/usr/share/software-center/softwarecenter/db/application.py", line 19, in <module>
    from apt.debfile import DebPackage
  File "/usr/lib/python2.6/dist-packages/apt/__init__.py", line 24, in <module>
    from apt.package import Package
ImportError: cannot import name Package

in the case of software-center it looks like if the program was starting but then nothing happens..


now about additional drivers and updates, i dont know whats the command to open them :oops: so if somebody was so kind to tell me i'll gladly copy what the terminal returns..

---

