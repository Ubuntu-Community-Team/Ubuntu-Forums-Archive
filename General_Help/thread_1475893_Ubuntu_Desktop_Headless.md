---
title: "Ubuntu Desktop Headless?"
date: 2010-05-07
forum: General Help
---

### Post by moening.10 on 2010-05-07
Hello
I am very new to linux and have never used it before. So if you could talk in "dumb terms" to me that would be great. I just took an older dell desktop and installed Ubuntu on it. I want to put it in the back room and only hook an ethernet cable into it so i can VNC to it if i need to use it at all. Only problem is, when I unhook the monitor out of it, I will not boot into the O.S but will hang at an error message saying I am at a "low graphics error" Is there any way to get the O.S to boot without a monitor right into the main desktop so VNC can start and I can use another computer in my house to access it?

Thanks for the help

Dan

---

### Post by HermanAB on 2010-05-07
Rather use SSH:

ssh -C -c blowfish -X user@serveripaddress gnome-panel

---

### Post by sylvester_0 on 2010-05-07
^ The computer isn't even booting, that command isn't going to do any good.

I'd re-evaluate what you're going to be doing with the machine and if you really need a GUI. Servers are generally used in headless mode.

If you're going to be running LAMP (Apache/Mysql/PHP), mail server etc then I'd install the server flavor and use SSH for access. If you really need a "GUI" to configure things you could use Webmin/phpmyadmin etc.

If you just want to play with Linux (and you have the resources on your main system) just install Linux into a virtual machine. Virtualbox is a great free way to get into virtualization.

---

