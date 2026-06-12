---
title: "Update Errors"
date: 2009-11-19
forum: General Help
---

### Post by Abadon125 on 2009-11-19
Hey everyone. I was trying to get JDK installed yesterday (which I still have not gotten solved) and things went wrong. See the thread linked below for details on that.

What is happening now is that it will not let me run update until I solve this error:
[INDENT]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
[/INDENT]Please see the screenshot below. I tried running the command in terminal and the window on the left shows what happens. It is the error that I keep getting and do not know what to do about. If anyone can help that would be amazing!
Thanks.

[JDK Problem Thread]("http://ubuntuforums.org/showthread.php?t=1331092")

---

### Post by bodhi.zazen on 2009-11-19
That error is a bit odd.

It is telling you to manually download the files, save them in /tmp , and change ownership to root.

You can download the files with firefox as a user, then become root with sudo -i

move the files to /tmp

chown root.root /tmp/file_name

then re-run 

sudo dpkg --configure -a

---

### Post by Abadon125 on 2009-11-19
Awesome, that got rid of that error for now.  All I have to do now is get the JDK to work.  Thanks so much!

---

