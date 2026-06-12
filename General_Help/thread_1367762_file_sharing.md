---
title: "file sharing"
date: 2009-12-29
forum: General Help
---

### Post by tobeach01 on 2009-12-29
getting message: failed to mount windows sharing when attempting to access files from other puters on the network.. can see the folders.. but cant access... what do I need to do?.. cheers

---

### Post by Bradj47 on 2009-12-29
Try checking the permissions on the folders. Right-Click -> Properties -> Permissions. Make sure Access for 'Others' is set properly.

---

### Post by tobeach01 on 2009-12-29
I right clicked on folders and get permissions could not be determined

---

### Post by the.lazy.boi on 2009-12-29
I believe you need to add the computer you wish to share to your /etc/hosts file.

---

### Post by tobeach01 on 2009-12-29
how?

---

### Post by the.lazy.boi on 2009-12-29
```

sudo gedit /etc/hosts

```

Then simply add the computer/s you wish to share with to the list at the top.

127.0.0.1	localhost
127.0.x.x	YourPChere
192.168.x.xx	PC You wish to share with

---

### Post by tobeach01 on 2009-12-29
didnt work.. i want to be able to access files from a windows based puter

---

### Post by Nooki on 2009-12-30
Which version of Ubuntu are you using? On my Ubuntu 9.10, I can browse other shares (even true Windows ones) without fuss.

May I suggest you try shutting down the firewall momentarily on the windows based PC? Then try accessing the shares again.

If I understand your situation, you can go into Places -> Network. Then you see the Windows machine (if it's in your WORKGROUP) server and can enter it? Or if it's not in your workgroup, you can reach it this way: Places->Network, then double click on Windows Shares, then double click on the Windows PC network group, then double click on the windows machine name. 

Can you "enter" it (double clicking on the PC-named icon)? Or does it throw an error at this stage?

---

### Post by the.lazy.boi on 2010-01-01
What version of windows are you running?

---

