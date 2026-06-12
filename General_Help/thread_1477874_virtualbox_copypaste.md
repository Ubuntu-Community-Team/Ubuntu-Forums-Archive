---
title: "virtualbox copy/paste"
date: 2010-05-09
forum: General Help
---

### Post by Kofgarter on 2010-05-09
Hello everybody. Have just installed ubuntu on virual disk. So now, as host machine I have - Windows, and as guest machine - Ubuntu. Such question, how to copy/paste texts between host and guest machines (into command-line, mc, etc.)? Thanks.
ps: I have tried ctrl+v and ctrl+shift+v (ctrl, shift - left buttons), no reaction at all.

---

### Post by P4man on 2010-05-09
You have to install guest additions on the VM. From virtualbox menu select Devices>Install Guest Additions

---

### Post by Kofgarter on 2010-05-09
thanks for help, I installed additions, then rebooted (everything as written here: [http://www.dedoimedo.com/computers/virtualbox-guest-addons.html](http://www.dedoimedo.com/computers/virtualbox-guest-addons.html)), and in result nothing changed. The text that I copy from windows, not inserted into ubunta.
what's up?? may be these additions don't boot with main system?

---

### Post by Kofgarter on 2010-05-09
I want to draw your attention to the fact that I've installed server version, and so I can only work through the console.

---

### Post by P4man on 2010-05-09
aah.. then im not sure you can. Its not like the tty has a clipboard.

---

### Post by nickpj on 2010-07-28
I have the same question, but I don't think it can be done at the moment (i.e. cannot currently copy text from host's clipboard onto console-based editors on the guest).

Here's the feature request in the VirtualBox bug tracker: [http://www.virtualbox.org/ticket/1139](http://www.virtualbox.org/ticket/1139)

---

