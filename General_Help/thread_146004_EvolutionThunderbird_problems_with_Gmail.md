---
title: "Evolution/Thunderbird problems with Gmail"
date: 2006-03-17
forum: General Help
---

### Post by leviathan660 on 2006-03-17
I wanted to give these mail clients a try, so I set them up with my Gmail account, however, I am having problems getting my mail. I can connect just fine, however, These clients cannot recognize all of my emails in my inbox. I have 800 emails in it right now, but they could only see about 31 at first. Eventually I got them to see some more (I'm at 400 something right now), but they still do not my mail. In fact, they do not see the test emails I sent using those clients. I think I got evolution to start downloading more files, but it then gave me an error when trying to download more emails. I'm not at my computer right now, but I think it either said the inbox or the email was too big. Is there any way to fix this?

---

### Post by leviathan660 on 2006-03-17
alright, here is the error message:
Cannot append message to mbox file: /home/ian/.evolution/mail/local/Inbox: File too large

any ideas anyone?

---

### Post by dcstar on 2006-03-17
[QUOTE=leviathan660]alright, here is the error message:
Cannot append message to mbox file: /home/ian/.evolution/mail/local/Inbox: File too large

any ideas anyone?[/QUOTE]
Firstly, do you have sufficient disk space on your filesystem?

Secondly, does your filesystem have a limit on individual file sizes (like the 2G limit on FAT)?

Keep in mind that **all** your Inbox mail messages are in one file, so it is usually good practice to create sub-folders to split these up.

---

### Post by leviathan660 on 2006-03-17
Yeah, I have 16 GB left for my Home folder, I should have enough space. Also, I moved alot of my emails to my different folders, but the error still persists.

---

### Post by sajal on 2008-07-15
This reply might be 2 years late... but i faced a similar thing recently.

When the import gets stuck, i believe evolution wouldnt even open up.. so here is what i did.

1) open the mbox using mutt . Delete few unwanted emails (specially ones with large attachments)
2) open evolution and stop the syncing process.
3) divide the mails into folders.

AFAIK the problem is due to size limit per file in evolution.

---

