---
title: "Can't login to Ubuntu"
date: 2010-01-30
forum: General Help
---

### Post by acl123 on 2010-01-30
I was using Myth TV to watch the women's final of the Australian Open and just as Serena Williams completed her championship winning shot, dropping to her knees in triumph, the picture froze. I pressed escape, and could get back to the MythTV menu but when I selected Watch TV, all my channels were gone. I was also getting other weird behaviour which I cannot recall.
Anyway, I pressed Ctrl-Alt-Backspace and dropped to the login screen.
But now, even after resetting, I can't login to Ubuntu using Gnome!
I put my username and password in, then the screen goes black, and then I am dumped back at the login screen without any message.
If I press Alt-F1 I can login at the console. So the problem is not my password, it must be Gnome.
What can I do?

---

### Post by blueshiftoverwatch on 2010-01-30
After logging into the command line enter the command **ps -e**. This will bring up a list of every process running on your system. Generally process names will be somewhat self explanitory.

You can kill a bad process by typing kill <insert_processes_number>. Also, by adding a number modifier (kill -1 through -9) you can tell your system how quickly/forcefully you want the app killed. You can move up and down the list of processes running (because, likely the list of processes will be longer than what can be listed on your monitor) by hitting shift+up/down.

---

### Post by acl123 on 2010-01-30
Wow the problem was because of lack of space!
Man Ubuntu needs to fix this! What a terrible experience!

---

### Post by blueshiftoverwatch on 2010-01-30
> **acl123 said:**
> Wow the problem was because of lack of space!
Man Ubuntu needs to fix this! What a terrible experience!
Do explain.

---

### Post by acl123 on 2010-02-04
It seems MythTV actually records everything you watch all the time!

I had had the tennis on all afternoon, and gradually the hard disk had filled up by over 20 gig. It got to within a couple of free megabytes and blew up.

After resetting and returning to the login screen I was getting the bizarre behaviour outlined above - i.e. I would try to login but was simply getting dumped back at the login screen with no explanation.

I ran the disk space cleaner under safe mode, which freed up enough space for me to login again.

The weird thing for me next (I still didn't fully realise what had happened), was watching my hard disk space gradually climb from 200MB free to over 20GB free, as the MythTV Backend cleaned out the temp recordings folder.

---

