---
title: "Making more space for Ubuntu"
date: 2009-09-25
forum: General Help
---

### Post by V1P3R- on 2009-09-25
Hello,

I recently deleted another linux that I was dual booting. 

[IMG]http://i687.photobucket.com/albums/vv236/ieatbabies616/Screenshot-18.png[/IMG]
There is 21GB of unallocated space adn I want to add that 21GB to the 30GB ext3 drive. I thought I could right click and make ext3 bigger, but it will not let me. 

Thanks for the help.

---

### Post by wojox on 2009-09-25
If the drive is mounted you need to boot from a live cd.

---

### Post by drs305 on 2009-09-25
I wrote this guide for expanding a / Ubuntu system partition. Much of it applies to your situation, such as running from a LiveCD, unmounting swap even in the LiveCD, etc:
[Expanding an Ubuntu System Partition  ]("http://ubuntuforums.org/showthread.php?t=1219270")

---

### Post by oldfred on 2009-09-25
You will also have to delete swap so ext3 is adjacent to the unallocated and then recreate swap at the beginning of the unallocated or at the end of the ext3 partition.

---

### Post by V1P3R- on 2009-09-26
Wow, I cant believe I didnt think of running the live cd..

Well, I got it to work. Thanks!

---

