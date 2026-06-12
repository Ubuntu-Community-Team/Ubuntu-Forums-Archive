---
title: "How to auto-execute a script every time a user logs out?"
date: 2010-07-06
forum: General Help
---

### Post by pstein on 2010-07-06
I want to automatically execute a (perl/shell) script every time a user logs out.
So ~/.bash_logout is not suitable because it is execute when I close a terminal window. If there are currently 5 open terminal windows and I close one of them then 
~/.bash_logout is executed although the user is still logged in.
 
So again the question: How can I setup a script for auto-execution at user-logout time?
 
Peter

---

### Post by Brandon Williams on 2010-07-07
[Here](http://ubuntuforums.org/showthread.php?t=1517628&highlight=gdm+logout+script) is a recent thread with the same question.

---

