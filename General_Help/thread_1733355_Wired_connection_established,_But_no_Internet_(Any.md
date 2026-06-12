---
title: "Wired connection established, But no Internet (Any version, 64 Bit)"
date: 2011-04-19
forum: General Help
---

### Post by Skorm92 on 2011-04-19
Hello,

I'm kinda new to Ubuntu, And i wanted to check out 10.10
installation went fine, i installed within windows. But i have no internet!
I tried to create my own internet setup but it failed, and auto internet fails aswell.
Then i tried 10.04 then ubuntu 9. wich is currently installed.

I had the similar problem om 10.04 a while ago, but then i just installed ubuntu 9
and the problem was solved.


I keep getting the message that the connection is established. but i have no internet :(
Can someone help me on this one?

---

### Post by Skorm92 on 2011-04-19
Anyone?

---

### Post by ashickur.noor on 2011-04-19
> **Skorm92 said:**
> Hello,

I'm kinda new to Ubuntu, And i wanted to check out 10.10
installation went fine, i installed within windows. But i have no internet!
I tried to create my own internet setup but it failed, and auto internet fails aswell.
Then i tried 10.04 then ubuntu 9. wich is currently installed.

I had the similar problem om 10.04 a while ago, but then i just installed ubuntu 9
and the problem was solved.


I keep getting the message that the connection is established. but i have no internet :(
Can someone help me on this one?
Try to ping your server.

---

### Post by techunit on 2011-04-19
Did you install the wireless drivers for your computer? Go to additional Drivers in the menu, and hook up to a ethernet cable. Then check the drivers you need and check them to be installed.

Good Luck.

Common problem what people don't understand is it isn't always possible to install wireless drivers with the OS.

---

### Post by Skorm92 on 2011-04-19
> **techunit said:**
> Did you install the **wireless drivers** for your computer? Go to additional Drivers in the menu, and hook up to a ethernet cable. Then check the drivers you need and check them to be installed.

Good Luck.

Common problem what people don't understand is it isn't always possible to install **wireless** drivers with the OS.


i'm **Wired**.

---

### Post by cek on 2011-04-19
Open a terminal and post the output of the following commands:

ifconfig


route -N

---

