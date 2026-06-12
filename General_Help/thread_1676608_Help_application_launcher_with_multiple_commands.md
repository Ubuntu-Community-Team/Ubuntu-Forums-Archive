---
title: "Help: application launcher with multiple commands"
date: 2011-01-27
forum: General Help
---

### Post by AndreMadsen on 2011-01-27
Hi, I created a application launcher (type:terminal) to replace the index.php on my apache server (/var/www/) with the index I keep updated on my desktop. This is the exact script I'm using on the launcher:

"sudo rm /var/www/Index.php && cp /home/andre/Desktop/Index.php /var/www/"

My idea was the launcher would delete the current file at /var/www/, and then copy the file on /home/andre/Desktop. 

But its not behaving properly, it is deleting both the file in my /var/www/ AND my desktop. 

Can anyone shed some light on the subject for me? Really apretiate it.

---

### Post by Habitual on 2011-01-28
try it in a bash/shell script with this content:

```
#!/bin/bash
sudo rm /var/www/Index.php 
sudo cp /home/andre/Desktop/Index.php /var/www/
```

save it as say ~/move_index.sh

in a terminal, 
chmod 700 move_index.sh

and then create a desktop launcher to run "gnome-terminal -e /home/**your_username**/move_index.sh" (without the quotes)

That should get you started.

---

### Post by AndreMadsen on 2011-01-29
Thanks a bunch. Solved this problem and a bunch of others I was having! Thumbs up!

---

