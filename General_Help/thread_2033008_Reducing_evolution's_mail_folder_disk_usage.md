---
title: "Reducing evolution's mail folder disk usage"
date: 2012-07-25
forum: General Help
---

### Post by chmac on 2012-07-25
I just did a quick check, and there are over 9k messages stored on disk in ~/.local/share/evolution/mail/accountid/folders/INBOX but there are only 150 messages in that folder. Looking at the content of the files on disk, there are very old emails still there.

How do I clean this up? I can't find any kind of "compact folder" option in Evolution. Do I need to delete the whole thing from disk and start over?

---

### Post by czigor on 2012-12-19
I have the same problem. My backup is growing every year and now it is above 2G. Is there a way to get rid of removed emails for real?

---

### Post by philinux on 2012-12-19
> **czigor said:**
> I have the same problem. My backup is growing every year and now it is above 2G. Is there a way to get rid of removed emails for real?

I just sorted this. I backed up evo first. The archive was 600 meg and evo was always crashing. 

I closed evolution and did a dig around in /home/username/.local/share/evolution/mail

In the screen shot I deleted all numbered folders above local. Restarted evolution and hit send/receive which got me some duplicate emails. Then did another backup. Archive size now 40 meg!

It regenerated some numbered folders. Everything in local is my important stuff like saved messages etc.

---

