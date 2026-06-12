---
title: "BASH: How to Prompt user to restart computer in the same way as an update?"
date: 2010-01-13
forum: General Help
---

### Post by drewsus on 2010-01-13
Hello, 
I was curious if anyone knew a good way to prompt a user to restart the computer (now or later) in much (or exactly) the same way as an update that requires a restart?
I would like to know how to do this in a bash script.
Drew

---

### Post by x33a on 2010-01-13
You could do this without bash also.

try
```
xmessage please restart your computer
```

or

```
sudo shutdown -k time [warning message]
```

the -k switch doesn't do an actual shutdown, only warn.
Though the latter would not prompt the user to shutdown, instead it will warn the user about shutdown

---

