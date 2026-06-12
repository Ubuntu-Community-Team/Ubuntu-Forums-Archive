---
title: "Tightvnc and KDE problem, grey desktop help!"
date: 2006-03-15
forum: General Help
---

### Post by joeca0304 on 2006-03-15
I've been searching the forums and I've found a few people who have had this problem.  I even found an old howto that had me change my xstartup to show this line

/usr/bin/startkde -geometry 80x24+10+10

anyway nothing has worked.

I startup my vncserver and it's fine.  When i vnc in from another desktop all i get is the gray desktop and an X for a mouse cursor.  I guess it's not starting kde correctly.  What do I need to do to fix this?

---

### Post by incubus on 2006-03-15
There's a conf file that you may need to edit:
/etc/vnc.conf

I would try to uncomment this line:
$vncUserDir = "$ENV{HOME}/.vnc";

If it still doesn't work, copy that file into your home directory as ".vncrc".

incubus

---

### Post by fakey1223 on 2006-03-26
I fixed the problem with the gray vnc screen and x cursor by going to Login Screen Setup->Security->Enable XDMCP.

---

