---
title: "Bluetooth mouse arbitrarily disconnecting"
date: 2009-11-11
forum: General Help
---

### Post by theodorekon on 2009-11-11
I have a Logitech V470 Bluetooth for my notebook and I have put this:
```
HIDD_OPTIONS="--i 00:07:61:9B:32:AB --server"
```
in /etc/default/bluetooth and normally it should connect to the mouse every time I boot. In fact some times it does and sometimes it doesn't. I cannot understand this kind of random behavior when it comes to computers but nevertheless I give the command:
```
sudo hidd --search
```
in a terminal and then I press the "connect" button on my mouse which normally does the job. What is very annoying though is that sometimes (again depending on ubuntu's mood) it disconnects after sometime which ranges from an hour down to a minute. 
I want my mouse to connect when I boot and NEVER disconnect until I log out. Is there anyway to permanently solve this problem or do I have to buy a cable mouse??

Thanks in advance

PS I'm under Ubuntu 8.04 LTS. I should also might add that I don't have the same problem in Windows Vista so the problem is not caused by the mouse.

---

