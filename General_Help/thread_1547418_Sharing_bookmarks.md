---
title: "Sharing bookmarks"
date: 2010-08-06
forum: General Help
---

### Post by xdeathcorex on 2010-08-06
How do i share bookmark between Windows' Firefox and Ubuntu's Firefox? means if i bookmarked a link in Windows and when i logged in ubuntu i can see it without having to backup bookmarks in the first place and restore it in ubuntu.

is there any way to share it? or just backup and restore? pfft

---

### Post by Rendrago on 2010-08-06
I have not tried this and don't know if it works but here goes.

Well in Ubuntu your bookmarks are stored in an HTML file:

```
~/.mozilla/firefox/<your_profile>/bookmarks.html
```

And in Windows they are usually in:

```
C:\Documents and Settings\<User>\Settings\Favorites\
```

So in Ubuntu Firefox, you could set your homepage to:

```
/media/<UUID of Windows hard drive or partition>/Documents and Settings/[User]/Favorites
```

In Windows, you would have to be able to see the Ubuntu file system and then set the Firefox homepage to something like:

```
/home/user/.mozilla/firefox/<profile>.default/bookmarks.html
```

That's just my ten minute guess for something that I would never ever do.

But if that's your fancy, have fun.

---

### Post by colin.p on 2010-08-06
Or just install the add-on xmarks in Firefox, both in ubuntu and windows. I have it in 2 different computers, 3 different OS's and even have it installed in any guest OS in virtualbox, that I run.

---

### Post by lovinglinux on 2010-08-07
Use [Firefox Sync]("https://addons.mozilla.org/en-US/firefox/addon/10868/"). Xmarks will also do, but Firefox Sync will come installed by default on Firefox 4.

> **Rendrago said:**
> ```
/home/user/.mozilla/firefox/<profile>.default/bookmarks.html
```


That file does not contain bookmarks anymore, since version 3 of Firefox. They are stored on a database now.

---

### Post by WorMzy on 2010-08-07
You can use the same profile for both Windows and Ubuntu. If you don't mind mounting your Windows partition every time. If you have a dedicated partition for file sharing between Windows and Linux that gets automounted at boot, then move your profile there, then point both Window's Fx and Ubuntu's Fx at it. I have seven Operating Systems on my machine, and they all use the same Firefox profile.

(I also have Xmarks installed to sync my bookmarks with other PCs I use)

---

### Post by Ginsu543 on 2010-08-07
+1 for Xmarks.

---

### Post by lovinglinux on 2010-08-07
> **WorMzy said:**
> You can use the same profile for both Windows and Ubuntu. If you don't mind mounting your Windows partition every time. If you have a dedicated partition for file sharing between Windows and Linux that gets automounted at boot, then move your profile there, then point both Window's Fx and Ubuntu's Fx at it. I have seven Operating Systems on my machine, and they all use the same Firefox profile.

That can be a problem if the user has extensions that are platform dependent.

---

### Post by WorMzy on 2010-08-07
Possibly, depending on how they work. I use a couple of "windows only" extensions on my Linux OS' without any problems (although a couple of my extensions only work correctly on Linux, due to them loading/storing info in files with Unix based paths, e.g. /media/Terastore/quicknotes/note1.txt)

For the most part, it works fine.

---

### Post by lovinglinux on 2010-08-07
> **WorMzy said:**
> Possibly, depending on how they work. I use a couple of "windows only" extensions on my Linux OS' without any problems (although a couple of my extensions only work correctly on Linux, due to them loading/storing info in files with Unix based paths, e.g. /media/Terastore/quicknotes/note1.txt)

For the most part, it works fine.

The extension install file has an element for the target platform like this:

```
<em:targetPlatform>Linux</em:targetPlatform>
```

If the developer doesn't specify the target, then Firefox considers it cross-platform. Some authors might specify the target as Windows only, because they haven't tested it on other platforms or because they actually don't work in other platforms.

The Unix based paths are not much of a problem, because the extension API allows to declare relative paths to the Profile folder and Firefox determines the correct location based on the system architecture. Nevertheless, there are some functions that are different between platforms and most importantly, there are extensions with binaries that are not cross-platform.

Additionally, Firefox on Windows has different behaviors. For instance when you change an extension preference in Linux, it is applied immediately by default, while in Windows, you need to click the "OK" button, otherwise the preferences are not changed. Some extensions rely on this instant change, so most of the time I need to add **instantApply="true"** to force the Windows version to work properly.

Bottom line, I wouldn't recommend. Is better to use a sync tool like Firefox Sync, which can sync bookmarks, passwords, preferences, tabs and history.

---

### Post by WorMzy on 2010-08-07
Well, I've been doing it for several years with various versions of Windows and Linux, different versions of Firefox and ~30 extensions, and I've yet to encounter a problem outside of different filepaths.

Either I'm incredibly lucky, or you've just been using very OS specific extensions. ;)

---

### Post by lovinglinux on 2010-08-07
> **WorMzy said:**
> Well, I've been doing it for several years with various versions of Windows and Linux, different versions of Firefox and ~30 extensions, and I've yet to encounter a problem outside of different filepaths.

Either I'm incredibly lucky, or you've just been using very OS specific extensions. ;)

I guess you are lucky. Depends on the type of extension you use too. I have 79 extensions installed and several would not work in Windows.

---

