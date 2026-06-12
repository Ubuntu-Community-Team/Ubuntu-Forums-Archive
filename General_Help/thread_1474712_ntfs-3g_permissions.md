---
title: "ntfs-3g permissions"
date: 2010-05-06
forum: General Help
---

### Post by Baruch on 2010-05-06
I have a partition loading with ntfs-3g. The problem is that it loads every single file and folder with 777 permissions. My fstab file has the following options listed:
```
auto,rw,nodev,noexec,nosuid,fmask=111,dmask=000,utf8
```
what can I do about it?

---

### Post by cdenley on 2010-05-06
> **Baruch said:**
> I have a partition loading with ntfs-3g. The problem is that it loads every single file and folder with 777 permissions. My fstab file has the following options listed:
```
auto,rw,nodev,noexec,nosuid,fmask=111,dmask=000,utf8
```
what can I do about it?

The question is what do you want to do about it? What permissions should it have? Should everyone be able to read it, and only you write?
```

auto,rw,nodev,noexec,nosuid,fmask=133,dmask=022,uid=1000,utf8

```

Or maybe anyone in the admin group can write, everyone else read.
```

auto,rw,nodev,noexec,nosuid,fmask=113,dmask=002,gid=118,utf8

```

Or only you can read or write
```

auto,rw,nodev,noexec,nosuid,fmask=100,dmask=077,uid=1000,utf8

```

---

### Post by Baruch on 2010-05-06
> **cdenley said:**
> The question is what do you want to do about it? What permissions should it have? Should everyone be able to read it, and only you write?

I'm sorry for not being clear. I want everyone to be able to read/write. I want 666. The problem is that everything is *executable*. I double-click on a text file in the file browser (is it called natiulas?) and it asks me if I want to run it or open it!

---

### Post by cdenley on 2010-05-06
> **Baruch said:**
> I'm sorry for not being clear. I want everyone to be able to read/write. I want 666. The problem is that everything is *executable*. I double-click on a text file in the file browser (is it called natiulas?) and it asks me if I want to run it or open it!
The configuration in your first post should work, then. I just tested it. All files are 666 (everyone can read and write but not execute) and all directories are 777 (full access for everyone).
```

lsb_release -r
apt-cache showpkg ntfs-3g

```

---

### Post by Baruch on 2010-05-06
> **cdenley said:**
> The configuration in your first post should work, then. I just tested it. All files are 666 (everyone can read and write but not execute) and all directories are 777 (full access for everyone).
```

lsb_release -r
apt-cache showpkg ntfs-3g

```

You're right. It does work. I don't know why it wasn't working before. Maybe I hadn't remounted it properly after changing fstab or something similar (originally I had "defaults,utf8"). I have since shutdown and now turned it on again and checked.

Sorry about the waste of time. I appreciate the effort:KS.

---

