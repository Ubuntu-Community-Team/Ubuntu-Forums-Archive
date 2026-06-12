---
title: "Documents open as write-protected"
date: 2009-11-01
forum: General Help
---

### Post by zumbi77 on 2009-11-01
Whenever I open a word or excel document e-mailed to me, it opens as write-protected, as opposed to windows where I can start working with straight away.

Is this a linux/ubuntu feature? How do I change it?

---

### Post by goldencako on 2009-11-01
I only see one cause for this, but I might wrong. The first one is, you are downloading the file onto a write protected folder. This would explain why all your files are being opened as write protected. Go to the folder and check if it allows for write access. If it doesn't, add it.

---

### Post by zumbi77 on 2009-11-01
Thank you. With a bit of googling I figured out I had to open nautilus as root and edit the properties of the tmp folder.

I still don't understand why it was set like that. This a fresh install of 9.10, and this was just impractical.

---

### Post by michy99 on 2009-11-01
You need to save the documents in your home folder, say in Documents, and then open them to work on them. If you open them in your e-mail program, it uses the /tmp directory, which is a temporary directory. It is cleaned out every time you boot. It needs to be owned by root; do not change the ownership.

---

### Post by coffeecat on 2009-11-01
> **zumbi77 said:**
> With a bit of googling I figured out I had to open nautilus as root and edit the properties of the tmp folder.

I still don't understand why it was set like that. This a fresh install of 9.10, and this was just impractical.

Well - /tmp is always owned by root - by design. It's a system folder. That's why it's owned by root. It's true that some apps store temporary data in /tmp (video rendering ones for example), but that's a different matter. That's partly what /tmp is for but /tmp is a poor place to store personal downloaded files. As a general rule in any Unix OS - Linux or MacOS - use only your home folder for personal stuff - including downloads. That's what your home folder is for. Then you won't get permission/ownership problems. Or use a separate data partition if you wish to.

I have to say it, but Windows is to blame for this sloppy habit of putting personal files anywhere. Windows will allow you (or at least XP did) to make personal folders in the root of the drive. It's untidy, it's ugly, it's inadvisable, and it's bad practice.

---

### Post by zumbi77 on 2009-11-01
Thanks for the advice. By no means did or do I intend to store my files in the tmp folder. I just wanted to be able to start working immediately with my documents when I recieve an e-mail. Both gmail and thunderbird place my documents in the tmp folder when I open them, so they're write-protected.

Does this mean you recommend I set them to place the documents in the download folder? How do I change that?

---

### Post by coffeecat on 2009-11-01
> **zumbi77 said:**
> Both gmail and thunderbird place my documents in the tmp folder when I open them, so they're write-protected.

Good Heavens! Is that the default behaviour?

I'm afraid I have no experience of email clients. The web-client of my mail provider (Yahoo) is so good (at least it serves my purpose) that I've never bothered. So when I download an email attachment it gets saved to the Firefox download location - which in my case is the desktop. Which is ugly and untidy as well. :lol: But at least I don't get permissions problems, and I can then move them where I want.

> **zumbi77 said:**
> Does this mean you recommend I set them to place the documents in the download folder? How do I change that?

Or any folder you want, so long as it is in your home folder. Sorry, but I don't know how to change the default download folder in Thunderbird, but there must be a Preferences or Options entry in the menus somewhere. If it's anything like Firefox it'll be under Edit (in Linux). Isn't Gmail like Yahoo in that you use a web-browser? Are you using Firefox for this? If so, go to Edit > Preferences > Main and specify your download location there.

---

### Post by michy99 on 2009-11-01
Try this: When you open a document, before you do anything else to it, do a Save As and save it where you normally keep documents. You should be able to do whatever you want to then.

---

### Post by TheForumTroll on 2009-11-01
Evolution should work. It creates a temporary file in ~/.evolution :)

---

