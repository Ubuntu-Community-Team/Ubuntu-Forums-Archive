---
title: "help to install ubuntu on dell 1555"
date: 2010-01-31
forum: General Help
---

### Post by veda87 on 2010-01-31
Recently I brought Dell 1555 laptop. I need to install ubuntu in it.
I tried installing but I couldn't able to see after I opted for install ubuntu.

I downloaded ubuntu-9.10 from the site and tried installing it. When I started it, It propmpted me like

Try ubuntu without causing changes
Install ubuntu
memory test
boot from hard disk

When I tried install ubuntu, The cursor blinks for some time and then a blank bright screen. i am not able to see anything.

I even tried noapic, nolapic, apic=off which are present under f6 options... No fruitful result.

this is the bootup line: ```
file=/cdrom/preseed/ubuntu.seed boot=casper only-ubiquity initrd=/casper/initrd.lz quiet splash --
```Can anyone tell me like what should I do inorder to install...

---

### Post by theozzlives on 2010-01-31
Could be a video issue, have you tried the alternate CD?

---

### Post by JK3mp on 2010-01-31
Making a new thread won't make it go any quicker. You've already started a thread at [http://ubuntuforums.org/showthread.php?t=1395307]("http://ubuntuforums.org/showthread.php?t=1395307") . Admin please combine the topics. veda please be patient I'm also having the same issue and someone will reply soon enough. I've posted my input on your prior thread. -Peace

---

### Post by veko on 2010-02-01
My first guess would be faulty install disk. Did you check that it is OK? It's "Install" and then "Check install media", if I recall it correctly. If you can't get even this far, then I'd suggest to make a new install disk.

You might want to run "Try Ubuntu from disk" too, just to check if that works.

I have Dell 1555 and Ubuntu 9.10 too. Everything works fine, though I can't remember if I had to set noapic kernel option. Generally there was no big hassle and practically everything worked right out of the box. So rest assured, you should be able to get Ubuntu running on your machine.

Sorry I can't really help you more.

---

