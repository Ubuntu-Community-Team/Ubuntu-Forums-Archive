---
title: "I can't save anything to external storage devices"
date: 2009-09-20
forum: General Help
---

### Post by grandpa2390 on 2009-09-20
I open up my external hard drive or a flash drive and I copy a file to it. It says the copy was complete and that everything is good. Then I unplug it and plug it back in and the file is missing, as if it never existed.

---

### Post by blueridgedog on 2009-09-21
Do you unmount or eject it before unplugging it?

---

### Post by grandpa2390 on 2009-09-22
I just unplug it. But even if i am running a virtualbox (windows xp pro) and I connect it there it still does not show

---

### Post by grandpa2390 on 2009-09-22
I will try ejecting or unmounting

---

### Post by grandpa2390 on 2009-09-22
amazing. If I was not so lazy it would have worked. Well so far so good. When I unmount or eject it whatever the proper term is, and then remount it in virtualbox it works. If I have anymore trouble with it, I will post a new thread.

---

### Post by grandpa2390 on 2009-09-22
oh and thankyou for your suggestion.

---

### Post by 3rdalbum on 2009-09-22
Before unplugging any data device on **any operating system**, always follow the procedure to "Safely remove" or unmount first. This ensures that all pending data is flushed (written to disk) and that no program decides to attempt to write data to the disk at the instant that you pull the disk out.

Linux mounts USB drives "async", which means that when you are writing data to a flash drive, it's actually just going into a memory buffer first. For technical reasons, this helps prevent flash wear-down, and makes writing quicker. The buffer gets flushed every so often and when it reaches a certain size, but you need to properly unmount the drive to make sure that any data still in the buffer gets written to disk.

When your Linux desktop reports that a copying operation has finished, it really means "all the data has been copied at least into the buffer"; if the destination disk is slower than the source disk, then data will continue to copy across from the buffer to the disk while you do other things (or when you go to unmount).

Just a bit of technical discussion about what actually happens, so you'll understand the reasoning behind new things on Linux :-)

---

