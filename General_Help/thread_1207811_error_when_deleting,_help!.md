---
title: "error when deleting, help!"
date: 2009-07-08
forum: General Help
---

### Post by lobbert on 2009-07-08
Today when I use tar- to backup my system, I forget to exclude the backup file itself. 
When I realize this point, I close the Terminal to stop tar command. 
Then I find that the backup.tgz file can not be deleted!!!
I changed its permission by chmod 777.
Still can not delete it.
Any ideas to solve the problem??
Thanks

---

### Post by synapsys on 2009-07-08
What command are you using to delete it?

---

### Post by lobbert on 2009-07-08
sudo rm backup.tgz
Is that right?
I am a beginner of ubuntu.

---

### Post by spibou on 2009-07-08
Please do```
ls -l backup.tgz
```and post the output. Do also ```
sudo rm backup.tgz
```and post the output.

By the way this is  good general advice. If you do something and it doesn't work you should post any error messages you see.

---

### Post by synapsys on 2009-07-08
```
sudo rm -rf backup.tgz
```

---

### Post by lobbert on 2009-07-08
Thanks a lot!
It woks now. I change to root account, then use rm backup.tgz. File is deleted.
Thanks again.

---

