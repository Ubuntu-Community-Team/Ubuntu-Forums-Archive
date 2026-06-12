---
title: "Shared Data Partition"
date: 2011-09-29
forum: General Help
---

### Post by mattrob33 on 2011-09-29
I have researched this as best I can but do not know much about drive partitioning so I can't find answers to my questions.

I want to multi-boot Ubuntu, Fedora, and Windows 7. Also, I want to store ALL my non-program data (documents, media, etc.) for Ubuntu AND Fedora on a 4th [data] partition that both Ubuntu and Fedora automatically mount on startup.

First, is this possible?

Second, is there anything strange I need to know about this? (i.e. I'll have problems later, I should have Ubuntu and Fedora share a swap partition, etc.).

Third, how much space should I allow for an Ubuntu or Fedora partition that only has system and program files?

Thanks in advance to everyone who actually gives me a helpful reply!


Also, I read somewhere about a driver for Windows that will allow you to use an ext* filesystem. So could my Windows partition access the data partition as well?

---

### Post by staticd on 2011-09-29
1)Separate Data partition:
(assuming you have done the partitioning)
When you install Ubuntu and fedora you will be given an option of choosing what partitions will be used and for what. Choose one partition to be mounted as / and another to be mounted as /home. Use the same partition for the /home of the other OS. 
However, if you run into trouble with the above method ( config files will be have conflicts between the two OSs. panel applets etc.)

Instead, try:
sdax on ubuntu /home/
sday on ubuntu /home/user/data

sdaz on fedora /home
sday on fedora /home/user/data

Link the Desktop, Documents,... .mozilla directories to copies in the data folder.


2)Shared swap:
If you hibernate from one OS, bad idea to share swap and boot from the other BAD idea to share swap.
3)Ext reader:
Yes the linux partition appears as another drive.

---

### Post by mattrob33 on 2011-09-29
Thanks!

To clarify, in the example you gave, what partitions would be mounted as / on each distro? The same as /home? Also to clarify, how many partitions would be used? Is it 2 for each distro (main & swap) + Data + Windows = 6 partitions? Or am I not understanding?

---

