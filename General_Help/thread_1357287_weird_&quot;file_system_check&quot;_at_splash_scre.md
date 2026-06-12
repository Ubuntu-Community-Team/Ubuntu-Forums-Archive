---
title: "weird &quot;file system check&quot; at splash screen?"
date: 2009-12-17
forum: General Help
---

### Post by black28 on 2009-12-17
hey guys. i booted up my PC today and on the bottom of the Xubunut Splash Screen "black with pic of mouse" there is this "file check" going on at the bottom. does anyone know where this is from or what is causing it? also it said Ethernet Connected but it wouldnt load anything til now. can anyone help me setup my internet? it was working when i first tried it. thanks.

---

### Post by MelDJ on 2009-12-17
that is fsck(i believe). it is normal and is done periodically

---

### Post by black28 on 2009-12-17
so it's automatically enabled? i thought i was hacked or something. haha. um any thing on the internet?

---

### Post by black28 on 2009-12-17
anyone?

---

### Post by Linuxforall on 2009-12-17
Its automatically enabled after a number of boots, thats to make sure all your files are intact and free from any corruption, its also a disk integrity check like you have in Windows called CHKDSK.

---

### Post by black28 on 2009-12-17
okay, thank you. so, about the internet. i have Road Runner into a Lynksis Wirless Router but am running a Cat5 to the Desktop. it used to work everytime at boot up. but now it says etho0 connected but browsers dont load until after sitting for about 10-15 minutes then it works. any help on this?

---

### Post by black28 on 2009-12-17
anyone please?

---

### Post by MelDJ on 2009-12-17
i don't know. but be patient.

---

### Post by JBAlaska on 2009-12-17
First check to see if IPv6 is disabled. Right click on the network manager applet in your upper panel, select your wired connection and click edit. go to the IPv6 tab and set to ignore.

Then set up a "Static" IP, go to the wired tab, select manual...enter a IP outside your routers DHCP range (Like 192.168.1.100), netmask to 255.255.255.0 gateway to your routers IP (normally 192.168.1.1 or 192.168.0.1) and set your DNS servers to googles (They are fast!): pri: 8.8.8.8 sec: 8.8.8.4

Hope this helps, as I'm off to bed..

---

### Post by black28 on 2009-12-17
okay, i did that. i currently had opera open on this thread. it works when i "reload" but when i try other sites in new tabs it quickly goes to error could not relocate server

---

### Post by black28 on 2009-12-17
okay, i switched back to my default network setting and now opera is working. you guys think that it could just be my ISP?

---

### Post by audiomick on 2009-12-17
Could be the ISP. Could be the router / modem feels like a restart, if it runs all the time.

Is it a router with a built in DSL modem? I was able to help myself isolate the cause of similar problems ( I ended up changing ISP ) by going straight into the set-up interface of the browser after boot-up and looking at the state of the internet connection. ( I am assuming that your router has the usual browser based set-up interface).

This will show you whether the computer is getting as far as the browser, whether the router/modem has a connection but the computer can't find it, or whether the computer is waiting for the modem/router to get it's connection. In the last case, the problem is with the ISP or the modem/router.

---

