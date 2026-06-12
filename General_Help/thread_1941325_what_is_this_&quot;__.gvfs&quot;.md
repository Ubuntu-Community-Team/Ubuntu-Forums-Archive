---
title: "what is this &quot;??  .gvfs&quot;?"
date: 2012-03-15
forum: General Help
---

### Post by garyed on 2012-03-15
Can anyone explain what is going on with this directory?
I've heard its supposed to be something about gnome virtual file system but root can not even access it. 
If I do an "ls -al" it shows:
> d?????????  ? ?    ?           ?                ? .gvfs

If I do as root "ls -al .gvfs" it shows:
> ls: cannot access .gvfs: Permission denied

Can i just delete it since it appears there's nothing in it?

---

### Post by ajgreeny on 2012-03-15
That is odd!  The **ls -al** command should give you some more output like 
```
total 12
dr-x------   2 *user* *user*     0 2012-03-15 09:02 .
drwxr-xr-x 107 *user* *user* 12288 2012-03-15 14:44 ..
```However, as you have said it is a virtual folder so takes no real disk space, and will just be remade next time that you start a gnome session; try it and you'll see what I mean.  I am not even sure you can delete it; try it and see for yourself.

EDIT: No you can not delete it or send it to the trash, as I rather thought.

See also
[http://en.wikipedia.org/wiki/GVFS](http://en.wikipedia.org/wiki/GVFS)
[http://en.wikipedia.org/wiki/Virtual_file_system](http://en.wikipedia.org/wiki/Virtual_file_system)

---

### Post by garyed on 2012-03-15
> **ajgreeny said:**
> That is odd!  The **ls -al** command should give you some more output like 
```
total 12
dr-x------   2 *user* *user*     0 2012-03-15 09:02 .
drwxr-xr-x 107 *user* *user* 12288 2012-03-15 14:44 ..
```However, as you have said it is a virtual folder so takes no real disk space, and will just be remade next time that you start a gnome session; try it and you'll see what I mean.  I am not even sure you can delete it; try it and see for yourself.

EDIT: No you can not delete it or send it to the trash, as I rather thought.

See also
[http://en.wikipedia.org/wiki/GVFS](http://en.wikipedia.org/wiki/GVFS)
[http://en.wikipedia.org/wiki/Virtual_file_system](http://en.wikipedia.org/wiki/Virtual_file_system)

This is funny, I checked ago a couple hours later & now it shows the same as yours & without even being root I can view it now. Maybe I caught it in a transitional period or something.

---

