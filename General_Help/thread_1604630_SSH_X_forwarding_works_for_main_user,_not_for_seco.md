---
title: "SSH X forwarding works for main user, not for secondary user."
date: 2010-10-24
forum: General Help
---

### Post by Arancaytar on 2010-10-24
I can SSH to my own box using "ssh -X arancaytar@localhost" and run graphical applications. When I try the same using "ssh -X chris@localhost", I get an error message saying

```

chris@enki:~$ gedit

X11 connection rejected because of wrong authentication.

(gedit:16304): Gtk-WARNING **: cannot open display: localhost:11.0

```

In case this is relevant, there is an .Xauthority file in ~arancaytar/, but not in ~chris/. I have no idea how to create one though.

---

### Post by Arancaytar on 2010-10-25
Well, now it works for neither user; and the .Xauthority file is missing from both users.

---

### Post by kaspar_silas on 2010-10-25
If I log in to a computer without a .Xauthority file I get this message.


/usr/bin/X11/xauth:  creating new authority file /home/xxx/.Xauthority

I take it you don't get this message? If so have you tried running 
/usr/bin/X11/xauth to make the file.

---

### Post by Arancaytar on 2010-10-25
... wow. I have rarely read a man page as ridiculously dense as that of xauth.

Short story long; no, it doesn't create an .Xauthority file. It does, however, tell me it is using some kind of temporary authority file at /var/run/gdm/auth-for-arancaytar-dxxtZn/database, and then start a command prompt. The command prompt gives me the option to "add dpyname protoname hexkey".

---

### Post by kaspar_silas on 2010-10-27
Okay second go I found this link on how to create .Xauthority files.

[http://linux.die.net/man/1/mkxauth]("http://linux.die.net/man/1/mkxauth") 

As to the xauth man page well that is over my head. Maybe someone else can comment.

---

