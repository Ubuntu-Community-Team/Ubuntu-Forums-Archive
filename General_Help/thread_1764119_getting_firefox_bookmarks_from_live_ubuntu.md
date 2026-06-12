---
title: "getting firefox bookmarks from live ubuntu?"
date: 2011-05-21
forum: General Help
---

### Post by 4techx on 2011-05-21
hi guys,

i've managed to mess up my ubuntu and will need to reinstall it, and have backup up everything i need from a live session, apart from the firefox bookmarks. 

does anybody know of a way i can get these? i don't know if they are stored anywhere, or if i can launch firefox in the live session using the bookmarks from the original partition, i haven't been able to get any info using google. i added quite a few important ones recently and would really like to save them.

---

### Post by 4techx on 2011-05-21
i've found something which should solve it, in the home directory i view the hidden files and there are some bookmarks stored in .mozilla/firefox/ 

i'll update this to solved if they are the right ones.

---

### Post by Quackers on 2011-05-21
That file just opens up an empty html page on mine.
I suspect if you go to the top menu bar in FF and click on Bookmarks > Show All Bookmarks.
Then in the new window that opens up click on Import and Backup in the top bar, then on Export HTML you can then navigate to something like a flash drive and it will export an html file to your flash drive.
Then in your new system you can do the same thing but Import them from your flash drive.

---

### Post by 4techx on 2011-05-21
you are right the 'bookmarks' file is empty, they are in fact stored as json files somewhere in there called bookmark backups. 

however i did have a lot of problems with permissions, particularly trying to view them in firefox (because firefox was started in the livesession it was not the right user). but i messed around with the permissions and solved that problem. 

apparently there are extensions which backup for you. thats definitely going to have to be done.

---

### Post by lovinglinux on 2011-05-21
> **4techx said:**
> you are right the 'bookmarks' file is empty, they are in fact stored as json files somewhere in there called bookmark backups. 

however i did have a lot of problems with permissions, particularly trying to view them in firefox (because firefox was started in the livesession it was not the right user). but i messed around with the permissions and solved that problem. 

apparently there are extensions which backup for you. thats definitely going to have to be done.

Bookmarks are stored in *places.sqlite* database file. Bookmarks backups are stored as *json* in the bookmarks folder.

---

