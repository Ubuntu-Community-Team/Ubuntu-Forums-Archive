---
title: "X-server does not automatically starts in Xubuntu."
date: 2006-05-22
forum: General Help
---

### Post by DoktorNo on 2006-05-22
Hi there.

I have installed server version of Ubuntu 5.10, and then I installed, via apt-get, xubuntu-desktop. The problem is, that after restart the system is displaying only text console login protomp. After loging in, the XFCE doesn't starts, and only way to start it is to type:
```
xserver
```
And then XFCE is starting up without any hassle.

Have I missed some package(s)? Personally I prefer graphic login screen&#8230; By the way, this problem doesn't occurs when I have installed just only XFCE4 pack. What is going on? ](*,)

---

### Post by DoktorNo on 2006-05-22
This problem is solved!!

The solution is to install any login menager, for example wgm or gdm. So here we go:
```
sudo apt-get install wdm
```

And after restart you can login using user friendly GUI. :)

---

