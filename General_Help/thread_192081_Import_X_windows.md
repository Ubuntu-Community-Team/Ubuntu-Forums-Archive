---
title: "Import X windows"
date: 2006-06-08
forum: General Help
---

### Post by dev-h on 2006-06-08
Hello everyone. I am not able to import X aplications with my ubuntu. 
The problem is not in the LAN because in the same computer i can import that aplications using WindowsXP.
I did the "xhost +" and i can export X windows to another computers.

Any ideas???


I just installed it and did no configuration changes.


Thanks.

---

### Post by schilcha on 2006-06-09
Actually, I'm pretty stunned, that forwarding an X-display doesn't work. What I usually do (and that's why I've never noticed this effect) is using 
```

ssh -X user@host

```
This allows you to tunnel the remote X application through the ssh-connection without problems.

Good luck!

---

