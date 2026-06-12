---
title: "Deja Dup"
date: 2011-06-13
forum: General Help
---

### Post by Trev4106 on 2011-06-13
made a backup before upgrading to 11.04 and when trying to restore keep getting error message

Backup location ‘/media/37C3-067A/backup/duplicity-full-signatures.20110612T164732Z.sigtar.gz’ does not exist.

I can see all the files in the backup folder including the sigtar.gz file. Help!
Thanks
Trev

---

### Post by Rasa1111 on 2011-06-13
Are you sure you havent moved the backup folder to a different location from where you set it when you made the backup? 

The only time I get a message like that.
Is when I try to use the backup from another location than where I made it.

For example;
I make the backup in its own folder on my desktop.
Once the backup is finished, I move it to an external hard drive, and delete the one from my desktop. 

Then, If I try to restore, even if I point it to the external drive, directly where the file is..
I am unsuccessful and get an error message that it does not exist. 

But, If I copy the backup back to my desktop, and then attempt the restore from deja dup, all is successful, without a hitch. 

Sorry if this doesn't help your situation. 
Hope it does though. Good luck.

---

