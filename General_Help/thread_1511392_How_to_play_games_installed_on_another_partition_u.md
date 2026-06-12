---
title: "How to play games installed on another partition under wine?"
date: 2010-06-16
forum: General Help
---

### Post by Tumex on 2010-06-16
Hey there guys,
I just got into Ubuntu, so you can bet that I don't know a lot yet but from the looks of it, it looks like I am going to use this OS for most of my needs! :)

However, there is still one need that has not been dealt with yet! And that is... the gaming need! 

Yup, that's right! My question pertaining to this need is, how can I play games from another partition (originally made under Windows) under Wine without having to install the games _**AGAIN**_?

Thanks a lot for the help and much success!
Tumex

---

### Post by mikewhatever on 2010-06-16
Don't think you can. To run under Wine, programs need to be install under Wine.

---

### Post by Tumex on 2010-06-16
> **mikewhatever said:**
> Don't think you can. To run under Wine, programs need to be install under Wine.
Thanks for the quick reply! Do you think that if I copy all the contents from my D: drive (which is my 'Games' drive) to the virtual drive created by Wine, this could work out?

I am however concerned about the registry stuff as some games create parameters in the registry that are REQUIRED for the game to operate properly.

Thanks for the help!

---

### Post by Tumex on 2010-06-23
Bump, I was hoping there would be a way. :)

---

### Post by jwbrase on 2010-06-23
It really depends. On our dual-boot desktop back home, I was able to get certain applications to run under Wine without being moved. The general idea, though, is going to be this: If it depends on registry entries or absolute file paths, it'll need to be reinstalled under Wine. If it only accesses data in its own directory, and only does so through relative paths it should run just as well either way.

EDIT:
[quote="Tumex"]
Thanks for the quick reply! Do you think that if I copy all the contents from my D: drive (which is my 'Games' drive) to the virtual drive created by Wine, this could work out?[/quote]

For games that rely on absolute paths, it will work *as long as* the virtual drives on Wine contain any files it requires at the same paths (for instance, if it expects to have access to C:\Windows\System32\aRandomDLL.dll, then Wine's C: drive will have to contain aRandomDLL.dll in the folder C:\Windows\System32. If the game expects its own absolute path not to change after installation (if it references its own files by absolute paths), then it will need to be installed on the same drive and path under Wine as under Windows). For games that depend on registry entries, there is no way, or, at least, none that is easier than reinstalling under Wine. Also, keep in mind that reinstalling under a different OS on the same machine, or copying an existing install, is a legal gray-area as far as copyright.

---

