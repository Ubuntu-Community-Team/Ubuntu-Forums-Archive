---
title: "Can't open the top folders under the places menu, desktop folder not shown"
date: 2011-11-10
forum: General Help
---

### Post by nokia2mon2 on 2011-11-10
hi
after i installed my second ATI radeon 6990 and made reboot:
1- all my gpu is shown normally. thats good
-----------
pyrit list_cores
Pyrit 0.4.1-dev (svn r308) (C) 2008-2011 Lukas Lueg [http://pyrit.googlecode.com](http://pyrit.googlecode.com)
This code is distributed under the GNU General Public License v3+

The following cores seem available...
#1:  'CAL++ Device #1 'AMD CAYMAN''
#2:  'CAL++ Device #2 'AMD CAYMAN''
#3:  'CAL++ Device #3 'AMD CAYMAN''
#4:  'CAL++ Device #4 'AMD CAYMAN''
#5:  'CPU-Core (SSE2/AES)'
#6:  'CPU-Core (SSE2/AES)'
#7:  'CPU-Core (SSE2/AES)'
#8:  'CPU-Core (SSE2/AES)'

the way i do it:
1. 1- Open up /home/username/.bashrc and add export DISPLAY=:0 2. 2- Open up a command prompt and run sudo aticonfig --adapter=all --initial -f
3- reboot 

-------------------------
2- all folders and files was disappeared from the desktop, i even cant use right click on the desktop.

3- all folders under places cant be open, its show down in the down panel for a seconds then its disappeared

4- the command line and firefox work normally, when i typed nautilus, i got this

----------------
(nautilus:4117): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

(nautilus:4117): Unique-DBus-WARNING **: Error while sending message: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
--------------------

i need your help please, and if any one have time to  fix that with me on the msn and teamviwer and teach me what was the wrong and give me answers about some basics i will pay for him. just send to me your msn info

help guys :( and sorry about my bad english
------
note: i used backtrack 5r - 64 bit

---

