---
title: "Login screen does not appear. I cannot log in anymore"
date: 2011-03-24
forum: General Help
---

### Post by Lucius123 on 2011-03-24
Hi,  since yesterday, I encounter a big problem in Ubuntu 10.04. So far I could not find any solution in the Internet for my problem. I hope anybody of you know any solution for my problem.

Since yesterday, Ubuntu boots into X-Windows. The violett background is there and also the mouse cursor. However, there is no login window, anymore. There is no possibility to login.

If I change to a console via Ctrl-Alt-F1, I see some error messages that likely cause the problem:[INDENT]mountall: Plymouth-Befehl fehlgeschlagen (command did not work)
[/INDENT][INDENT]mountall: Keine Verbindung zu Plymouth (no connection to Plymouth)
[/INDENT][INDENT]init: plymouth-splash main process (822) terminated with status 2
[/INDENT][INDENT]init: plymouth main process (344) killed by SEGV signal
[/INDENT][INDENT]/dev/sda7: ... (2.1% nicht zusammenhängend)... (not continous)
[/INDENT][INDENT]init: ureadahead-other main process (894 ) terminated with status 4 ...
[/INDENT][INDENT]init: ureadahead-other main process (900) terminated with status 4
[/INDENT][INDENT]init: plymouth-log main process (917) terminated with status 1 ....
[/INDENT]I already tried something, but so far I was not succesful. I reinstalled plymouth, ureadahead and gdm. 

There could be a reason why my system does not work anymore. Yesterday, my root directory filled up to only 50MB free space. Now there is again 5GB. Maybe this has caused the problem?!

Thank you very much in advance! Lucius123

---

### Post by Lucius123 on 2011-03-26
Hi, today, I was able to solve the problem described above. The cause was indeed that the root partition was full for a few seconds resulting in IO-errors. Especially, important XWindows-relevant files were corrupted, which I could see in .Xerrors in the home folder.


Solution:
First, I had to reinstall Plymouth and reconfigure it via:
sudo update-alternatives –config default.plymouth


GDM was still broken, hence I needed to install KDM which worked fine. However, Gnome was also broken. E.g. there was no panel.


The ultimate solution was to upgrade the entire system to Ubuntu 10.10 by typing 

 sudo  do-release-upgrade in the terminal.


After that, everything worked fine again.

---

### Post by linuxuser12345 on 2011-03-26
...

---

