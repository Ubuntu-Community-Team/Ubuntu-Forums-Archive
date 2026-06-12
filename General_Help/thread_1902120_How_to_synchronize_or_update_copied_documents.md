---
title: "How to synchronize or update copied documents"
date: 2011-12-30
forum: General Help
---

### Post by Catlike on 2011-12-30
I may not be calling the operation by the right name. Anyway, what I have is a LibreOffice Calc ledger which I want to hold on both my desktop and on my laptop taters. (That way, when I'm away from home, I can update the ledger with expenditures, and remain up to date.) 
The issue is synchronizing them. To now, the only way I know how is to boot up both taters, then painstakingly go through the most-recently-used copy of the ledger, copy new items from it, and type them into the other copy of the ledger. I may have made unique entries in BOTH copies of the ledger, which then means I have to be REALLY painstaking and identify what is unique in each copy, then copy lines back and forth. Ugh.
Is there a way that the computers can communicate, compare the ledger copies, copy unique items that are in copy 'A' into copy 'B' and unique items that are in copy 'B' into copy 'A' automatically? 
Thank you. 
I'm using Oneiric Ocelot.

---

### Post by 2F4U on 2011-12-30
After reading the first half of you post I was tempted to either suggest a cloud service such as Ubuntu One ([https://one.ubuntu.com/](https://one.ubuntu.com/)) or tools like rsync. However, after reading the rest of your post I realized that what you really need is kind of a diff functionality for LibreOffice Calc. Unfortunately, I am not aware of such a tool.

---

### Post by Buggrit on 2011-12-30
Hi there, I had a similar problem with two people working on the same spreadsheet independently and then coming back toothed office. We got around this very easily by uploading the sheet to Google Docs - a free cloud-based service from the Google. It now allows both people to update the same sheet, just like you say you would have wanted, but moreover they can do it in real-time, simultaneously and see what eachother are typing as it is being typed! - very handy. You'll need to create a free Google account, but that's quite easy. We actually use the Google Apps service to achieve this and some other team stuff too but from the sounds of it, you don't need to go that far.

I hope this helps

---

### Post by Ex-windows on 2011-12-30
Would Meld Diff viewer work for this? I have been using (learning) it to sync copies of docs and it does work for text documents so maybe it will work for calc docs as well. Just a thought.

---

### Post by Catlike on 2012-01-01
Thank you for replying. I will take a look at the Google Docs functionality.

---

### Post by Catlike on 2012-01-01
I have just added Meld Diff Viewer, and will experiment. Thank you.

---

### Post by dcstar on 2012-01-02
> **Catlike said:**
> 
...........
Is there a way that the computers can communicate, compare the ledger copies, copy unique items that are in copy 'A' into copy 'B' and unique items that are in copy 'B' into copy 'A' automatically? 
Thank you. 
I'm using Oneiric Ocelot.

The **Unison** package will allow you to sync things across two networked machines or a USB drive etc. After the initial sync, it will then only sync the changed files so it can be pretty quick.

You will have to set up your environment so that the two machines can communicate (like Shared folders etc.) and then set up a Unison profile to use when you want to sync.

I have been using this method to make backups of my data to an external eSATA drive in case my main drive totally fails.

---

