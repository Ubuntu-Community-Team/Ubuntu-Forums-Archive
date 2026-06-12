---
title: "How to change the swappiness value in Ubuntu 11.10"
date: 2011-11-10
forum: General Help
---

### Post by subhadip_sky on 2011-11-10
Hi, the documented method [here]("https://help.ubuntu.com/community/SwapFaq") won't work if I want to permanently change the swappiness value but the temporary method works. But I want to make it permanent. As I edit the sysctl.conf file, there is no mention of vm.swappiness, so I add it to the end of the file as it is mentioned in the documentation but it won't change the swappiness value even after reboot. Any help will be appreciated, thanks.

---

### Post by xulsolar on 2011-11-30
Yes it does. If you change the value in sysctl.conf does change the value in the Ubuntu system.

---

### Post by stinkeye on 2011-12-01
Make sure you put it on a new line, not the line beginning with "#".
eg
```
# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#
vm.swappiness=10
```

---

### Post by crazy bird on 2011-12-01
There's has been some discussions on other forums about changing the swappiness. Some stated that changing the swappiness doesn't have any effect while others claiming an improvement of the overal speed and performances. My own experience is that i have not experienced any improvement what so ever. 
 
The right question to ask now is, how many RAM do you have installed?

---

### Post by subhadip_sky on 2011-12-01
Well thank you for your help, yes adding it in a new line without the # works.
In my experience, if you have 512 mb RAM then changing the swappiness definitely increases the performance, I tried on my friend's old computer. But as I have 1.5 gb RAM on my computer and laptop both, the change in performance is not prominent.

---

