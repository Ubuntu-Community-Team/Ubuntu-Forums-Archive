---
title: "No wired internet"
date: 2010-03-08
forum: General Help
---

### Post by Emascu on 2010-03-08
Hello.

I'm having a problem with connecting to the internet under Ubuntu 9.10 on my dell latitude D600 laptop. After a clean install there's just no action after plugging in the cable. I rarely ever use a cable, but I need to download/install my wireless driver, but to do that I'm going to need a wired connection.
Wired and wireless work just fine under my xp partition.
Can anyone help me to get this wired connection going? Hopefully step by step if possible because I'm no expert.
I'd appreciate the help!

---

### Post by 2hot6ft2 on 2010-03-08
When you right click on the network manager in the top right panel and select Edit Connections, what is shown under Wired?

---

### Post by Emascu on 2010-03-08
It shows 'Auto eth0' under Name and 'never' under Last Used.

---

### Post by acalora on 2010-03-08
Left click on the network manager in the upper-right corner and click on 'Auto eth0'

---

### Post by Emascu on 2010-03-08
Then the icon starts spinning and after a while it stops and I get a black popup saying 'Disconnected, you are now offline'.

---

### Post by 2hot6ft2 on 2010-03-08
Have you tried unplugging the router and modem waiting a minute then plugging in first your modem then wait a minute and plugging in your router then waiting a minute and rebooting.

Sometimes that will work.

Or try
```
sudo /etc/init.d/networking restart
```
in a terminal
Applications > Accessories > Terminal

---

### Post by Iowan on 2010-03-08
If it won't play nice - you may need to resort to deeper troubleshooting. Check (from a terminal) **sudo lshw -C network**.

---

### Post by Manyette on 2010-03-08
I hope you have had the ethernet cable plugged in when you installed.  It is required if you want the system to set up cable ethernet when you installed the system.

---

