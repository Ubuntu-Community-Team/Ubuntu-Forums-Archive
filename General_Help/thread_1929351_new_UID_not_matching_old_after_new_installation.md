---
title: "new UID not matching old after new installation"
date: 2012-02-21
forum: General Help
---

### Post by Zelen3d on 2012-02-21
This problem started after I installed Linux Mint on top of my Ubuntu home folder. **Continue reading, this issue isn't Linux Mint specific.** I deleted everything except the /home directory (witch was on a separate partition) and hoped everything would work OK because I was going to name all the user accounts as they were named on Ubuntu. Later, I found out that users aren't only identified by their name but also by their UID and GID. 

 The problem is that my UID was 1001 on Ubuntu but is now 1000 on Linux Mint. When I first opened my newly installed Linux Mint, I had plenty of problems related to this witch I ignorantly solved by... deleting the configs of the programs that didn't work.

 Now that I realized the origins of those problems, I am stuck with a Home folder filled with 1001 belonging files and with other, newly created, 1000 ones.#-o

 What should I do now? Change my UID and GID?

Edit: I have a backup of my /home directory on a disk

---

### Post by M!K3_$ on 2012-02-21
> **Zelen3d said:**
> What should I do now? Change my UID and GID?

I would give that a shot.
```
usermod -u 1001 username
```

---

### Post by Zelen3d on 2012-02-21
Isn't there a way to restore the backup while systematically "chowning" the files? That would repair my "bad start" I had with Linux Mint.

Edit:  Finally I did:   sudo chown -R paul:paul /home/paul 
Looks like it worked.

Edit: Anyway to prevent smilies anyone?

---

### Post by M!K3_$ on 2012-02-23
> **Zelen3d said:**
> 
Edit: Anyway to prevent smilies anyone?

You can use code tags. Put your text in between the code blocks (without the spaces).
```
[ code]my commands[/ code]
```

---

