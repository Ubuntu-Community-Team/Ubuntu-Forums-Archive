---
title: "Put Windows into Hibernation from SSH?"
date: 2010-08-02
forum: General Help
---

### Post by GriFF3n on 2010-08-02
I have a Windows Home Server and would like to put it into hibernation from my laptop running Ubuntu. Is this possible through SSH or a program? Thanks,

GriFF

---

### Post by chopinhauer on 2010-08-04
If you install an SSH server on Windows, there is a 'shutdown' program on Windows too.

I can not tell you more, since I haven't a Windows box available.

---

### Post by marshmallow1304 on 2010-08-04
Well, from [this page]("http://txt.binnyva.com/2007/04/shutdown-a-windows-system-from-command-line/"), it looks like you should be able to do
```
shutdown /hibernate
```

but I've no idea how the ssh server works on Windows server.

---

