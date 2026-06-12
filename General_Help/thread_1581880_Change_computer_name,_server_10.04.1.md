---
title: "Change computer name, server 10.04.1"
date: 2010-09-25
forum: General Help
---

### Post by Cool Javelin on 2010-09-25
I just installed from scratch Ubuntu server 10.04.1, and goofed when I typed in the computer name.

Can someone tell me what file(s) I need to fix to change the computer name?

How does this affect Samba or other stuff? Is there more then one file to change (password files, networking files?)

I note in smb.conf, the "server string" (is this the comment stuff?) that gets sent out to other computers is %h. I assume this will automatically change when the name gets changed somewhere else.

Thanks for your help

Mark.

---

### Post by gzarkadas on 2010-09-25
See [this HowTo thread]("http://ubuntuforums.org/showthread.php?t=774029") and in particular the OP's first post and them my post,  [#18]("http://ubuntuforums.org/showpost.php?p=9452050&postcount=18"), in there.

---

### Post by Cool Javelin on 2010-09-26
Thanks gzarkadas, exactly what I needed.   :P

---

