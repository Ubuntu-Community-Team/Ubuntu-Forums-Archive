---
title: "Terminal freezes when left Idle over SSH"
date: 2006-05-20
forum: General Help
---

### Post by Jimmy McPuddin on 2006-05-20
Hello Ubunters,

I am new to Ubuntu so my troubleshooting skills are poor if not lacking in themselves.

Basically, I wish to connect to many remote servers using SSH.  This works perfectly fine.  After I leave the connections idle (even thouhg I'm not idle on my computer), the ssh connections periodically freeze.  When I mean freeze, I mean I can't do anything on the SSH terminal.  The screen is still active but it is just not registering anymore keyboard commands.  Therefor, I usually have to restart or relogin.

Does anybody know if this is a specific problem with my computer / connection / ubuntu configuration?

This does not occur on my Windows computers that are on the same connection using SSH.

Thanks guys.
Jimmy

---

### Post by halfvolle melk on 2006-05-20
This might be because ssh times out after a while. Windows probably handles this differently.
[http://www.openssh.com/faq.html#2.12](http://www.openssh.com/faq.html#2.12)

---

