---
title: "Documents from XP partition unreadable"
date: 2010-10-19
forum: General Help
---

### Post by rweddy1 on 2010-10-19
So I set up my laptop dual boot with XP, now when I try to open text files, word docs, etc with get or doc files get error message with Gedit and with open office shows crazy unreadable characters???


Can someone tell me what settings I have wrong?

Cheers

-R

---

### Post by dcstar on 2010-10-20
> **rweddy1 said:**
> So I set up my laptop dual boot with XP, now when I try to open text files, word docs, etc with get or doc files get error message with Gedit and with open office shows crazy unreadable characters???


Do not use Linux tools on Windows filesystems. Gedit does not work correctly on non-Linux filesystems.

---

### Post by Pollox on 2010-10-20
> **dcstar said:**
> Do not use Linux tools on Windows filesystems. Gedit does not work correctly on non-Linux filesystems.

I have never had any issue opening files that arose from the type of filesystem the file is on. For instance, just now I opened a text file on an NTFS partition with gedit. NFTS support (both read and write) has been working properly for a while now on Ubuntu. You seem like an experienced user, so I'm curious if there is some issue I'm not aware of regarding this.

To the OP, do the files you are trying to open work with notepad and openoffice in Windows? Note that gedit is for text files and won't handle rtf or doc files. Also, openoffice may have trouble with newer Microsoft office files (I have not tested it with files created by Office 2010.).

---

