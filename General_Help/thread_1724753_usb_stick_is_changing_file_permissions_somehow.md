---
title: "usb stick is changing file permissions somehow"
date: 2011-04-08
forum: General Help
---

### Post by dave00001 on 2011-04-08
So, I've got a weird problem....

I have two computers (one at work, one laptop) that I use daily.  Both are running Ubuntu 10.04.  I frequently use a usb stick to transfer files from one to the other.  Somehow, every time I do this, all files get turned into executables (as if I did a chmod a+x on them...)

This happens every time I use the usb stick.  I've reformatted the stick, but still this problem persists... anyone have any ideas on what is going on?  It is really getting annoying to have to zip up folders so this doesn't happen...

Thanks for any input you may have.

---

### Post by Telengard C64 on 2011-04-08
Is the USB stick formatted with a Linux native filesystem? If not, then that would explain why it doesn't correctly store permissions.

---

### Post by dave00001 on 2011-04-08
You may be right - I actually formatted it as FAT16 since I also have a few Windows computers at work too...  I'll try reformatting on Monday and post back then.  Hopefully this is a quick (easy) fix..

---

### Post by dave00001 on 2011-04-13
Well, your suspicions were correct.  The FAT type changes file permissions - and the ext2 type doesn't have these problems.  Thanks for your help.

This problem is now solved, but regardless it is a bit annoying... I have no idea if this constitutes a "bug" and I'm not sure if I should bring it up to the ubuntu developers if it is...  any ideas/suggestions??

---

### Post by Telengard C64 on 2011-04-13
The cause of the problem is simple. FAT filesystems are not designed to store Unix metadata. Same goes for NTFS and other filesystems. I don't think there is anything Ubuntu developers can do about this fact.

One thing you can do is to store your Linux files in a tar archive when they must reside on an alien filesystem. It is the only way I know for sure to preserve the metadata which Linux filesystems use natively.

---

### Post by Telengard C64 on 2011-04-14
I should have included some links to better explain.

[https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)

[http://manpages.ubuntu.com/manpages/lucid/man1/tar.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/tar.1.html)

---

### Post by dave00001 on 2011-04-17
This makes sense.  I was thinking that since windows cant store the permissions, the default would be non-executable...  oh well - I've been tarring my folders anyhow.

Thanks for your help.

---

### Post by Telengard C64 on 2011-04-17
> **dave00001 said:**
> I was thinking that since windows cant store the permissions, the default would be non-executable...

Actually I know there is a way to mask the permissions bits when you mount the volume. I just don't know how to do it properly so I'll leave that as an exercise for you if you like  :P

Glad to help  :)

---

