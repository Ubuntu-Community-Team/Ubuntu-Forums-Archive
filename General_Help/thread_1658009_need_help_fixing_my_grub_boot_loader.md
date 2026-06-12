---
title: "need help fixing my grub boot loader"
date: 2011-01-02
forum: General Help
---

### Post by mikzdx on 2011-01-02
Hello,

Here is what happened.  I had vista and Ubuntu 9.10 installed on my laptop.  Because vista was running horribly on my laptop i decided to format that partition and install windows 7.  After doing this, windows 7 automatically booted up and the grub boot-loader didnt show up so i couldnt boot into ubuntu.  To fix this, I used rescatux to fix the grub boot-loader.  Now, I do have my loader back and can boot into ubuntu, but the windows option is still windows vista instead of windows 7.  How do I fix this?  And on a side note, in the grub boot-loader I have a bunch of ubuntu options with (recovery mode) next to them.  How do i get rid of all those extra options?

---

### Post by Hur Dur on 2011-01-02
> **mikzdx said:**
> Hello,

Here is what happened.  I had vista and Ubuntu 9.10 installed on my laptop.  Because vista was running horribly on my laptop i decided to format that partition and install windows 7.  After doing this, windows 7 automatically booted up and the grub boot-loader didnt show up so i couldnt boot into ubuntu.  To fix this, I used rescatux to fix the grub boot-loader.  Now, I do have my loader back and can boot into ubuntu, but the windows option is still windows vista instead of windows 7.  How do I fix this?  And on a side note, in the grub boot-loader I have a bunch of ubuntu options with (recovery mode) next to them.  How do i get rid of all those extra options?

It still works right?

You could try going into menu.lst and changing "title Windows Vista" to "title Windows 7" or Grub.cfg and removing the menuentry for Vista, and replacing it with 7.

---

### Post by cheapie on 2011-01-02
"Recovery Mode" isn't "Extra". It's the Linux equivalent of safe mode. As for the naming issue, I suggest following the above instructions.

---

### Post by wilee-nilee on 2011-01-02
In the Ubuntu terminal.

sudo update-grub

---

### Post by mikzdx on 2011-01-02
wilee-nilee's suggestion worked.  It got rid of the old vista partition that didn't work, and it gave me a windows 7 option.  On my second problem though, I still have a bunch of lines that look like this.  I suppose these are made when my computer crashes unexpectedly?

-----------------------------------------------
Ubuntu, Linux 2.6.31-20-generic
Ubuntu, Linux 2.6.31-20-generic (recovery mode)
Ubuntu, Linux 2.6.31-19-generic
Ubuntu, Linux 2.6.31-19-generic (recovery mode)
Ubuntu, Linux 2.6.31-17-generic
Ubuntu, Linux 2.6.31-17-generic (recovery mode)
Ubuntu, Linux 2.6.31-16-generic
Ubuntu, Linux 2.6.31-16-generic (recovery mode)
Ubuntu, Linux 2.6.31-15-generic
Ubuntu, Linux 2.6.31-15-generic (recovery mode)
------------------------------------------------

---

### Post by Quackers on 2011-01-02
It is normal to have old kernels in the grub menu. People here advise that once the newest kernel is known to work you can delete all the older kernels (except one, to be kept for safety reasons). You can uninstall all the old kernels via synaptic package manager. Just enter 2.6.31 into the search boc and they will all appear. There will be 2 entried for each kernel. Right-click each entry and select Mark for complete removal. Then apply the change by clicking the green tick mark in the toolbar. Please don't remove tha latest kernel, or you will have nothing to boot with!
Once that's done, you can run ```
sudo update-grub
``` in a terminal to update grub.cfg and the grub menu.

---

### Post by mikzdx on 2011-01-02
Thank you guys.  I was able to fix my grub-loader.

---

### Post by cheapie on 2011-01-02
In that case, please mark the thread as [SOLVED].

---

### Post by Miter_J on 2011-01-02
Even your problems seem to be fixed already, I recommend you to learn to modify your grub options in the file /boot/grub/grub.cfg.
Just read it and you'll easily find out how to.
I think this can help you more than using the synaptic way. You may deal with lots of other problems with grub in the future by modifying this file.

---

### Post by Quackers on 2011-01-02
If you manually edit grub.cfg the changes will be over-written when grub is updated. That's why it says at the top of the file Do Not Edit!

---

