---
title: "Mount ISO on a network share"
date: 2010-07-02
forum: General Help
---

### Post by Asmodai on 2010-07-02
Hey,

I'm trying to mount an ISO file over a Windows network share.
The share is automatically mounted by Nautilus somewhere in ~/.gvfs and I'm trying to mount the image using:

```
sudo mount -o loop,ro -t iso9660 '~/.gvfs/[...]/image.iso' /tmp/iso
```However, I just get a 
```
[...]/image.iso: Permission denied
```When I copy the ISO file over to my local hard disk, it works fine, but not over the network. How come? I don't have write access to said network share, but I don't think that should be necessary anyway.

Any ideas on how to make this work?

---

### Post by gzarkadas on 2010-07-02
If you double-click the .iso from within the nautilus window it is auto-mounted and shows up immediately in `Places' tab at the left part of the window. You can open it then from there with a single click. There is no need to mount it the way you try.

Now regarding why the command you typed fails, it probably has to do with how gvfs is being implemented as a fuse filesystem. I don't know if it can be done; you'll have to research it further. But you could try to explicitly specify the owner in the mount options to be the account inside who's directory the .gvfs exists. Add to the existing mount options the following: `user,owner' and then if it still does not work `uid=<account>,gid=<account>'.

---

### Post by Asmodai on 2010-07-02
I tried to add the options you mentioned, but the permission denied message remains.
However mounting it using Nautilus works great, even over the network. Can't believe this feature was there all the time and I didn't see it.
Thanks for that.

---

### Post by hovrashko on 2011-03-17
I dont think it has been solved, however i figured out how to do it through [furiousisomount]("https://launchpad.net/furiusisomount") and your shear has to be mounted already:

[I][B]>start furiousisomount
>click browse >/home/username/. gvfs/yourmountshear/yourimage
>click mount
done[/B][/I]

to be able to see .files Ctrl+h

hope that helps.

;)

---

