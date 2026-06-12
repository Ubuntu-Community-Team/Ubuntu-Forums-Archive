---
title: "Bug Report (with workaround): Kmenuedit"
date: 2010-03-26
forum: General Help
---

### Post by Anderson Brasil on 2010-03-26
There is an issue with kmenuedit. It was complaining that it couldn't write to /home/usuariokubuntu/.kde/share/config/kmenueditrc. But even running it with sudo, the behavior was strange (the applications weren't saved at the menu, and everything was very slow - like taking 40 seconds to create a new item at the menu). It seems that the problem was that the file /home/usuariokubuntu/.kde/share/config/kmenueditrc was setted as owner and group as "root". I've changed the ownership and the group of that file to the user owner of home (in my case, usuariokubuntu), and it is working fine now. So, I would life to report this, so developers can fix the issue. I've upgraded a completely clean instalation of kubuntu 9.04 to 9.10, so I don't know if the issue also happens when directly installing 9.10.

Well, the bug is reported and I've registered here the solution to help people around with the same problem. That's all, folks.

UPDATED: I thought that it was fixed, but now it is complaining that he can write to */home/usuariokubuntu/.config/menus/applications-kmenuedit.menu (which also was setted as owned by root). I tried to change the ownership of the file to "usuariokubuntu", just like I did to the other file, but it is showing up the same message. I don't know what is going on, I can't see any issue with permissions going here.* I really could use some help.

UPDATED2: Now I've changed the */home/usuariokubuntu/.config/menus directory, now the owner is usuariokubuntu too. It removed the "can't write to file" message, but it is still not working. When I press "save" at kmenuedit, I get the message "updating system configuration" and a message *"QFile::remove: Empty or null file name" at console. Any modification that I make to the menus don't work at all. =/

BTW, why there are so many files owned by root user inside of the home directory? 

Cheers,

Anderson Brasil.

---

### Post by dcstar on 2010-03-26
> **Anderson Brasil said:**
> There is an issue with kmenuedit.
........
Well, the bug is reported and I've registered here the solution to help people around with the same problem. That's all, folks.
........

Unless **you** have actually reported the bug in Launchpad using the tools provided in every Ubuntu system, then all you have done is waste your time as well as those in this forum.

If you have reported the bug, post the bug number so anyone else with the problem can find it.

---

### Post by Anderson Brasil on 2010-03-26
> **dcstar said:**
> Unless **you** have actually reported the bug in Launchpad using the tools provided in every Ubuntu system, then all you have done is waste your time as well as those in this forum.

If you have reported the bug, post the bug number so anyone else with the problem can find it.

I am new to ubuntu. I have no idea what this launchpad is. Of course that, if it was not the right channel to report a bug, that someone would tell me what would the proper place to do so. 
Also, keep in mind that I am not only reporting a bug, but I am also requesting help for solving it. A system where I can't add any program to the K menu can hardly be considered friendly. So, I really would like to solve that.

Cheers,

Anderson Brasil.

---

### Post by Anderson Brasil on 2010-03-28
Can't anybody help me? I am also wondering, how unlikely is that I may be the only one with the same issue. =/

Thanks in advance!

Anderson Brasil.

---

