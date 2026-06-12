---
title: "Auto-login with ssh+svn?"
date: 2009-08-24
forum: General Help
---

### Post by somethingkindawierd on 2009-08-24
I have an svn that I access with a url like ssh+svn... and I am always asked for my password with every commit. Is there a way to store the password somehow so I do not need to log in every time?

Thanks!

---

### Post by Brandon Williams on 2009-08-24
If you have direct shell access to the svn system, you should be able to set yourself up for key-based authentication. That way, if you load your key in your local ssh-agent, you'll be able to connect to svn without entering a password every time.

---

### Post by bodhi.zazen on 2009-08-24
There are other fun things you can do with keys =)

[http://blog.bodhizazen.net/linux/svnssh/](http://blog.bodhizazen.net/linux/svnssh/)

You could probably make a key without a password, not sure if it would go automatically or if you would need to hit the enter key anyway.

+1 for ssh-add

Last, it you use a service such as denyhosts or rules in iptables, take care as each time you initiate a new file these tools see it as a new connection and you can get locked out of your server, not that that has *ever* happened to me =)

---

