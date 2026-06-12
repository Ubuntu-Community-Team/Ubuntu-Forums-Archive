---
title: "File permissions issue"
date: 2011-05-05
forum: General Help
---

### Post by Cyked on 2011-05-05
I setup apache2 mods for streaming music and am using a symlink to the music that is on a mounted drive on a windows 7 drive.  I have another directory in apache2 like this that works perfectly fine.

I did all the install for the apache2 music mod, created what I needed to in httpd.conf.  Created the symlink as "s".  The default for the music mode is localhost/music.  So I go there in the browser, works fine.  As soon as I hit the symlink "directory" I get 403 Forbidden "You don't have permission to access /music/s/ on this server."  

I checked permissions, they are the same (see below).  I removed the auth digest settings in httpd.conf, and I still get 403 Forbidden.  What am I overlooking?  I'm not seeing anything in security on the windows box that makes sense that it would be causing this and I don't remember having to do anything special on the windows box for the other drive when I set up that symlink.

Here are the permissions.  The "works" ones are for the symlink I've used for months.  The other is the new one I setup for music.

```

*works*
lrwxrwxrwx 1 root    root       23 2011-04-25 20:25 s -> /mnt/mntpnt1/pics/
*doesn't work*
lrwxrwxrwx 1 root    root       24 2011-05-05 11:31 s -> /mnt/mntpnt2/MP3/


here are some sub-directories.
*works*
drwxr-xr-x 1 root root   28672 2011-02-14 20:21 images
*doesn't work*
drwxr-xr-x 1 root root       0 2008-01-19 10:24 Warren G

```

---

### Post by Cyked on 2011-05-05
This is in the apache error.log

 Symbolic link not allowed or link target not accessible:

does that mean its not permissions, or it still could be?

---

