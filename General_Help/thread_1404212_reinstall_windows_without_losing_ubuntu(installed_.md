---
title: "reinstall windows without losing ubuntu(installed inside windows on separate partiton"
date: 2010-02-11
forum: General Help
---

### Post by VIKRAM.NOV.14 on 2010-02-11
Hi,

I am using windows vista and ubuntu 9.10.Ubuntu has been installed inside windows on a completely separate partition space.However , i need to uninstall windows vista(in drive C:/) due to some problem but i dont want to lose ubuntu (in drive H:/ but installed inside windows)...Is there a way to do it ?
I am a beginner so please be a bit patient and explicit...
Thanks in advance...

---

### Post by bumanie on 2010-02-11
You could use lvpm to move the ubuntu virtual installation to its own dedicated partition. Look [here]("http://lubi.sourceforge.net/lvpm.html") for details. Wubi is good to allow one to see and use ubuntu - as you seem to like it, why not put it on a separate partition and then you can do what you want with vista - although you may end up bootloader issues (which can usually be sorted out). Just a thought - it may not be what you want, but I don't think it is possible to reinstall windows and keep a wubi installed ubuntu intact, unless the ubuntu installation is moved first.

---

### Post by Mark Phelps on 2010-02-11
This question has been asked many times -- but (not using Wubi myself) I don't know the exact answer and have not seen anyone post with a definitive answer.

The problem you'll have is that Wubi installs Ubuntu in a fashion similar to any other MS Windows app, meaning, it puts entries into the registry, and may (this is not confirmed) write files into various MS Windows directories.

When you remove Windows, you wipe out the registry entries and remove those other files.

What has been suggested is that you write down the specifics of your current Wubi installation (version, drive letter, size) and, after you reinstall MS Windows, reinstall Wubi using the same information.  But ... don't remove the current Wubi installation.

It's possible that Wubi will then simply rewrite the same registry entries and same system files, leaving your installation intact otherwise.

Sorry I can't be more definitive -- but as I said, I don't use Wubi.

---

