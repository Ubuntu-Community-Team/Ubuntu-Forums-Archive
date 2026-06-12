---
title: "Apply systemwide proxy option missing in Ubuntu 12.04"
date: 2012-08-12
forum: General Help
---

### Post by Kunal Maini on 2012-08-12
Hi
I recently re-installed Ubuntu 12.04 32-bit  and figured out there isn't any "Apply system-wide proxy" option in System Settings > Network > Proxy, which I realized when I was not able to download any software from Ubuntu Software Center.

Please help

---

### Post by irv on 2012-08-12
I am not sure what you are saying here. When you installed Ubuntu you had to have setup a password. And when you go to install software from the software center or package manager or from the command line it will ask for that password and you should be able to install them.
For example if you do it from the command line you need to type
```
sudo apt-get install [name of package]
```
you will be asked for your password for sudo (super user do).

---

### Post by Kunal Maini on 2012-08-12
> **irv said:**
> 
For example if you do it from the command line you need to type
```
sudo apt-get install [name of package]
```
you will be asked for your password for sudo (super user do).

Yes, it does ask for my password every time I try to update or install any software as you wrote. It's working fine on networks that do not require proxy.
Whenever I use my college network(which requires a proxy), it displays messages like "Failed to fetch" and "Unable to connect" even though I have entered the correct proxy settings.

It's working fine on my friend's PC, who is also using Ubuntu 12.04 and the college network

---

### Post by irv on 2012-08-12
OK, now it is clear to me what you are saying.
Can you check with your friend, and compare his network setting with your. There must be some setting you don't have set like his. I am not sure what it is seeing in am not using a proxy. Maybe someone else out can help you.
I did fine this in askubuntu: [Proxy settings not working:]("http://askubuntu.com/questions/69983/proxy-settings-not-working")

---

### Post by Kunal Maini on 2012-08-12
Thanks, that helped. I was able to download the packages using Synaptic but I am still unable to understand why Ubuntu Software Center and sudo apt-get commands are not working with proxy.

---

