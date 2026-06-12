---
title: "How mo &quot;move&quot; user folders"
date: 2010-06-19
forum: General Help
---

### Post by Darth_tater on 2010-06-19
I've searched and searched, but i cant find the answer for this.

What i want to do is change the locations of the user folders (specifically music and photos) to a different partition / fstab mount point.

All the guides and answers that i've found say to create symbolic links... but the behavior is not quite as needed.

ln -s /my/media/drive/music/folder /home/me/Music

make a "folder" shortcut inside my /home/me/music folder.

How can i get it so that /home/me/Music just points to /my/media/drive/music/folder

I am sure i almost have it (that it's just some small modification to the ln command)


Please help!

Much appreciated!

---

### Post by KeyserSoze93 on 2010-06-19
Add a line like this to your /etc/fstab:

```

/media/music/music  /home/blah/music    bind    defaults,bind   0 0

```

Then, either reboot or run:

```

sudo mount -a

```

That'll make a bind mountpoint, which allows you to mount one folder into another. Quite useful, and perhaps what you are looking for.

It's more flexible than a symlink, since it means that it is actually a folder for all intents and purposes as opposed to a file.

It would be true about the ln command if it were a file, but hard links don't work for folders, so ln only allows symlinks.

---

### Post by Darth_tater on 2010-06-19
yes!  that is exactly what i needed.  Thanks!

---

### Post by yang925goes on 2010-06-19
1) you can move whole user profiles with usermod. However Documents, Music etc. are just defualt folders used by your DE. Kde allows you to change them under System Settings-> About Me -> Paths. So you can use usermod to move the profile to your mount point and configure your default locations accordningly.

2) Another option is just mount your storage as /home/username etc w/ Fstab. This is probably the easiest and most compatiable, since the defualt locations stay the same from the DE's perspective. Etc. use fstab to mount /dev/sdb as /home/username. 

3.) Not sure, but you can also try symbolic links. with the LN command. Link your mount point to /home/profile/Music etc.

---

