---
title: "Using a graphic editor to edit a remote file"
date: 2010-05-30
forum: General Help
---

### Post by pwaugh on 2010-05-30
If I'm on my laptop.local logged in as "patrick" (a normal user), and I wish to edit a file owned by root on my server.local, currently I ssh in on patrick, then use $sudo vi /etc/some_file_owned_by_root to edit the file.

What if I want to use gedit or emacs or whatever graphical editor on my laptop (which is running the desktop version vs. server)?  How do I do this?

I can see the file in Nautilus, but of course can't just open it by right clicking as it is owned by root, not me.

patrick

---

### Post by juancarlospaco on 2010-05-30
*If the server dont have X you cant, without copying it locally...*

---

### Post by pwaugh on 2010-05-31
> **juancarlospaco said:**
> *If the server dont have X you cant, without copying it locally...*

So, given I installed the "server" version, and your response I presume X is not installed.

I thought the "x-server" is on the local computer (which would be my laptop) and the client is on the other (backwards from what one would normally expect).

patrick

---

### Post by marshmallow1304 on 2010-05-31
The easiest thing to do is probably to mount the ssh server's filesystem via sshfs (Places->Connect to Server, set service type to ssh and enter info.  Alternately, you can enter ssh://[user@]ip[:port] in the nautilus address bar.  Then you'll be able to open the remote filesystem and edit the files with local editors.

---

### Post by pwaugh on 2010-05-31
> **marshmallow1304 said:**
> The easiest thing to do is probably to mount the ssh server's filesystem via sshfs (Places->Connect to Server, set service type to ssh and enter info.  Alternately, you can enter ssh://[user@]ip[:port] in the nautilus address bar.  Then you'll be able to open the remote filesystem and edit the files with local editors.

I've done that, but I have to be root to edit root owned files on the server... I guess I can just become root on my laptop then edit them.  Thanks

After reviewing VI, I've remembered how to use it again.  Like riding a bike I guess, lol.

patrick

---

