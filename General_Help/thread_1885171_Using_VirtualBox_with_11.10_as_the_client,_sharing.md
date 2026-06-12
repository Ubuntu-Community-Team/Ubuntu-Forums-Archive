---
title: "Using VirtualBox with 11.10 as the client, sharing folders"
date: 2011-11-22
forum: General Help
---

### Post by craigsn on 2011-11-22
I have a Win 7 system running 11.10 in VB. I want to share My Document files from Windows to 11.10, and be able to write back to the directory. Using VBs shared folders, I have created a shared folder and I can get to the directory (/media/sf_myDocs). So that all works. Now I simple want to have that folder show up in the Documents folder in /home/me/Documents. I have tried to create a link, but the error message says that hard links are not allowed. What should I be doing?

Thanks

---

### Post by lechien73 on 2011-11-22
Hi,

The reason is that hard links are not allowed for directories, you need to create a symbolic link instead:

```
ln -s /media/sf_myDocs /home/me/Documents/
```

HTH

---

### Post by craigsn on 2011-11-23
Hello lechien73,

Thanks, the symbolic link worked, or at least it was created. 
ln -s /media/sf_myDocs /home/me/Documents/WinDocs

However, I am unable to use the link to get into the folder on Windows. I get the message saying "cd: WinDocs: No such file or directory."

Any suggestions?

Thakns

---

### Post by oldtimer7777 on 2011-11-23
sudo apt-get install ntfs-3g

It is no longer pre-installed in Ubuntu 11.10


> **craigsn said:**
> I have a Win 7 system running 11.10 in VB. I want to share My Document files from Windows to 11.10, and be able to write back to the directory. Using VBs shared folders, I have created a shared folder and I can get to the directory (/media/sf_myDocs). So that all works. Now I simple want to have that folder show up in the Documents folder in /home/me/Documents. I have tried to create a link, but the error message says that hard links are not allowed. What should I be doing?

Thanks

---

### Post by craigsn on 2011-11-24
Hi Oldtimer777
When I tried that the response from linux was that I already had the latest software installed. 

However, I retried the symbolic links, and this time it worked when I did it as sudo,

so 

sudo ln -s /media/sf_myDocs /home/me/Documents/

This worked.

Thanks to all

---

### Post by lechien73 on 2011-11-25
Great stuff. Glad it's working. If you get chance, could you please mark the thread as [SOLVED] using the **Thread Tools** menu at the top of the page?

Thanks

---

