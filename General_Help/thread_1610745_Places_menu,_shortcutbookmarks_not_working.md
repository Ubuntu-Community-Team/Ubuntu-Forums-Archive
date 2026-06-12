---
title: "Places menu, shortcut/bookmarks not working"
date: 2010-11-01
forum: General Help
---

### Post by digitography on 2010-11-01
Ubuntu 10.10

The places menu shortcut/bookmarks not working, however "Computer" and "Network" do work, so I can work around, but it's damn annoying.
I tried creating new shortcuts/bookmarks and these don't work either.

This issue has popped up since Friday, till then all was well. Could it be an update has screwed the pooch?

---

### Post by plucky on 2010-11-01
> **digitography said:**
> Ubuntu 10.10

The places menu shortcut/bookmarks not working, however "Computer" and "Network" do work, so I can work around, but it's damn annoying.
I tried creating new shortcuts/bookmarks and these don't work either.

This issue has popped up since Friday, till then all was well. Could it be an update has screwed the pooch?

Alt+F2 and in the window that opens,type **Nautilus**

When the file browser opens,right click on a folder and select **Open with Other Application** and then select **File Browser** the **Open**

You should now be able to open folders in the Places menu.

Good Luck

---

### Post by woodbrick on 2010-11-04
I have the same problem, and the above does not fix. I can open volumes on my desktop, and navigate to anywhere in the file browser once it is open, but I cannot open anything in the "places" menu. I just a message on the panel saying "opening...." and then after a few seconds, nothing. 

I can even drag a shortcut to my home folder from "places" onto the desktop and open it from there, but nothing opens from "places" (except for 'computer' and 'network', as per first post) 

Any ideas?

---

### Post by plucky on 2010-11-04
> **woodbrick said:**
> I have the same problem, and the above does not fix. I can open volumes on my desktop, and navigate to anywhere in the file browser once it is open, but I cannot open anything in the "places" menu. I just a message on the panel saying "opening...." and then after a few seconds, nothing. 

I can even drag a shortcut to my home folder from "places" onto the desktop and open it from there, but nothing opens from "places" (except for 'computer' and 'network', as per first post) 

Any ideas?

Open a terminal and post any output for the command ```
nautilus
```

---

### Post by digitography on 2010-11-04
many thanks for the fix it worked for me.
How do I mark it solved?

---

### Post by thameera on 2010-11-04
@digitography
Click on the "Thread Tools" icon on top of the page and click "Mark thread as solved" in the resulting menu.

---

### Post by woodbrick on 2010-11-04
Hi thanks for the response


> **plucky said:**
> Open a terminal and post any output for the command ```
nautilus
```

There is no output. The command simply opens another file browser window. 

To give a little more background: 

Until recently, nautilus was not working at all on boot-up. I had no desktop icons/ no right-click on desktop. I got around this by:

-Opening terminal, run 'nautilus &'
(home folder then opens, and desktop icons are restored)
-Opening System-Preferences-Startup Applications-Options tab
-click "Automatically remember running applications"
-Reboot (system starts up with desktop icons and right-click working)  
-Go back and uncheck the "automatically remember..." option
-Reboot (system starts up with desktop icons and right-click working) 

Throughout this entire process, "places" has not functioned. Hope this might help. I am keen to try any suggestions you may have. 

Thanks again

---

### Post by plucky on 2010-11-05
Try adding a new **Menu Bar** by right click on panel and select "Add to Panel".
In the window that opens select "Menu Bar" and then "Add".

See if it works from the new menu bar.

If that doesn't work,right click on the new menu bar and select "Remove from Panel".

Good Luck

---

### Post by woodbrick on 2010-11-06
Thanks for the suggestion. It didn't work, unfortunately.

---

### Post by geovino on 2010-12-08
> **plucky said:**
> Alt+F2 and in the window that opens,type **Nautilus**

When the file browser opens,right click on a folder and select **Open with Other Application** and then select **File Browser** the **Open**

You should now be able to open folders in the Places menu.

Good Luck

This worked for me and I'm using Maverick 10.10 64bit,

Thank you. :)

---

### Post by billrandle on 2010-12-09
Using 10.10 and this worked for me too.

---

### Post by mordenm1 on 2011-03-06
> **plucky said:**
> Alt+F2 and in the window that opens,type **Nautilus**

When the file browser opens,right click on a folder and select **Open with Other Application** and then select **File Browser** the **Open**

You should now be able to open folders in the Places menu.

Good Luck

thanks this worked a ton

---

### Post by Cpl.Punishment on 2011-04-24
Thank you! It also worked for me on 10.10. Must have gotten messed up during an update. One thing that was confusing is that you right click any of the files on the right, and then select other application/file browser. Good fix!

---

