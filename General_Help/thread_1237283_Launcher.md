---
title: "Launcher"
date: 2009-08-11
forum: General Help
---

### Post by marjon on 2009-08-11
I have installed the Linux version of Nero in Ubuntu but

when I try to use a launcher I get the following:

Details: Failed to execute child process "/usr/share/nero/mime/kde/x-nero-linux-compilation.desktop" (Permission denied)

Can any one help?

---

### Post by sanderd17 on 2009-08-11
Have you tried to execute the launcher as root?
Copy the launcher to a directory (your desktop by example) right click and get the properties, copy the path you see to a terminal and add "sudo" in front of it. If it works that way you know it's a permission problem and you can maybe change the permissions of the file you mention in your post.

---

### Post by Barafu Albino Cheetah on 2009-08-11
try ```
chmod a+r /usr/share/nero/mime/kde/x-nero-linux-compilation.desktop
```
Don't run it as root ever, or you'll get weird problems.

---

### Post by ad_267 on 2009-08-11
Try running:
```
sudo chmod a+x /usr/share/nero/mime/kde/x-nero-linux-compilation.desktop
```

That will change the file permissions to make it executable. You can enter that command in a terminal from Applications - Accessories - Terminal. 

By the way, the default disk burning application that comes with Ubuntu, Brasero, is very good. I don't see a reason to use Nero myself.

Note: Trying to execute a file as root that is not executable will not help. This is a misconception that I see a lot. Root can't execute a file that isn't executable, although there may be files that are executable for root and not other users. sanderd17's suggestion won't work for that reason, and also because sudo requires running a command from a terminal, you would need to use gksudo in this situation (but don't).

---

### Post by Barafu Albino Cheetah on 2009-08-11
There is no reason to make .desktop file executable, unless there are some esoteric quirks in nero code.

---

### Post by ad_267 on 2009-08-11
> **Barafu Albino Cheetah said:**
> There is no reason to make .desktop file executable, unless there are some esoteric quirks in nero code.

Try it yourself, they do actually have to be executable. 

Drag a launcher from your menu to the desktop, do a chmod -x to it then double click on it.

Edit: Ok that actually brings up a message about the application being marked as "untrusted". I haven't seen that before but I'm pretty sure launchers do actually have to be executable.

---

### Post by marjon on 2009-08-12
> **ad_267 said:**
> Try running:
```
sudo chmod a+x /usr/share/nero/mime/kde/x-nero-linux-compilation.desktop
```

That will change the file permissions to make it executable. You can enter that command in a terminal from Applications - Accessories - Terminal. 

By the way, the default disk burning application that comes with Ubuntu, Brasero, is very good. I don't see a reason to use Nero myself.

Note: Trying to execute a file as root that is not executable will not help. This is a misconception that I see a lot. Root can't execute a file that isn't executable, although there may be files that are executable for root and not other users. sanderd17's suggestion won't work for that reason, and also because sudo requires running a command from a terminal, you would need to use gksudo in this situation (but don't).
Thanks ad_267 it works great.
Regards,
Marjon

---

