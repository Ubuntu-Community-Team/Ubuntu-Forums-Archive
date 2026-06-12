---
title: "Can't login when press CTRL + ALT + F1"
date: 2009-07-23
forum: General Help
---

### Post by fernandoc1 on 2009-07-23
I was playing ZSNES at full screen mode on Ubuntu Jaunty when suddenly the program stopped working and all the key strokes in graphic mode were not responding - ALT+TAB CTRL + ALT + DEL and etc. I think that the application froze the X server.
Since Jaunty has no more CTRL + ALT + Backspace, then I decided to press CTRL + ALT + F1 to try to kill the application, but I couldn't login with my account. Why did it happened?
It tells me that login is incorrect. It's not possible that I'm getting crazy to type my login incorrectly, becouse I use it every day!:confused:

---

### Post by philcamlin on 2009-07-23
Try booting into recovery mode. After you get to a shell, enter:
 ls /home
 Your username should appear in the results. Then, enter:
 passwd <username>
 and follow the prompts. Note: your password will not appear, not even as ***** as you type it.

---

### Post by fernandoc1 on 2009-07-23
How can I boot in recovery mode?
In this case, I'm already in a session, but it is frozen by an application.

---

### Post by fernandoc1 on 2009-07-23
Problem solved!
That is a distraction of mine that caused this.
When we switch to the command line terminal using ctrl+alt+f1, the num lock is switched off, and I didn't realized it.
Sorry about the post.

---

