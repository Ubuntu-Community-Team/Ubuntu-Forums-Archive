---
title: "Server isnt serving anymore!"
date: 2010-06-06
forum: General Help
---

### Post by rugbert on 2010-06-06
I just go back into town and turned on my ubuntu server to listen to music but for some reason I cant connect to it. I tried to putty into it and I get connection refused, but I can ping it just fine. its also not serving the website I have set up on it.

I moved it over to my monitor and logged in psychically and it has an IP address but I dunno. I havent made any changes since I last used it last week.

Where should I start looking for answers?

---

### Post by tgalati4 on 2010-06-06
dmesg | tail -100

Look for errors.  Examine all files in /var/log.  Post snippets of anything that you don't understand.

---

### Post by nemilar on 2010-06-06
Probably sshd is not started.

```
/etc/init.d/sshd status
```

If it's not running, start it:

```
/etc/init.d/sshd start
```

"Connection refused" means that your computer responded, but said "no, go away."

---

### Post by jerome1232 on 2010-06-06
Might want to look at /var/log/auth to see why it's refusing you, do you run a software based firewall? Check it's logs too. Check that your services are starting up as they should when you turn the thing on. Do you run denyhosts or some other software that will block out ip's if they try connecting to much?

---

