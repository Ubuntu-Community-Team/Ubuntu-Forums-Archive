---
title: "Resume Windows from hibernate and can't see files made by Ubuntu in previous session?"
date: 2010-05-13
forum: General Help
---

### Post by congminh1709 on 2010-05-13
Hello everyone, I want to ask this question.

I have dual boot system on my laptop: Ubuntu 10.04 LTS and Windows Vista SP2.

1/ I boot from Windows --> hibernate.

2/ I boot from Ubuntu --> create some files and folders on Windows partition (NTFS file system) --> shutdown. These partitions are mounted automatically by Storage Device Manager utility.

3/ I resume Windows from hibernate --> I can't see files, folders made by Ubuntu in previous session (stage 2/)?

4/ I restart Windows --> Now, I can see these files, folders.

Why this happens, can I see these files, folders immediately in stage 3/?

Thanks for reading my post.

---

### Post by kevinatkins on 2010-05-13
The reason this happens is that when you hibernate Windows, it writes the system state to a file stored on disk, so that when you bring the system back up, instead of having to go through a complete boot process, the contents of the saved system state are loaded from the file - so it's quicker.

If you boot Ubuntu after having put windows into hibernation and change or create files on the windows partition, the saved system state file will be unaware of those changes so they won't show.

---

### Post by congminh1709 on 2010-05-13
Thanks for replying, "system state" means "RAM", and "a file stored on disk" means "hiberfil.sys"?

Ubuntu changes the content of hard disk directly, but after that, Windows resume and just only load hiberfil.sys (an old system state) to RAM, which doesn't include the changes.

Is this your explaination? So, can I have a solution to refresh the system state without restart?

---

### Post by kevinatkins on 2010-05-13
Yes, system state is the contents of RAM.

I don't know whether there is a solution to what you want. Actually, I'd be slightly cautious about this - a situation where the physical contents of the windows drive differs from the saved system state is not something windows would have been designed to accommodate. It might be safer to shut down windows completely (which, from memory, you need to explicitly ask Vista to to from the sub-menu, rather than clicking the 'Off' button on the menu which merely hibernates) between sessions.

---

