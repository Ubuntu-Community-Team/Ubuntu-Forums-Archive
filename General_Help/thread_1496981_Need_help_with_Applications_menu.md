---
title: "Need help with Applications menu"
date: 2010-05-29
forum: General Help
---

### Post by rtimai on 2010-05-29
Ubuntu 10.01 Lucid

I had a few problems with applications failing to install properly with Synaptic Package Manager which resulted in a slew of launchers in my Applications > Other folder which all delivered error messages. These all had some kind of grey screen icon. I deleted them after uninstalling the applications which failed to install (wine 1.2, wine-gecko 1.2, then later wine 1.0, Wine-gecko 1.0, and winetricks.) I didn't notice that some non-wine applications also were given the grey-screen icon, and accidentally deleted "Archive Mounter." I know that I only deleted the launcher not the application, but don't know how to re-create the launcher in the Applications menu.

Would someone... 
1 - Right-click on the Applications panel, 
2 - Select Edit Menus
3 - Find "Archive Mounter" (probably in "Other" folder) 
4 - Select Properties for the launcher, look at the Properties sheet and tell me what the Archive Mounter command is, so I can re-create the launcher manually? And if you could, the path to the icon too, please. 

Thanks!

---

### Post by dcstar on 2010-05-30
> **rtimai said:**
> Ubuntu 10.01 Lucid

I had a few problems with applications failing to install properly with Synaptic Package Manager which resulted in a slew of launchers in my Applications > Other folder which all delivered error messages. These all had some kind of grey screen icon. I deleted them after uninstalling the applications which failed to install (wine 1.2, wine-gecko 1.2, then later wine 1.0, Wine-gecko 1.0, and winetricks.) I didn't notice that some non-wine applications also were given the grey-screen icon, and accidentally deleted "Archive Mounter." I know that I only deleted the launcher not the application, but don't know how to re-create the launcher in the Applications menu.

Would someone... 
1 - Right-click on the Applications panel, 
2 - Select Edit Menus
3 - Find "Archive Mounter" (probably in "Other" folder) 
4 - Select Properties for the launcher, look at the Properties sheet and tell me what the Archive Mounter command is, so I can re-create the launcher manually? And if you could, the path to the icon too, please. 

Thanks!

Archive **Manager**: file-roller %F

---

### Post by rtimai on 2010-05-30
Thanks, David, but I need the command and path to the icon for Archive MOUNTER, not Archive Manager. This tool allow you to view the contents of an archive (e.g., RAR, ZIP, ISO) persistently as though it were a mounted drive. 

The Archive Mounter launcher appeared in the "Other" folder of my Applications menu. I don't know, it may be located elsewhere on other systems. 

Anyway, I'd really appreciate it if you'd try again. This is not a tricky troubleshooting request, but something anyone could do. I appreciate that you responded to it. 

Roger

---

### Post by s.shawky on 2010-05-30
for archive manager :[COLOR="Blue"] file-roller %U[/COLOR]

for archive mounter : [COLOR="Blue"]/usr/lib/gvfs/gvfsd-archive file=%u[/COLOR]

---

### Post by s.shawky on 2010-05-30
for archive manager :[COLOR="Blue"] file-roller %U[/COLOR]

for archive mounter : [COLOR="Blue"]/usr/lib/gvfs/gvfsd-archive file=%u[/COLOR]

---

### Post by rtimai on 2010-05-30
> **s.shawky said:**
> for archive manager :[COLOR="Blue"] file-roller %U[/COLOR]

for archive mounter : [COLOR="Blue"]/usr/lib/gvfs/gvfsd-archive file=%u[/COLOR]

Thanks so much, s.shawky! In searching for information, I saw clues that it had something to do with gvfs, but there're no man pages for it or similar commands.

Hate to bother you further, but can you provide the path to the icon for this launcher? I need a clue. 

Roger

---

### Post by s.shawky on 2010-05-30
> **rtimai said:**
> Thanks so much, s.shawky! In searching for information, I saw clues that it had something to do with gvfs, but there're no man pages for it or similar commands.

Hate to bother you further, but can you provide the path to the icon for this launcher? I need a clue. 

Roger
no problem
but which launcher do you mean?

---

### Post by rtimai on 2010-05-30
> **s.shawky said:**
> no problem
but which launcher do you mean?

Archive Mounter... Unh... never mind, that part's not so important, as it turns out. Thanks for your help, solved a mystery for me.

---

