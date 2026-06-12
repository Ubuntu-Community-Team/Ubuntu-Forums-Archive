---
title: "Is there a &quot;sudo followthoserpermissions&quot; command?"
date: 2009-10-29
forum: General Help
---

### Post by Roasted on 2009-10-29
I used sudo to move a file that I owned to a folder owned by root in the terminal. Now the file is in a folder owned by root:root when the individual file is owned by jason:jason.

From what I understand, it doesn't even matter, because I guess files take on permissions of the folder they're in, so with the folder it's in being root:root, the file being owned by me I guess is kind of null.

BUT - it brought up a question. Is there a way I can just navigate to /media/folder and issue a command that makes the permissions, ownership, and group ownership of /media/folder apply to ALL files/folders inside?

I know I can do:

sudo chmod -R 770 /media/folder
sudo chown -R jason:group /media/folder


etc

But I'm just wondering if there's a command to be like, sudo setperms and bam the parent folder just issues everything in its access to the files/folders inside.

---

### Post by Dark_Stang on 2009-10-29
That's what the -R is for, recursive. It takes the folder you targetted, changes it's permissions, and recursively targets everything contained in that folder.

---

### Post by Roasted on 2009-10-29
> **Dark_Stang said:**
> That's what the -R is for, recursive. It takes the folder you targetted, changes it's permissions, and recursively targets everything contained in that folder.

Yeah, I know. I just wasn't sure if there was a command to auto-fill in the parameters, know what I mean? Granted it's easy enough to look and see who owns it, what the group is, and easy enough to figure out the permissions to apply them recursively. I just wasn't sure if there was a command where you just fire it out there and it does the rest.

---

### Post by bribera on 2009-10-29
According to the chmod manpage, you can set a reference file from which it'll copy permissions.

```
       chmod [OPTION]... --reference=RFILE FILE...
       [snip]
       --reference=RFILE
              use RFILE&#8217;s mode instead of MODE values
```

So in action on directory "foo":

```
chmod --reference=foo foo -R
```

That will set all children of foo to the same permissions as foo.

---

