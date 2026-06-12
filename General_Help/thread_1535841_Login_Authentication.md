---
title: "Login Authentication"
date: 2010-07-21
forum: General Help
---

### Post by linux1534 on 2010-07-21
Hello.


Can I change how many times I can try to login into ubuntu before it disconnects me, get a waiting time or simply retry?

Both for being on the system itself, behind it, and from openssl? It was the only option I couldn't find in the sshd.conf.


I often forget my password. :)



Thanks.

---

### Post by deathadder on 2010-07-21
That's a forum wide setting so nope. Have you thought about storing you passwords within a password manager like gpass or Revelation?

---

### Post by kaelspencer on 2010-07-21
> **deathadder said:**
> That's a forum wide setting so nope. Have you thought about storing you passwords within a password manager like gpass or Revelation?

I think he is referring to his OS, not the forums.

linux1534, I think you would be able to adjust it using this:
[http://manpages.ubuntu.com/manpages/lucid/man8/pam_tally.8.html]("http://manpages.ubuntu.com/manpages/lucid/man8/pam_tally.8.html")

---

### Post by deathadder on 2010-07-21
> **kaelspencer said:**
> I think he is referring to his OS, not the forums.

linux1534, I think you would be able to adjust it using this:
[http://manpages.ubuntu.com/manpages/lucid/man8/pam_tally.8.html]("http://manpages.ubuntu.com/manpages/lucid/man8/pam_tally.8.html")

:redface: how on earth did I manage to read that wrongly!

---

### Post by linux1534 on 2010-07-21
Thanks kaelspencer. It seems kinda complex though.

Isn't it just possible to remove the login "checker" or whatever and just have no limit to allowed logins?


@deathadder, yea but I don't like password managers, They get messy over time.

---

