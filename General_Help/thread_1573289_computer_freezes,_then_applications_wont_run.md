---
title: "computer freezes, then applications wont run"
date: 2010-09-12
forum: General Help
---

### Post by iochinome on 2010-09-12
Hello all,

a couple of times now, my computer has frozen while I had firefox and eclipse open. when i restart it, firefox will not run because it is under the impression that it is already running; eclipse will start up, but does not allow me to access the necessary workspace because it is under the impression that it is still in use. how can i get rid of these problems?
i tried pkill for firefox, but it does not show up on the list of processes running...

thanks!

---

### Post by Lukas666 on 2010-09-12
FF creates a lock file every time it starts and deletes it when gets closed. Since the file was not deleted when FF crashed, FF thinks it's already running. 

More reading here:

[http://support.mozilla.com/en-US/kb/Firefox+is+already+running+but+is+not+responding](http://support.mozilla.com/en-US/kb/Firefox+is+already+running+but+is+not+responding)

---

