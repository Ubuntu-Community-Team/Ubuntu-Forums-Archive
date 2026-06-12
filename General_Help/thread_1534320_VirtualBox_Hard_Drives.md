---
title: "VirtualBox Hard Drives"
date: 2010-07-19
forum: General Help
---

### Post by Ready2DropWin on 2010-07-19
Hello,

I can't seem to find the dir for where virtual box stores the hard drives. I have made a few test hard drives, and I want to remove them off my computer. Does any one know where they are?

Thanks

---

### Post by Fire_Chief on 2010-07-19
You can use the Virtual Media Manager in the File menu to manage the hard drives as well as ISO files in VBox.

---

### Post by 3Miro on 2010-07-19
The correct way is via the media manager in VirtualBox itself. If you really want to manually do that, open Places -> Home and then hit Ctr + H to show hidden files. Look for the folder .virtualbox, I am not sure about the exact spelling, it may vary depending on the virtual box version. Virtual Hard Drives are files within.

---

### Post by Ready2DropWin on 2010-07-19
Thanks so much, both post were most helpful. I didn't know about the ctrl + h to show hidden files. Now if I wanted to back up my virtual hard drive, all I need to do is copy the harddrivename.vdi file, right?

---

### Post by 3Miro on 2010-07-19
> **Ready2DropWin said:**
> Thanks so much, both post were most helpful. I didn't know about the ctrl + h to show hidden files. Now if I wanted to back up my virtual hard drive, all I need to do is copy the harddrivename.vdi file, right?

That is correct. I have done this myself several times.

---

### Post by Irony on 2010-07-19
Note, you don't have to install your guest operating system in the .virtualbox folder... you can install it anywhere, for example I've installed my .vdi file in a separate partition.

---

### Post by Ready2DropWin on 2010-07-19
Thanks for the heads up, on were I can install it. I am just now using vbox now for the first time.

---

### Post by etdsbastar on 2010-07-19
> **Ready2DropWin said:**
> Thanks for the heads up, on were I can install it. I am just now using vbox now for the first time.

If you have solved your query then please mark your thread as solved by selecting the thread tools above, this keeps forums neat and clean.

---

