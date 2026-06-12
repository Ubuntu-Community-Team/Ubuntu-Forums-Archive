---
title: "Add new icons"
date: 2010-06-15
forum: General Help
---

### Post by sokekoke on 2010-06-15
Hi :-)

I have some .png icons on my desktop i'm trying to drag to my /usr/share/pixmaps library, however i get following message: Error moving file: Permission denied
So i'm talking a wild guess here, but i need to do this in terminal with some kind of basic linux command right? Or maybe i can adjust my permission level somewhere?

Thanks =)


EDIT: Sorry i was too impatient with google.

For others here is solution: [http://superuser.com/questions/133046/permission-denied](http://superuser.com/questions/133046/permission-denied)

---

### Post by Chesamo on 2010-06-15
Mark the thread Solved, please.

---

### Post by NYKevin on 2010-06-15
May I ask why you need the images to be there?  Are you trying to assign one as an icon for a symlink?  Usually you can use the file chooser to pick an icon anywhere in the system.  If you want to put the files there so they don't accidentally get moved, that's simple enough to do, but you should make sure that you actually need to do this.

If you're sure you need to do this, here's how:
```
sudo mv -t /usr/share/pixmaps/ file1 file2 file3...
```Make sure that file1, etc are full paths and not just file names.  Alternatively, do a ```
cd ~/Desktop
``` before issuing the mv command.

Remember that the files are now in /usr/share/pixmaps/, so either  ```
cd /usr/share/pixmaps
``` or use full paths.

Next, you should change the ownership of the files to root:root.  This is accomplished by```
sudo chown root:root file1 file2 file3...
```Finally, do a ```
sudo chmod 644 file1 file2 file 3
```You can press tab in the middle of a path to have the computer try to  autocomplete it.  If it's ambiguous, the computer will complete as much  as it can and then beep.  Press tab again to see what it's confused about.  Type another letter or two and press tab  again to autocomplete again.  If it isn't ambiguous, the computer will complete up to the next  slash.  If it's wrong (not a valid path), the computer will beep and won't give you options when you press tab again.  This can be useful in making sure your paths are correct.

Edit: Apparently he found it on Google while I was writing my post.

---

