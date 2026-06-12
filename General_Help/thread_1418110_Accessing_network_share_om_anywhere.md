---
title: "Accessing network share om anywhere"
date: 2010-02-28
forum: General Help
---

### Post by ebp on 2010-02-28
Hi

At home i have setup samba share on my linux box, which mount as drives on my windows box. I would like to do this not only on my local network, is this possible?

---

### Post by Iowan on 2010-02-28
Other threads suggest Samba may not be the best protocol for sharing files across the Internet. 
Whatever format you choose, the serverwill need to be accessible - that ususally means port-forwarding from your router to the server. Unless your ISP issues you a static address, you will need a service like [no-ip.com]("http://www.no-ip.com/") or [dyndns.com]("https://www.dyndns.com/account/entrance/").

---

### Post by ebp on 2010-02-28
i already have setup a dynamic ip service, so that's set. Since samba isn't secure, is there any secure options?

---

### Post by Iowan on 2010-02-28
There's [vsftp]("http://ubuntuforums.org/showthread.php?t=218630") and [SSH]("https://help.ubuntu.com/community/SSH").

---

### Post by ebp on 2010-03-01
I've found a solution, i'm connection via sftp from the program expandrive and it works quite well. :)

---

### Post by Iowan on 2010-03-01
Congrats! Glad you found a solution...
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

