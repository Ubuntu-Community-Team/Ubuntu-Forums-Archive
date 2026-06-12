---
title: "Wrong File Type Association"
date: 2010-04-02
forum: General Help
---

### Post by Zvenne on 2010-04-02
Hello,

I recently discovered that my Ubuntu 9.10 thinks my MP3-files are application/x-executable files. So I can't double click them to get them playing since they show up as executables! While trying to fix this I also discovered that many, almost every, file I had on my computer was the wrong file type. Pictures, music, archives, all was wrong. 
Also I hade two MP3-files where one showed up as an application/x-executable and the other one as unknown. Both files play though.

I did search for answers, found that you could right click/properties/open with tab... But this tab don't exist for me. I only got General and Permissions tab.

I don't know how to proceed, please help me this problem is so annoying!

Thanks in advance!

EDIT: I just discovered that f the file lies directly on the desktop it behaves normally and all, but if I put it in a folder it bceomes an "application/x-executable".

---

### Post by irishbreakfast on 2010-04-02
check the file persmissions. You probably want to be the owner of the file, with read/write access. From a terminal, "ls -la filename" will show the permissions. chown is the command to change the owner and chmod to change the access permissions.

---

### Post by Zvenne on 2010-04-02
I am the owner of the file with full access to the file so I guess that is not the problem.

---

### Post by irishbreakfast on 2010-04-02
What if the file is in your home directory? And is the directory you tested, where it failed, on the same partition?

---

### Post by Zvenne on 2010-04-02
I tried putting it in my home directory but the problem still occurs. I also have tried putting the files on a different partition, the problem is still present although the file now switches from being an executable to being an unknown format.

---

### Post by Zvenne on 2010-04-02
Already checked that, I am the owner of the file, full access.

---

### Post by Zvenne on 2010-04-02
Okay so I think I have found the problem or at least part of it. I tried installing a different File Manager, Thunar, in which the problem was not present. Everything works like a charm in this new File Manager. But since the other one is standard and I prefer that one, PCMan File Manager, I would like to get it working again. Is there anyway to reset it or something? Would a reinstallation help the problem?

---

### Post by irishbreakfast on 2010-04-02
PCMan? Are you using xubuntu? 
If you are using nautilus (ubuntu) I learned that the file associations are in ~/.local/shar/applications. There are two files mimeapps.list and mimeinfo.cache, perhaps one of these is corrupted. 
But removal and install can't hurt either.

---

### Post by Zvenne on 2010-04-02
No I am using regular Ubuntu 9.10. I found the files you said, but there seems to be nothing wrong with them. I also tried to completely remove PCMan and reinstalling it, although the problem persists.

---

### Post by irishbreakfast on 2010-04-02
did you purge, which removes config files as well?
other than that you could try at #ubuntu on freenode.

---

### Post by akakingess on 2010-04-02
If you are working in the X-terminal than I could see PCMan being the default, but as far as I know Nautilus is the default for GUI side of Ubuntu, it is definitely the default compared to Thunar, so you may want to try Nautilus out as well and see if that compares to PCMan for you if you can't get PCMan working properly. Since I haven't personally used PCMan I'm afraid I can't be of any actual assistance, but good luck and let us know what you decide and what the outcome is.

Also, you would definitely have to do a 'purge' upon uninstall of PCMan or you may run into the same problems, if you do it via CLI, it should read something like sudo aptitude pcman -purge ..   Not quite sure of the order, it's been so long since I have had to purge everything for an app.

---

### Post by Zvenne on 2010-04-02
Okay so I solved it this way, I uninstalled PCMan completely and then Nautilus took over everything. Didn't have to do anything else, and now everything works perfectly! 

Thanks for all your help guys!

---

