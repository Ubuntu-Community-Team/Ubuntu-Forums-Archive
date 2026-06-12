---
title: "VSFTP + pam htpasswd + virtual users = &quot;500 OOPS: cannot locate user entry:&quot;"
date: 2011-02-01
forum: General Help
---

### Post by IndieRockSteve on 2011-02-01
I followed the directions here:
[http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/](http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/)

but now I get 
```
500 OOPS: cannot locate user entry:music
Login failed.

```

I see no errors in my auth.log, and in my vsftpd.log I see
Tue Feb  1 13:01:13 2011 [pid 2] CONNECT: Client "<omitted_ip>"
Tue Feb  1 13:01:20 2011 [pid 1] [<username>] OK LOGIN: Client "<omitted_ip>"

so it looks like the user is able to log in, but I can't tell what the issue is beyond that.

Anyone have an idea of whats causing this?

---

### Post by sychare on 2011-02-15
After following the same guide I'm hitting this issue too. Nobody has any ideas where to look?

---

### Post by squeeb on 2011-08-30
I also have this issue.

---

### Post by danutak on 2011-10-21
Make sure, that in vsftp.conf file you have this line:

```
guest_enable=YES
```

---

### Post by mlerley on 2011-12-09
YES! Thank you.  guest_enable it is. I swear it used to work though... weird.

---

