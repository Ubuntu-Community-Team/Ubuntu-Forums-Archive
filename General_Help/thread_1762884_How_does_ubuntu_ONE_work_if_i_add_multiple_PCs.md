---
title: "How does ubuntu ONE work if i add multiple PCs??"
date: 2011-05-19
forum: General Help
---

### Post by Matt Pellegrini on 2011-05-19
If i have two Ubuntu PCs with currently different Documents directories say and I sign into the same ubuntuOne account on both and sync the Documents directories, does this merge the directories or will some files get deleted?

There's a chance I've completely misunderstood what Ubuntu One does so please, nothing too complex.

What i mean is if pc1 has files v x y in it's Documents directory and pc2 has x y z in it's Documents directory, both are set to sync. Which if any of the following happen?

pc1 and pc2 have x y in Documents
pc1 and pc2 have x y z in Documents
pc1 and pc2 have v x y in Documents
pc1 and pc2 have v x y z in Documents

---

### Post by kostkon on 2011-05-19
Obviously, the 4th
```
pc1 and pc2 have v x y z in Documents 
```

---

### Post by Matt Pellegrini on 2011-05-20
If that's the case then surely if both were synced and had  v x y z files in them, then while working on pc1 i decide i don't need document x so i delete it. Then when they resync surely it would put document x back? (as it was still on pc2)?

Thanks

---

### Post by mc4man on 2011-05-20
> **Matt Pellegrini said:**
> If that's the case then surely if both were synced and had  v x y z files in them, then while working on pc1 i decide i don't need document x so i delete it. Then when they resync surely it would put document x back? (as it was still on pc2)?

Thanks
No - what's likely to happen is x will be removed from pc2 - one should be a bit careful in this regard (as to what synced means

---

### Post by Matt Pellegrini on 2011-05-20
deleting x from pc 2 is exactly what i would want (if i chose to delete it from pc1).

The point of asking all this is that i have two pc's running Ubuntu with some shared files and others not. The shared files are from emailed copies or something. I want to keep the directories synced using Ubuntu one but don't want to loose files during the setup.

---

### Post by grahammechanical on 2011-05-20
I do not use Ubuntu One in the same way as you intend to use it, so I may be incorrect in some of the things that I say. Please remember that.

1) It is your Ubuntu One account. The files are stored in folders on computer servers somewhere in the world. You can access those files from any computer because you have the password that lets you login to the Ubuntu One site.

2) I have certain files that are marked for syncing. If I am working on those documents and I save the work, then the file gets uploaded to the Ubuntu One servers. There is another folder in my file system called Ubuntu One. If I copy a document to the folder it will be uploaded to a folder on the Ubuntu server.

3) It is possible to share my documents with another computer and this is my understanding of how it works. Both computers have Ubuntu One installed. I mark a folder as being shared by that computer. Then, when I copy a document into that folder on my computer it gets uploaded to the Ubuntu One servers and then downloaded to the other computer. And the process works in reverse.

I see this feature as a means of passing documents back and forth between computers. I see this as two separate features. A document that is edited on one computer will be updated on the other computer. This is part of the purpose of Ubuntu One. But another part of that purpose is on-line storage and it would not be good if others could edit files as part of this process. So, I think that there is a separation. Of course my understanding might be completely wrong.

Regards.

---

