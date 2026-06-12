---
title: "Strange mounting message on start-up"
date: 2010-06-29
forum: General Help
---

### Post by rfbeck on 2010-06-29
I use Lucid x86_64. Lately I have been getting the following message referencing the mounting of my flash drive on start-up:

"The disk drive for /media/UDISK is not ready yet or not present.
Continue to wait; or Press S to skip mounting or M for manual recovery."

I hit skip and and Lucid continues to boot fine, and the flash drive is mounted and working properly after booting. 
How can I get rid of this message?
Thanks for the help.

______
Robert

---

### Post by mikewhatever on 2010-06-30
You need to remove the appropriate line from /etc/fstab. If you need help identifying it, post the output of 
**cat /etc/fstab**.

---

### Post by rfbeck on 2010-06-30
Thanks. I made the edit to fstab. It now boots smoothly, without the aforementioned message. 
Nice. Thanks for your help!
______
Robert

---

