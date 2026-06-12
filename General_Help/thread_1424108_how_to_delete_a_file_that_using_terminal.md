---
title: "how to delete a file that using terminal"
date: 2010-03-07
forum: General Help
---

### Post by dosox on 2010-03-07
I want to remove a file/directory but can't.
How do i delete a directory using the terminal.
Can someone please add the exact command line so that I can do copy paste.
I've attached a pic & I want to remove that selected directory in the pic [CONTEXT]

---

### Post by warp99 on 2010-03-07
Two ways to do this:

1) With the file manager:

Press alt-f2 and in the run dialog type "gksudo nautilus" to start a root file manager session, then you'll be able to delete these files.

2) At the terminal:

```
sudo rmdir *$dir*
```

This will only remove empty directories. To remove the files and directories at the same time:

```
sudo rm -r *$dir*
```

Be careful with these commands since you don't want to delete vital system files. Please see my signature for more answers to basic questions.

---

### Post by joeknoodle on 2010-03-07
I'm an amateur, so all cautions apply, including backing up important files

The sudo and rm commands are very powerful and can cause security or stability issues.

I don't anticipate this causing trouble, but you never know...

To remove the file from command line:

```

sudo rm -R /usr/lib/rhythmbox/plugins

```Sudo for super user
rm for remove
-R for all subdirectories and files

You'll use your password when prompted.

---

### Post by dosox on 2010-03-07
@warp99 ahh that was easy.. isn't it? :D Thanks a lot warp99

one more question.. through this way can I extract tar files into these directories directly

---

### Post by dosox on 2010-03-07
Thnks joeknoodle :)

---

### Post by nothingspecial on 2010-03-07
> **dosox said:**
> @warp99 ahh that was easy.. isn't it? :D Thanks a lot warp99

one more question.. through this way can I extract tar files into these directories directly

Through sudo.......yes.

sudo give you the power.

See [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/RootSudo")

---

### Post by warp99 on 2010-03-08
> **dosox said:**
> @warp99 ahh that was easy.. isn't it? :D Thanks a lot warp99

one more question.. through this way can I extract tar files into these directories directly

With the file manager:

Open a root nautilus session. Right click on the tarball then choose "Open with Archive Manager". Extract to the directory of your choosing. The files you extract will also be owned by root.

At the terminal:

```
sudo tar -xvf *$tarball* -C *$path_to_directory*
```

The -C parameter allows you to change directory to extract so you don't have to move the tarball into that directory first.

---

