---
title: "Does EnvyNG work in Karmic x64? I get errors upon launch."
date: 2009-12-29
forum: General Help
---

### Post by martini1179 on 2009-12-29
I was just wondering if EnvyNG is still being actively maintained. I ask because it's giving me errors when I try to start it in Karmic x64. If I try to start the QT, I get: 

Traceback (most recent call last):
  File "/usr/share/envyng-qt/envyngqt.py", line 886, in <module>
    form = EnvyMainDlg()
  File "/usr/share/envyng-qt/envyngqt.py", line 329, in __init__
    self.updateTreeModel()
  File "/usr/share/envyng-qt/envyngqt.py", line 381, in updateTreeModel
    i.setText(0, candidate)
TypeError: argument 2 of QTreeWidgetItem.setText() has an invalid type


When I try to launch the textual interface, I get: 

Traceback (most recent call last):
  File "interface.py", line 432, in <module>
    a.mainMenu()
  File "interface.py", line 295, in mainMenu
    a.driverMenu('nvidia')
  File "interface.py", line 322, in driverMenu
    self.driverPage(driver)
  File "interface.py", line 216, in driverPage
    candidateLen.append(len(details['candidate']))
TypeError: object of type 'NoneType' has no len()

---

### Post by martini1179 on 2009-12-30
/bump

---

### Post by Mark Phelps on 2009-12-30
Maybe the launchpad bug writeup linked below answers your question:

[http://https://bugs.launchpad.net/ubuntu/+source/envyng-core/+bug/396301]("https://bugs.launchpad.net/ubuntu/+source/envyng-core/+bug/396301")

---

