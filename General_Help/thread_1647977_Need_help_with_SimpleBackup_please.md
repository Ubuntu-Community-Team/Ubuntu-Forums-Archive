---
title: "Need help with SimpleBackup please"
date: 2010-12-18
forum: General Help
---

### Post by germanix on 2010-12-18
Hi all, I need to back-up my /home approx. once a week and for this reason I installed SimpleBackup to take care of this. I want the app to back-up to my external drive. This is a new drive which I formatted to ext4 and named it UbuntuBU. Setting up the Simple Backup suite and under the Tab "Destination" I choose "use custom local backup directory" and point the program to the partition I want on the external drive. I then get the following message:
"The selected destination is not writable with current permissions. Backups cannot be stored there"
Question: How and where do I now need to change the permissions so that I can backup to this drive?  How do I solve this problem?

---

### Post by byStanderone on 2010-12-18
...haven't tried simplebackup as of yet, but i'd suppose the external drive is mounted before you did the backup process...permission can be done by editing the drive properties..

---

### Post by germanix on 2010-12-18
I cannot change the permissions as I am told that I am not the "0wner" The owner is shown as "Root"

---

### Post by ajgreeny on 2010-12-18
You will need to change the ownership of the folder where the external drive is mounted, so find where that is by plugging in the drive and checking that /media/UbuntuBU exists.

Assuming it does, you should be able to change ownership with ```
sudo chown username:username /media/UbuntuBU
```

You may also need to change the permissions with the chmod command, but I think chown should do it for you.

---

### Post by germanix on 2010-12-18
Hi ajgreeny, Thank you very much for your help. The code you provided was spot-on. I am now happy to say that thanks to your help, the back-up is now in process. It is very nice to have people such as yourself around, willing to help others. Have a nice day and thank you once again.

---

