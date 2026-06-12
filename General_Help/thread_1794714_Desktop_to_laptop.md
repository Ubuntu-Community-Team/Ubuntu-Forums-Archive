---
title: "Desktop to laptop?"
date: 2011-07-01
forum: General Help
---

### Post by UncleMonty on 2011-07-01
I want to transfer the files on my laptop to my desktop. Both run ubuntu 10.04. How can I do this?

---

### Post by dino99 on 2011-07-01
use nautilus to switch your data on a usb stick

---

### Post by akand074 on 2011-07-01
Or use an external hard drive if you have a lot of files. Alternatively, you can set up a share, but with lots of files I wouldn't transfer over the network.

---

### Post by samigina on 2011-07-01
A cable (cross cable) network, between the desktop and the laptop should be the best way.

---

### Post by collisionystm on 2011-07-01
> **samigina said:**
> A cable (cross cable) network, between the desktop and the laptop should be the best way.


Give both computers a static address on the same network.

Cut a regular ethernet cord open. Join the orange white to the green white, white green to white orange. Voila. you have a crossover.

Although I believe USB is faster depending on how new your computer is.

---

### Post by mikejonesey on 2011-07-01
> **samigina said:**
> A cable (cross cable) network, between the desktop and the laptop should be the best way.

vote 1+

use the start->places->connect to server, use ssh port 22 dir / and the ip can be attained using ifconfig... this will open a nautilus window with sftp so you can easily copy from one to the other...

or if u prefer command line you can use either scp (secure copy, runs across nets), or use sshfs to make a mount which would enable you to use stuff like rsync easily...

ps i think when i was last checked ubuntu defaults to half duplex, use ethtool to set full duplex for faster copying...

---

### Post by pqwoerituytrueiwoq on 2011-07-01
how about using scp copy over network (install openssh-server on the desktop)
scp -r ~/Documents/ user@me-desktop:/home/me/Documents/

---

### Post by linuxuser12345 on 2011-07-01
Put all of your files into Ubuntu One. This way, you can keep your files synced between both computers *and* your files stay safe and secure in Canonical's servers.

---

### Post by akand074 on 2011-07-02
> **linuxuser12345 said:**
> Put all of your files into Ubuntu One. This way, you can keep your files synced between both computers *and* your files stay safe and secure in Canonical's servers.

Yeah except for the bandwidth costs of uploading and then downloading every time you use anything. Just put them on an external device unless you have a super fast network.

---

