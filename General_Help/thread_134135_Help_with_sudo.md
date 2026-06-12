---
title: "Help with sudo?????"
date: 2006-02-21
forum: General Help
---

### Post by REXXER on 2006-02-21
When i type "sudo" into the terminal, it says "sudo: unable to lookup RONEN via gethostbyname()" Wat does that mean?? HELP!!!!! TY

---

### Post by jones_jj on 2006-02-21
Are you able to sudo any command at all?  e.g. are you able to sudo ifconfig to see your network settings?

Also do you have root enabled?  If you are able to access root log into root by pressing ctrl+alt+F1 and logging into root.  From there run visudo.  When visudo is running you will see a line that says:

**root ALL=(ALL) ALL**

You will want to add your username after line that defines root.  So it will look like this:

**<username> ALL=(ALL) ALL**, <username> is your username.

If you can't access root, you will have to run sudo passwd to enable root, give root a password.  Then follow the steps above.

---

### Post by REXXER on 2006-02-21
ty it works now

---

### Post by REXXER on 2006-02-21
ty it works now

---

### Post by jones_jj on 2006-02-21
No problem.  I would actually write those steps down just in case you ever have to reinstall Ubuntu or install it on another machine, and that way you will be able to do those steps and not even think about it again.

---

### Post by beku on 2006-02-21
i have the same problem. i edited visudo like you have said, but i still have the same reply when i write sudo or anything like that...

---

