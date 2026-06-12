---
title: "Open windows folder saved as .tar file"
date: 2011-02-15
forum: General Help
---

### Post by neglect on 2011-02-15
So this seemed such a simple thing but I can't seem to make it work. Via empathy a friend sent me a windows folder containing jpg files. I suppose he just drag and dropped the folder into the messenger window in Win7 and sent it to me that way. I accepted and saved on the desktop. Empathy turned the folder into a .tar file. 
When I try to open the tar file I get the following error:

tar: This does not look like a tar archive
tar: Skipping to next header
tar: Exiting with failure status due to previous errors

Not surprising as it is indeed not a real tar archive. When I check to see which filetype it is with the file command it says -data. I've tried multiple versions of mount commands with various filetypes but I just can't seem to open this thing. How can I open this folder saved as .tar?

---

### Post by Habitual on 2011-02-15
just on a hunch **cough "windows folder" cough** rename the file to .zip and run

```
gunzip file
```

---

### Post by hawkmage on 2011-02-15
If file tells you it is data then it is not a standard tar or other type of archive type.  What do you get if you use strings on the file to see what printable info is in it.

---

### Post by neglect on 2011-02-16
Thanks for the replies so far! 
I did try renaming the file to a number of extensions such as .zip but that didn't work out. After all, it isn't a file it is a folder. I was sent a folder via the messenger, not a file.
Upon saving on my desktop it turned out Ubuntu/empathy turned it into a .tar file. I was hoping I could just leave out the extension and Ubuntu would figure out it is a folder but unfortunately it just becomes a file of the unknown type.

---

### Post by WorMzy on 2011-02-16
Just a stab in the dark here, but maybe you could mount it with the ntfs-3g driver?

```
sudo mount -o loop -t ntfs-3g /path/to/file /mnt
```

---

