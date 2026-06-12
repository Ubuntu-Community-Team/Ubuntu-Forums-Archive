---
title: "Remote Desktop Viewer"
date: 2012-04-01
forum: General Help
---

### Post by carmenin87 on 2012-04-01
I use Remote Desktop Viewer to connect from one Ubuntu machine (master) to another (slave).

In order for me to connect into the slave machine, I have to be logged on.  If I log off for whatever reason, I am unable to remote in until I am logged in with an ID.

Is there any way to remote into an Ubuntu machine while it is still at the log on screen?

Thank you

---

### Post by Ms. Daisy on 2012-04-02
Welcome to the forums.
 
I'm not clear on what you want.  You want to connect your local Ubuntu computer to a remote Ubuntu computer without logging into your local machine?

---

### Post by HiImTye on 2012-04-03
you can use ssh for this task and 'ssh -X' lets you view X windows over ssh

---

### Post by carmenin87 on 2012-04-03
Actually, I've sorted it out.

I just had to set the slave machine to auto login and everything now works.

---

### Post by sammiev on 2012-04-03
I hope you are doing this on the local network and not on the Internet. Over the Internet I would really suggest using SSH.

---

