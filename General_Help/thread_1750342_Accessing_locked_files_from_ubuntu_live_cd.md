---
title: "Accessing locked files from ubuntu live cd"
date: 2011-05-05
forum: General Help
---

### Post by kpuz on 2011-05-05
Hello,
I tried upgrading my 10.04 system to 11.04 and the installation hanged at the beginning and now the I can't load into ubuntu 10.04. It was stupid of me to not back up what I had on the drive and now I am stuck. Using the 11.04 live cd I can mount the partition where 10.04 is loaded and can even back up some of the folders in my /home/user/ directory. But some of them are locked and give me this error when I try to copy to an external hdd :  You do not have permission to view the folder.... 

I was wondering if there was a way to get root access to these files so I can copy them. Any help is appreciated.

---

### Post by kpuz on 2011-05-05
Nevermind. Fixed it by using sudo mount through terminal and copied what I needed using the sudo cp -r <directory> <directory> command.

---

