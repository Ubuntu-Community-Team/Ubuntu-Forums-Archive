---
title: "Help: How can I ever get rid of trash and free up my /Home???"
date: 2010-11-26
forum: General Help
---

### Post by zhaotianwu on 2010-11-26
I've just installed Ubuntu 10.10. I think there is a big bug here. My 40GB LVM has been quickly filled and I used Accessories=> Disk Usage Analyzer, found that the biggest chunck of stuff was stored in a so called ".loacl" directory. When I open it, I found all my previously deleted files are here. I tried to delete them manually, but they quickly came back, with a changed suffix name each time, e.g. "file A. 2","file A. 2.2","file A. 2.2.2"....  How can I ever get rid of trash and free up my /Home???

---

### Post by WorMzy on 2010-11-26
Open nautilus, press Ctrl+L, and enter ```
trash:///
``` Then click on the "Empty Wastebasket" button.

OR

Open a terminal and run
```
rm -r ~/.local/share/Trash
```

---

### Post by zhaotianwu on 2010-11-27
> **WorMzy said:**
> Open nautilus, press Ctrl+L, and enter ```
trash:///
``` Then click on the &quot;Empty Wastebasket&quot; button.

OR

Open a terminal and run
```
rm -r ~/.local/share/Trash
```

  Thank you for the information. But do I need to manually do this every time? There gotta be something wrong here? Why is dumping garbage so complicated in Ubuntu?

---

### Post by WorMzy on 2010-11-27
If you want to delete things permanently, without having to clear the recycle bin, just press Shift+Del instead of delete.

Of course if you accidentally delete "reallyimportantdocument.odt" with this method, then recovering it won't be easy.

---

### Post by bobcollard on 2010-11-27
> Thank you for the information. But do I need to manually do this every  time? There gotta be something wrong here? Why is dumping garbage so  complicated in Ubuntu? 
Unless the items in the trash are restricted by Permissions it should be simple enough, just right click the trash icon and "Empty Trash"

---

### Post by zhaotianwu on 2010-11-28
> **bobcollard said:**
> Unless the items in the trash are restricted by Permissions it should be simple enough, just right click the trash icon and &quot;Empty Trash&quot;

  I think I used the Suod 700 $Home earlier so maybe that causes the permissions problems? Anyway, it didn't work and every time when I delete the documents in trash folder, it immediately came back, with an added suffix, .2, .2.2, .2.2.2,etc. Could this be virus? Oh my god. It's driving me crazy.

---

### Post by asmoore82 on 2010-11-28
You should have a trash applet, I believe in the lower right corner by default.

---

### Post by Spyderkid on 2010-11-28
I know of a very good program which cleans up unused cookies, caches, files and the waste-paper basket by just a click of a button. You can get it from the Ubuntu Software Centre, It is called **_*BLEACHBIT*_**

---

### Post by WorMzy on 2010-11-28
> **zhaotianwu said:**
> I think I used the Suod 700 $Home earlier so maybe that causes the permissions problems? Anyway, it didn't work and every time when I delete the documents in trash folder, it immediately came back, with an added suffix, .2, .2.2, .2.2.2,etc. Could this be virus? Oh my god. It's driving me crazy.

Deleted items get sent to the waste basket. If you normal-delete an item in the waste basket folder, it goes straight back to the waste basket. Use the trash:/// folder to manage your deleted items instead, the normal-delete is replaced with perma-delete.

Like I said earlier, you can skip the waste basket stage completely by using Shift+Del instead of just Del.

---

