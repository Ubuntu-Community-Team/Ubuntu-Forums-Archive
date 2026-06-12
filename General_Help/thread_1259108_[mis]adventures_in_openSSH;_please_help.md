---
title: "[mis]adventures in openSSH; please help"
date: 2009-09-05
forum: General Help
---

### Post by oospill on 2009-09-05
hello. I've got a laptop (running ubuntu desektop) connecting to my wireless router.  I also have a desktop (running ubuntu server) plugged into the router.  great fun so far.  I successfully installed OpenSSH on both, and was able to connect my laptop to the server via ssh with my server destination ip as 192.168.1.3.  I used the default key names, and no password, and from what I understand that's a pretty safe connection.

here's the tricky part.  I set my router to forward port 22 to 192.168.1.3.  as quick as that, I can now connect to my server with my ip (what my ISP gives me).

I didn't make any new keys, and I didn't type any passwords, just 'ssh [my ip].  I answered 'yes' to continue, and it connected as if I just did it locally.

please tell me that my door isn't wide open!! it's connecting through the long route only because I got the keys already setup, right??

I hope that made sense, and I appreciate the help.  (still on my training wheels here.)

---

### Post by Vaphell on 2009-09-05
strange indeed
are both accounts the same with the same passwords? I don't know how ssh behaves exactly, but in my case when i ignore login in **ssh server_addr** my current session login is used as remote login. Why you didn't get password prompt is weird though. It should pop up.
Maybe you had some sudo and your session remembered password? It's a wild guess though, because i don't think sudoing would do that.

---

### Post by oospill on 2009-09-05
weird.  it's been about 30 minutes since I posted that question..  now, when I ssh to my (isp's) ip, OR to my (local) ip (192.168.1.3), they BOTH ask for my password.  I have the same user name on both systems.  and NO, I didn't specify a pass-phrase when making my keys.  arg! all this key stuff confuses me!!

oospill

---

