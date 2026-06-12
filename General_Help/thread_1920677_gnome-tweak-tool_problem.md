---
title: "gnome-tweak-tool problem"
date: 2012-02-05
forum: General Help
---

### Post by khaj_vah on 2012-02-05
Hello people,
I am using ubuntu 11.10 with gnome shell and have a problem with gnome-tweak-tool. when i click on it, it does nothing and when i try to open with terminal it gives this error:

Traceback (most recent call last):
  File "/usr/bin/gnome-tweak-tool", line 22, in <module>
    import gi
ImportError: No module named gi


I googled a bit, found some solutions(reinstalled some python-gobject pachages), but still didnt help./
Thanks for spending time on me ;)

---

### Post by Frogs Hair on 2012-02-05
You can try the following .

1. Turn off all extensions if installed and remove the Gnome Tweak Tool .
2. Open Nautilus as root using gksudo nautilus in the terminal .
3. Navigate to File System /usr/share/gnome-tweak-tool .
4. Delete the gnome-tweak-tool file.
5. Close nautilus and reinstall the Tweak Tool.

If there is a problem in the configuration this may remove it .

---

### Post by khaj_vah on 2012-02-06
Thanks for reply but i can not disable them without tweak-tool. Is there any other way to do that?

---

### Post by philinux on 2012-02-06
> **khaj_vah said:**
> Thanks for reply but i can not disable them without tweak-tool. Is there any other way to do that?

Someone else had this see last post too. 
[http://ubuntuforums.org/showthread.php?p=11624982](http://ubuntuforums.org/showthread.php?p=11624982)

---

### Post by khaj_vah on 2012-02-06
> **philinux said:**
> Someone else had this see last post too. 
[http://ubuntuforums.org/showthread.php?p=11624982](http://ubuntuforums.org/showthread.php?p=11624982)

Yeah, thanks. That person is me. I forgot that i posted ;) everything works now

---

