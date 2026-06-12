---
title: "rc.local - can't make it executable"
date: 2012-03-07
forum: General Help
---

### Post by castalla on 2012-03-07
I'm using a live persistent usb - I want to add a line to rc.local.  

If I use chmod -x on rc.local - nothing changes in the permissions.

How do I set the executable value?

---

### Post by 3rdalbum on 2012-03-07
Did you forget to use sudo? You didn't mention sudo in your post.

RC.local should be executable already anyway?

---

### Post by Sergius14 on 2012-03-07
Exactly the opposite...


#sudo chmod +x /etc/rc.local


I think regular users can't modify that file.

---

### Post by castalla on 2012-03-07
Ooops!  The + did the trick!

thanks!

---

### Post by raja.genupula on 2012-03-07
please mark the thread as solved from thread tools . 
Thank you .

---

