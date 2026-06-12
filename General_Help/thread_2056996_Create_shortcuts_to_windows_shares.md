---
title: "Create shortcuts to windows shares"
date: 2012-09-12
forum: General Help
---

### Post by wilnotdie on 2012-09-12
I posted this in the networking section, but perhaps it was the wrong section, as I got no replies lol.  Hopefully this section can help me.


Well I've searched here and there, and couldn't make heads or tails of the solutions. 

When trying to add attachments in Thunderbird, I'm constantly navigating through our file shares to get to the right folder/files.

Currently I have our windows share automounting and it ends up under /home/user/.gvfs/

I want to create some type of shortcut to a specific folder in the server, that I'm able to quickly access from Thunderbird.

I tried creating a Launcher on my Desktop, and I'm able to access it when I double click it, but its not accessible from Thunderbird. 

I tried navigating to that folder and adding a bookmark in places, but it doesn't show up in Thunderbird. 


I'm not exactly sure how to search for something like this. I've tried different keywords and ideas, but I'm having troubles obviously lol.

Ubuntu 10.04
Thunderbird 14

Thanks in advance!

---

### Post by LewisTM on 2012-09-12
Make a symbolic link to your network folder and move it to a convenient location.

In Nautilus, go to your .gvfs directory, select the desired folder and click Edit->Make link [ OR Ctrl-Shift-Drag ] and move it to your target location.

Other approaches:
1) Bookmark your .gvfs, give it a meaningful name like "Network Shares"
2) Drag-and-drop files from Nautilus to Thunderbird.

Cheers!

---

### Post by LewisTM on 2012-09-12
I ran some tests and it seems that the first method, making a symlink, doesn't work in Nautilus (or Thunar) because of some weird restrictions on the .gvfs directory. The story is that gvfs mounts cannot hold special files like symlinks, which conflicts with the file manager's way of creating links in the current directory before moving them.

Doesn't mean symlinking a folder inside .gvfs is impossible. Symlinks can point to anywhere on the file tree.
This kind of command works fine:
```
ln -s /home/<user>/.gvfs/source/folder /home/<user>/target/destination
```
Example:
```
ln -s "/home/lewis/.gvfs/lewis on remotebox/Documents" "/home/lewis/RemoteDocs"
```

---

### Post by wilnotdie on 2012-09-13
Thanks a whole lot!!

That works good.  I guess I should learn to fall back to the terminal if the guy doesn't work.

---

