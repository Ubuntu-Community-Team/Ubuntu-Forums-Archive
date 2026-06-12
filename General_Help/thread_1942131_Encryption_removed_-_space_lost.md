---
title: "Encryption removed - space lost"
date: 2012-03-16
forum: General Help
---

### Post by d3ngar on 2012-03-16
Hi,

I recently removed the home folder encryption that I had on my laptop. 
I did this by copying the files into a new unencrypted folder and then removing all the encryption packages and renamed the folders. 
My new folder, unencrypted, became my home folder and the home folder a backup.
I rebooted and deleted the old folder.

This worked like a charm, but it seems I didn't free up the memory from the encrypted folder...

I can't figure out where this encrypted file system might be stored. Could someone give me some advice?

Thanks!

---

### Post by d3ngar on 2012-03-18
Thought I bump this up, as no reply was posted

---

### Post by d3ngar on 2012-04-18
> **d3ngar said:**
> Hi,

I recently removed the home folder encryption that I had on my laptop. 
I did this by copying the files into a new unencrypted folder and then removing all the encryption packages and renamed the folders. 
My new folder, unencrypted, became my home folder and the home folder a backup.
I rebooted and deleted the old folder.

This worked like a charm, but it seems I didn't free up the memory from the encrypted folder...

I can't figure out where this encrypted file system might be stored. Could someone give me some advice?

Thanks!
Okay, I have found how to get the space back:

basically the encrypted folders are stored in the /home/ directory. There is a hidden folder called encrypt_hidden with all the encrypted files and folders in it.

If you have removed all the encryption packages and your system is working fine - and you are sure about what you are doing, you can delete that folder...

---

