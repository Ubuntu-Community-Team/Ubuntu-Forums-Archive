---
title: "Annoying behavior"
date: 2010-08-08
forum: General Help
---

### Post by BASH-full on 2010-08-08
I use Google Desktop to search for table data strings in .doc files that I then paste into the file I'm currently working on.  I use Desktop dozens of times a day for this function.  I didn't know where to go for help on this topic so I came here.  The problem is that when I click on a file that Desktop found that contains the string that I was searching for a warning dialogue box pops up asking me if I want to let Desktop open the file.  I have to click the "yes" button to continue.  After the umpteenth time doing this it gets old.  Fast.

It seems to me that it's Ubuntu that's generating this dialogue and not Desktop or Firefox (Desktop runs within the default browser, in my case FF).  I feel that because of the generic look and feel of the dialogue box.  I included a screenshot of the dialogue box.

Is there any way to stop this unwanted behavior?  Some Ubuntu configuration change or something?  It's really bothersome.  It would be great if there were some way to get the file system to recognize Desktop as having carte blanche permission to open files so I wouldn't have to be constantly clicking on this button all day long.

---

### Post by lovinglinux on 2010-08-09
> **BASH-full said:**
> It seems to me that it's Ubuntu that's generating this dialogue and not Desktop or Firefox (Desktop runs within the default browser, in my case FF).

Google Desktop, is a standalone application and not an extension for Firefox. So it does not run within the browser. What it does is integrate with the browser to search for e-mails, web history and other files. Additionally, the GD settings are configured from a browser page, but the application itself runs in your desktop.

Unfortunately, I'm not running Gnome, but I just installed Google Desktop here in KDE and it works fine. No prompt.

Perhaps you could delete the folder ~/.google/desktop to see if it helps. This will remove all stored GD data and you will probably will need to re-index your files.

---

