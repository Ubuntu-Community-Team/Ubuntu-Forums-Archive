---
title: "Document Viewer is not Responding"
date: 2011-01-13
forum: General Help
---

### Post by surajit697 on 2011-01-13
I am using UBUNTU 10.10 on my desktop and it is running quite well. But I  got a problem from last few days. Document Viewer is not responding at  all. When I click to open a .pdf file, it shows nothing without a  loading icon on the right hand top corner. I have waited a long, but it  did not seem to change. Today I have removed document viewer using  ubuntu software center and reinstalled it, but the problem exist.
What should I do?

---

### Post by acplusplusprogrammer on 2011-01-13
Open the terminal and try:

sudo apt-get check
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoclean
sudo apt-get autoremove

restart the PC and see what happens

---

### Post by surajit697 on 2011-01-13
Thank you.
The problem is solved.

---

