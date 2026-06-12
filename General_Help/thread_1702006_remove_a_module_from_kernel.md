---
title: "remove a module from kernel"
date: 2011-03-07
forum: General Help
---

### Post by mahmoodn on 2011-03-07
Hi,
I have inserted a module with modprobe. However it seems to have problem. 
1- How can I remove the module from modprobe?
2- If I reboot and the kernel can not boot up because of this faulty module, how can I remove it?

---

### Post by krishna1650 on 2011-03-07
Few days ago, i also inserted a faulty module. And i was not able to type any command in terminal to remove the module. Then i simply rebooted and everything was fine. If simply a module is inserted and no other modification (like to add it to start-up scripts) is done, simply rebooting the system should work. At least that happened to me. 

Hope this helps.

---

### Post by timgood on 2011-03-07
```
sudo modprobe -rf <name of module>
```

Hope this helps.

---

### Post by krishna1650 on 2011-03-07
Few days ago, i also inserted a faulty module. And i was not able to type any command in terminal to remove the module. Then i simply rebooted and everything was fine. If simply a module is inserted and no other modification (like to add it to start-up scripts) is done, simply rebooting the system should work. At least that happened to me. 

Hope this helps.

---

### Post by mahmoodn on 2011-03-07
Yes seems that I the kernel is crash becuase I can not ssh to that. I only used "modprobe" and did not add that to start up script. So I hope that a reboot will make every thing back to normal. I will try that. thanks

---

