---
title: "bug.. Folder connection kidnapped"
date: 2012-06-13
forum: General Help
---

### Post by oklokl on 2012-06-13
[http://ubuntuforums.org/showthread.php?t=1999064](http://ubuntuforums.org/showthread.php?t=1999064)
Transmission

The same bugs and ...
The above information is the same bug.
Has been deleted but still occurs.
rm -rf ~/.config/transmission


I found a new bug .... Found the cause. -> Folder bookmarks coupling bug

If you take a screenshot. Move to the end of the specified folder.

Easy to understand.

/123/abc What if there is a folder

/123
I by specifying the path to the folder.
 


/123/abc is connected automatically. (kidnapped)

If

abc123 What if there is a folder

/123/abc/abc123
Continue to connect to the folder.

ex>
/123/abc/
/123/abc/abc123
/123/abc/abc123/1
/123/abc/abc123/1/2
/123/abc/abc123/1/2/3

I have to force the last
 The path is moved.
/123/abc/abc123/1/2/3

I chose a folder. -> /123/abc          but..  -> /123/abc/abc123/1/2/3 (Arrival)



Continue connecting the inside to connect. Connect.

And once connected, a folder, the bug still occurs.

Forced into a specific folder as per kidnapped.

so..

/TTKK If you encounter a bug in a folder named.
Continued ... /TTKK When you click a folder named.
/123/abc is connected to ...

This is my kernel. Linux ubuntu 3.2.0-24-generic #38-Ubuntu SMP Tue May 1 16:18:50 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Thank you.

---

