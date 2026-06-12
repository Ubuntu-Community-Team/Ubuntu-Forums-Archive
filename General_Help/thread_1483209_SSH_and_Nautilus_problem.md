---
title: "SSH and Nautilus problem"
date: 2010-05-14
forum: General Help
---

### Post by Sanus Compleo on 2010-05-14
So I was using nautilus to access an ssh server, all was going well and fine, but I decided that I wanted to log in automatically.  Well... there was a problem with that.  Whenever I try to access the ssh now, it sends the wrong username, and a blank password, which gets me sitebanned for about two days.  Where can I change this behavior?

---

### Post by HiImTye on 2010-05-14
how are you connecting to the remote computer

edit: I realize nautilus but are you using for instance, the bookmarks pane on the left?

---

### Post by Sanus Compleo on 2010-05-14
Typing in the ssh:// address, and the port in the basic "File opener"'s location bar.

---

### Post by HiImTye on 2010-05-14
ok, instead of that, do
```
ssh://username:password@host/directory
```

---

### Post by Sanus Compleo on 2010-05-14
It asked me for the password a second time... I won't be able to find out if it worked or not until the admin gets in.

---

### Post by Sanus Compleo on 2010-05-14
Woo.  So that didn't work.  Am sitebanned for 48 hours again.

---

### Post by Sanus Compleo on 2010-05-14
gconf-editor provides no further insight to fixing nautilus' send silly data issue.

---

### Post by Neezer on 2010-05-14
Sanus,

I have had great luck in using the Places menu to connect to my ssh server.

Just go to Places -> Connect to Server and a dialog page will open up. You can specify a port if you aren't on the default port 22 for ssh. You can also put a username in. It can even remember you password for you. Then you can save a bookmark for that connection and it will show up in the "Places" menu as whatever you name it so that you don't have to put in the connection information each time you connect.

[img]http://news.cnet.com/i/bto/20080708/ubuntu.places2.jpg[/img]

---

