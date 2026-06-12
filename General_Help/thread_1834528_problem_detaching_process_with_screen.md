---
title: "problem detaching process with screen"
date: 2011-08-27
forum: General Help
---

### Post by junderbr on 2011-08-27
I am trying to run the PMS PS3 media server from my server running 10.10.  I control my server by SSH from my desktop machine so I need to detach the process from the terminal window so that it stays running when I close the SSH connection.  I am able to use screen to run the PMS.sh script detached but the script itself runs a java process which is not detached.  So when I close the terminal it ends the java process on which PMS is dependent, thereby rendering PMS useless.  Any ideas on how to solve this problem would be greatly appreciated

---

### Post by galvatron408 on 2011-08-27
nohup
[http://en.wikipedia.org/wiki/Nohup](http://en.wikipedia.org/wiki/Nohup)

---

