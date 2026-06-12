---
title: "Does encrypted /home stop ssh access on lan?"
date: 2010-09-22
forum: General Help
---

### Post by pgibson on 2010-09-22
I've upgraded to my old dell from Xubuntu 9.10 to Xubuntu 10.04 and set up separate /home partition.  I chose to encrypt the /home folder when I installed. I'm wondering if that's the quick answer for why I can no longer sftp from my Ubuntu Jaunty laptop.  

Both machines are on my desk, and I've been happily using ssh to get files between them before this. The Xubuntu machine has openssh server and client installed, the Jaunty machine has only ever had only the ssh client.   Now I get a popup saying "Could not open location ..." and the sftp address, and "Host key verification failed."  

I've not done much with this new install, so I don't mind just re-installing again.  I don't need an ecrypted /home, but I do want very much to be able to continue to ssh into that machine.

Is it my encrypted /home that's causing this?

---

### Post by pgibson on 2010-09-22
No takers?  Okay.  I'm going to get rid of the encrypted /home partition, which is to say that I'm going to reinstall Xubuntu 10.04.  Later on I'll play with encrypting something unimportant.  I don't think I'm nearly a saavy enough user to have my whole /home encrypted by something as non-GUI as ecryptfs.

---

### Post by spiky001 on 2010-09-22
hi can you ssh in from terminal?

---

### Post by pgibson on 2010-09-22
Alas, no, I wasn't able to get in via the terminal, though I don't remember precisely what the result's wording was, it was a no-go.  I don't think I can try anymore either, gparted has just now completed deleting and reformatting the previous install, and the Xubuntu 10.04 live disk has just confirmed that I have a USA keyboard.:D

Thanks anyway.

---

### Post by CharlesA on 2010-09-22
If /home/ is encrypted then you will have problems using public/private keys to connect.

I assume the same thing would happen if you were using sftp or scp without that user bying physically logged in.

---

### Post by pgibson on 2010-09-22
Yeah, I tried sftp as well and it didn't work either.  It's fine. I look forward to playing with encryption, but it will initially only be playing.  I'll try setting up a private folder within /home using ecrypt.  I've also heard about truecrypt and LUKS (sp?), so I'll look at those too ... Hey Xubuntu install is almost done already.  Yay.  Now we'll see what's truly what on this upgrade.

Peace.

---

