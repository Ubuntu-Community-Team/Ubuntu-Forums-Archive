---
title: "VERY strange problem after closing Firefox"
date: 2009-10-27
forum: General Help
---

### Post by Dolomount on 2009-10-27
I recently made the mistake of doing a recursive chown on my /usr/ folder.. That led to several problems, but I was able to solve them.  Now I'm having another problem, and I'm not sure if it's related.

Every time I close Firefox, ubuntu becomes essentially inoperable.  Every file on my filesystem becomes read-only, and I'm unable to open any other programs.  When I try to open any system tools, like network settings or synaptic, all I get is a white box.  When I restart my computer, it will try to do a filesystem check, but it fails every time and won't boot.  The only way around this is by unplugging my laptop so that the filesystem check is skipped (due to it running on battery power).  

Everything works fine if I keep Firefox minimized.. but that's not really a practical solution. I tried to uninstall and then reinstall firefox, but the problem persists.  

If anyone knows anything about this problem, please help!  I just signed up for an account just so I could ask about this problem.

---

### Post by dummy910 on 2009-10-27
I would just rename my "home/USERNAME/**.mozilla**"(notice the . in front of the folder name=hidden) folder, say "**._mozilla**", then restart and then close Firefox to see if the problem still exists as FF will create a new folder named "home/USERNAME/**.mozilla**".

If all is well, just re-import your bookmarks etc from the "._mozilla" folder you renamed earlier.

---

### Post by Dolomount on 2009-10-27
It worked!!  Oh man!  Thanks a lot, I was going to reinstall ubuntu!

---

### Post by dummy910 on 2009-10-27
Glad it worked!

Just remember this concept in the future with other progs... most of them have a hidden(remember the . in front of the file-folder name) user-configuration folder in the /home/USERNAME directories.

---

