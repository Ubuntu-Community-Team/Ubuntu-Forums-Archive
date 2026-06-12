---
title: "How do I figure out hardware related information about my computer?"
date: 2012-09-20
forum: General Help
---

### Post by arroy_0209 on 2012-09-20
I do not remember facts for some hardware related characteristics (e.g., RAM, processor, hard disk capacity, presence/absence of misc cards etc) of my desktop. I vaguely remember some of these but I need to confirm. How do I know these values? Are there commands or some other ways to know?

A second related question: In which directory are the programs installed by me can be found? I need to create back-up of all of these programs. Thanks.

---

### Post by grahammechanical on 2012-09-20
Run this command:

```
sudo lshw -html > hardwareprofile.html
```

That will paste the output of the lshw command into a html document called hardwareprofile.html. You will find it in the home folder and it will open in a web browser window and it will list all available information about your hardware.

Regards.

---

### Post by Zill on 2012-09-20
> **arroy_0209 said:**
> ...A second related question: In which directory are the programs installed by me can be found? I need to create back-up of all of these programs. Thanks.
Linux is *not* Windows and so Linux programs are *not* stored in a single directory as Windows programs are.  The different files needed to run an application are stored in several different directories depending on their function.  A lot depends on *how* you installed the program(s) and so the following two links should help point you in the right direction:
[LIST]
[*][What is the equivalent to the Windows “Program Files” folder?]("http://askubuntu.com/questions/27213/what-is-the-equivalent-to-the-windows-program-files-folder")
[*][Where is the default folder for Apps?]("http://askubuntu.com/questions/60826/where-is-the-default-folder-for-apps")
[/LIST]
Having said that, I suggest that it is rarely necessary for a user to backup installed program files.  It is usually quick and easy to reinstall any required apps again.  If you keep your /home directory on a separate partition then all your data and user config info can remain intact after reinstalling or upgrading the OS.

---

