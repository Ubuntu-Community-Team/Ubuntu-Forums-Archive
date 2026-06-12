---
title: "Weird Chars in &quot;ls -a&quot; results"
date: 2009-11-11
forum: General Help
---

### Post by 200mg on 2009-11-11
Hello everyone.  I am having an issue where when I run an ls -al in my home dir, the two bottom entries are a string of strange chars and I cannot figure out how they got there or how to get rid of them.  Check out the bottom 2 results.

```
trace@trace-1:~$ ls -al
total 61124

drwxr-xr-x  2 trace trace     4096 2009-09-08 14:29 .xine
-rw-r--r--  1 trace trace     9619 2009-11-11 12:03 .xsession-errors
-rw-r--r--  1 root  root      9743 2009-09-09 09:05 ?&´?þ???v?ÿþ?04?¸?ë?fÿÿÿB?¶?Ò?¶¤´?$ÿÀ¶Ã]_^[\Ä?
-rw-r--r--  1 root  root         0 2009-08-14 15:40 ????@?&#1681;@8?@?????&#33571;?

```

---

### Post by hwttdz on 2009-11-11
Because they're owned by root you're going to need to sudo rm them.  Any idea what they're from?

Oh and it may be a good idea to edit all but the lines in question out of your previous post.

---

### Post by 200mg on 2009-11-11
Thanks for the reply, I did edit out the unused lines.

I'm really not sure where they're from, and I have tried to sudo rm -r these files and it says they are not a file or a directory. It is weird.

---

### Post by hwttdz on 2009-11-11
Please make sure you understand what you're typing before you try these commands, I don't want you to accidentally delete something you need on my advice. 

It's probably because they have characters which must be escaped.  Try typing "sudo rm -rif \?*", make sure ls \?* gives you only the files in question first.  You can also try "find .|grep "?"" to ensure that you're getting only the files in question.  Then "find . -print0|grep "?"|xargs -0 sudo rm -rif".

---

### Post by hwttdz on 2009-11-11
I've updated these so make sure you are trying to remove only the files in question before you try anything.  

Also maybe try "sudo nautilus" then remove them using the gui.

---

### Post by hwttdz on 2009-11-11
And now thinking to be safest it's probably best to make a directory titled "to_delete" or somesuch, and try to move the files in question to that directory, then remove the directory.  That way if you accidentally move a file you want you can just move it back before you delete the directory.

---

### Post by 200mg on 2009-11-11
hwttdz, 

thanks for the help with this....no matter what i tried cli I could not get them to delete.  I think they may have been temp folders placed there during a cisco anyconnect vpn installation, however I cannot prove this.  Using the gui to delete them did work however and I have run everything, including the vpn, and everything seems to be working.  I find it odd that as root rm -r did not work, but gui did work...Thanks again

---

### Post by alphaniner on 2009-11-11
Double post.

---

### Post by alphaniner on 2009-11-11
What were the commands you used to remove the files via the terminal?  I created file with the same names and had no problems removing them:

```
$ sudo touch '????@?&#1681;@8?@?????&#33571;?'

$ sudo touch '?&´?þ???v?ÿþ?04?¸?ë?fÿÿÿB?¶?Ò?¶¤´?$ÿÀ¶Ã]_^[\Ä?'

$ ls -l
total 0
-rw-r--r-- 1 root root 0 2009-11-11 14:53 ?&´?þ???v?ÿþ?04?¸?ë?fÿÿÿB?¶?Ò?¶¤´?$ÿÀ¶Ã]_^[\Ä?
-rw-r--r-- 1 root root 0 2009-11-11 14:53 ????@?&#1681;@8?@?????&#33571;?

$ sudo rm \?\?\?\?@\?&#1681;@8\?@\?\?\?\?\?&#33571;\? 

$ sudo rm \?\&´\?þ\?\?\?v\?ÿþ\?04\?¸\?ë\?fÿÿÿB\?¶\?Ò\?¶¤´\?\$ÿÀ¶Ã\]_\^\[\\Ä\? 

$ ls -l
total 0
```

And the rm commands aren't as daunting as they appear, thanks to Tab completion.  To get ```
sudo rm \?\?\?\?@\?&#1681;@8\?@\?\?\?\?\?&#33571;\?
```

I simply typed **sudo rm ?<Tab>\?<Tab>**

---

