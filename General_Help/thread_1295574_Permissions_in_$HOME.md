---
title: "Permissions in $HOME"
date: 2009-10-19
forum: General Help
---

### Post by Unanimated on 2009-10-19
Apparently, everything in my $HOME folder belongs to root, including everything in my Documents, Pictures, Music, and Video folders. I can fix the problem by individually right-clicking the folder and changing the permissions in a sudo nautilus session, but I want a way to do that and apply it to everything inside the folder. In my Music folder, I have a folder with the band name, and then a folder inside with the album name. Both of them belong to root, and clicking 'Apply Permissions to Enclosed Files' doesn't do it for folders, as well. Is there a way I can make *every single file* in my home folder belong to my account at once, without having to individually do it folder-by-folder?

---

### Post by mikewhatever on 2009-10-19
Use 'sudo chown -R username:username' and next time, be careful with changing permissions. Obviously, username is your real login username.

---

### Post by Unanimated on 2009-10-19
Well, what happened was that I installed a new hard drive in my computer and I wanted to make that one the primary one instead of the one that already was, so I installed Ubuntu on that one and kind of copy-pasted my old home folder into my new one. I forgot about permissions.

But to get that command to work, I had to put this in:
```
sudo chown -R username:username /home/username
```
Thanks!

---

