---
title: "Problem Sharing MySQL databases between Ubuntu and Windows 7"
date: 2011-07-24
forum: General Help
---

### Post by joshmo on 2011-07-24
Hello, I have managed to share my mysql databases between windows and ubuntu. However, I have a problem with the ibdata and iblogfile files. They cannot be shared between the two OS's, I suspect because the status or info in the files changes on each run or start of the mysql server. So because of this, I decided to make different folders for both OS's for their ibdata and iblogfile files but the issue I am facing here is that a database created in windows cannot be opened in Linux and vice verser, which I suspect is the same reason the same files cannot be shared. Is there any way around this issue?(I am using Ubuntu 11.04)

[Edit]
The Database can be opened, tables can be seen but tables cannot be accessed. I get the error "table does not exist" in either OS

---

### Post by mikejonesey on 2011-07-24
i didn' think this is posible (different fstypes), am interested...

---

### Post by joshmo on 2011-07-24
just posted the same question here [http://forums.mysql.com/read.php?22,428137,428137#msg-428137](http://forums.mysql.com/read.php?22,428137,428137#msg-428137) in case someone bumps into it...:)

---

