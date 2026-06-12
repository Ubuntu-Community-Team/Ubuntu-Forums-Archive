---
title: "Symlink multiple folders"
date: 2011-11-10
forum: General Help
---

### Post by Sutur on 2011-11-10
Hello!

Is it possible to symlink the contents of more than one folder to a single united folder? I have videos scattered in different places and it's a pain trying to find a specific one in 4-5 different places.

Or, any suggestions as to a workaround?

---

### Post by llamabr on 2011-11-10
you could link the CONTENTS of a bunch of folders into one folder, but not a bunch of folders into one folder.

I do not know if ln will allow you to do them as a batch, or if you'll need a short script.

---

### Post by Sutur on 2011-11-10
> **llamabr said:**
> you could link the CONTENTS of a bunch of folders into one folder, but not a bunch of folders into one folder.

I do not know if ln will allow you to do them as a batch, or if you'll need a short script.

Oh you mean symlink each and every file, in each and every folder, to that one folder?
Yes...that would need a script run every time the directory is opened, something like this?:

[LIST=1]
[*]Delete contents of main folder
[*]Symlink all files from each folder
[*]Open folder in a file manager
[/LIST]

---

### Post by blueridgedog on 2011-11-10
You can mount existing folders in new folders...

If you have:

```
/path/to/foldera
/anotherpath/to/folderb
/yetanotherpath/to/folderc
```

You can:

```
mkdir /home/USER/videos
mkdir /home/USER/videos/foldera
mkdir /home/USER/videos/folderb
mkdir /home/USER/videos/folderc

mount --bind /path/to/foldera /home/USER/videos/foldera
mount --bind /anotherpath/to/foldera /home/USER/videos/folderb
mount --bind /yetanother/path/to/foldera /home/USER/videos/folderc
```

---

### Post by Sutur on 2011-11-10
> **blueridgedog said:**
> You can mount existing folders in new folders...

If you have:

```
/path/to/foldera
/anotherpath/to/folderb
/yetanotherpath/to/folderc
```

You can:

```
mkdir /home/USER/videos
mkdir /home/USER/videos/foldera
mkdir /home/USER/videos/folderb
mkdir /home/USER/videos/folderc

mount --bind /path/to/foldera /home/USER/videos/foldera
mount --bind /anotherpath/to/foldera /home/USER/videos/folderb
mount --bind /yetanother/path/to/foldera /home/USER/videos/folderc
```

That's nice, but here's what you're saying:


```
FolderA -> LinkedFolderA
FolderB -> LinkedFolderB
FolderC -> LinkedFolderC
```

And here's what I was asking for:

```
FolderA -> LinkedFolderA
FolderB -> LinkedFolderA
FolderC -> LinkedFolderA
```

---

### Post by blueridgedog on 2011-11-10
It is the closest I can get.  You will have folderA, B and C inside a new folder of your choosing.  Not perfect, but one approach.

---

### Post by SeijiSensei on 2011-11-11
If all you want to do is create a folder that contains symlinks to other folders, that's simple.  

```

mkdir MyVideoFolder
cd MyVideoFolder
ln -s /path/to/folder1 localnameforfolder1
ln -s /path/to/folder2 localnameforfolder2
[etc.]

```

That's so obvious that I must be missing something about your request.

Files and directories are essentially identical on POSIX-compliant filesystems like ext2/3/4.

---

