---
title: "Rsync like incremental backup"
date: 2010-10-20
forum: General Help
---

### Post by machko on 2010-10-20
Hello, i have a question about rsync, hope somebody can answer :)  The thing is, i need some help to move the updated files, and i don't know the rsync know that or not...what i mean is: 
  when rsync is finished the update, or in the meantime - i need to move  the updated files to a different location - like date +%Y%m%d something  or what ..the reason is, because of the development, i need the modified  files, but all of them, not just the last one - so i have to store them  daily, but !! i dont want to store the whole dir - just that few files  which are updated....
  does it make sense? :)

---

### Post by mike555 on 2010-10-20
I'm not sure what you mean, but you might try "Lucky Backup"

---

### Post by P4man on 2010-10-20
Although it should be possible with rsync, Unison is what you are looking for I think. Its in the repo's
[http://www.cis.upenn.edu/~bcpierce/unison/index.html](http://www.cis.upenn.edu/~bcpierce/unison/index.html)

---

### Post by bluefrog on 2010-10-20
rdiff-backup will do the job nicely

---

### Post by oregonbob on 2010-10-20
You should read up on subversion . It is specifically designed to do what you describe.

---

### Post by machko on 2010-10-21
thank you, its perfect

---

