---
title: "Internet stopped working!!!"
date: 2011-10-02
forum: General Help
---

### Post by ambdeep on 2011-10-02
I was running an update on my ubuntu 11.04 when my laptop ran out of battery in the middle of an update process. Now my internet is not working. I am able to connect to any network (wired/wireless) but i cannot access the internet. Please help.

---

### Post by eric_1982 on 2011-10-02
Can you try to ping something by ip address?

Open an terminal and type the following. (You can cancel the command by hitting CTRL + c)

**ping 74.125.225.18 **

(Above is an example of pinging google by IP (74.125.225.18 ))


What is displayed when type the following two commands in a terminal?

**ifconfig**


**cat /etc/resolv.conf**

---

