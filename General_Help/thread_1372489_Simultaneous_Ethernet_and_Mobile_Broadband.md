---
title: "Simultaneous Ethernet and Mobile Broadband"
date: 2010-01-04
forum: General Help
---

### Post by RudolfK on 2010-01-04
I just installed 9.1 and connected to another computer that has Windows ICS running for sharing the internet connection on that computer (3G USB stick). I then set up my Ubuntu machine's Ethernet interface with a static IP address and the default gateway to that of the Windows computer. This works and I could browse the web through the Ethernet connection. Then, I removed the 3G stick from the Windows machine, and inserted it into the Ubuntu machine, and set up the Mobile broadband connection. Now, there were two active network interfaces, Eth0 and the Broadband connection. Now web browsing stopped working. The moment I pulled the Ethernet cable out, i could once again browse the web.

So, the question is, how do I set up networking so that I can use the Ethernet interface for file/printer sharing with other computers, while browsing the web through the broadband interface. Eventually i would like to share the internet through Eth0 as well, but i guess one thing at a time. 

I am quite a newbie to Ubuntu, your help is much appreciated.

---

### Post by dansang on 2010-01-05
I am also using mobile bb and having the same problems sharing it across a network, network manager seems to be defaulting wired eth0 to gain a connection from an old BT hub. Where as i, like you want to share my mobile bb across a network wired to my laptop. eventually being able to wireless the connection for a around the house use.

Sorry i can't offer advice!!

I'm still not even sure i have an eth0 connection linking the two as of yet...newbie but still working on it. :)

---

### Post by RudolfK on 2010-01-05
So my problem is not that unique, thanks for the reply! In retrospect I think I should have started the thread in the Networking support category... Wonder if I can move a thread, or should I just start a new one there and mark this one as solved ?

---

### Post by plucky on 2010-01-05
Never tried it but this [link](https://help.ubuntu.com/community/Internet/ConnectionSharing) might help.

OR

[this link](http://ubuntuforums.org/showthread.php?t=91370&highlight=sharing+internet+connection)

Good Luck

> Wonder if I can move a thread, or should I just start a new one there and mark this one as solved ? 

Use the **Report abuse** button and ask a Moderator to move the whole thread to the Networking Forum

---

### Post by RudolfK on 2010-01-07
Thanks plucky, the first link , first suggestion solved my problem!  How do I mark this thread as solved ?

---

