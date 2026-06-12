---
title: "Status long running commands?"
date: 2009-08-29
forum: General Help
---

### Post by VTStevenVT on 2009-08-29
This is really a bash question. 
So I reformated an old ntfs drive as ext3 and mounted it on /storage. I then moved a huge folder from my main drive to /storage with the command:  
```
mv Folder /storage   
```Then the console just sits there for a LONG time because it is moving all of those files in Folder (about 25 Gb).  I was just curious if it was possible to open another terminal and see what the status of the mv operation was.

---

### Post by Rob_H on 2009-08-29
Few possibilities here. You can use the "-v" switch of **mv** to get file-level detail. You can also get continuous updates by changing to the directory in another console and issuing the **watch** command like this:

```
watch -d ls -aFl
```

Alternatively, you can use a file manager GUI, which will give you a progress bar.

---

### Post by Stunts on 2009-08-29
One way you have to do that is to open a new terminal window, just "cd" to "/" and type:
```
du -h /storage
```

The last line will be the total space taken on your folder. You just have to see how much is left to reach you 25 GB.

---

