---
title: "A couple of questions"
date: 2010-07-16
forum: General Help
---

### Post by Ziton on 2010-07-16
How do I get to my flash drive E: in mythbubtu 10.04?
Is Mythbuntu 10.04 ready for a dialup  connection with modem or does it need other applications?

---

### Post by prodigy_ on 2010-07-16
First, Linux doesn't assign letters (like E:) to partitions/volumes. Forget about them. Second, I'm not sure what file manager Mythbuntu uses but I believe it's Thunar. So if I'm not mistaken, you need to press Alt+F2, type **thunar** in the dialog window that will appear and press Run. This command starts File Manager where the list of your drives should be in the panel on the left side.

Regarding dial-up connection, read [this HOWTO](https://help.ubuntu.com/community/DialupModemHowto).

---

### Post by ThesaurusRex on 2010-07-16
If you're familiar with the terminal, pop one of those open and type:
```
cd /media;ls
```
Your drive should be listed.

---

### Post by Ziton on 2010-07-16
I cant find the places menu in Mythbuntu 10.04.
That was the first thing I looked for.

Would it be worth the trouble to buy a serial to USB adapter "$5" to simplify the dialup connection? Are there any real benefits of the USB opposed to the serial?

---

### Post by Ziton on 2010-07-16
> **prodigy_ said:**
> cd /media;ls

I'll try  this.
thanks

---

### Post by Ziton on 2010-07-16
No joy.
Couldn't find it in the file manager "thunar" or cd/media;lscd 
any other suggestions?

---

### Post by prodigy_ on 2010-07-16
Then probably it's not mounted at all. Can you run a couple of commands in terminal and post the output here?

```
sudo fdisk -l
sudo mount
```

---

### Post by linux18 on 2010-07-16
can you post the output of the command ```
 cd /media ; ls 
``` then try ```
 sudo mount -a 
``` then retry ```
 cd /media ; ls 
``` and post that

---

### Post by Ziton on 2010-07-16
I'll check those.

---

### Post by linux18 on 2010-07-16
Please copy/paste the output of the commands it's hard to know what the problem is if I can't see it.

---

### Post by Ziton on 2010-07-16
> **linux18 said:**
> Please copy/paste the output of the commands it's hard to know what the problem is if I can't see it.
I'd love too. I'm having to surf in xp cause I haven't figured out how to get mythbuntu  connected with the US robots serial Modem.  I need to get Ubuntu online bad.

---

