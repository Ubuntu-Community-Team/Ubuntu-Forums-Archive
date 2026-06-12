---
title: "How to install bz2 files"
date: 2010-08-22
forum: General Help
---

### Post by lwalper on 2010-08-22
I've installed VMware Server and am having trouble logging in and doing "other stuff" once I finally do manage to login. A user at the VMware forum suggests that the current version of Firefox has incompatibilities with VMware ... so

I downloaded a previous version (3.0.9)  which was a tar.bz2 file. I have untarred the file into it's own folder and the executable file (firefox) does run the program, but don't I need to "install" this program somewhere? Or am I consigned to navigate the to the file each time I want to use Firefox? Or do I just move the executable to the desktop. It has no regular icon associated with the file and when I double click it a dialog box opens asking if I want to run in terminal, display, cancel, or run the file?

I read the "help" (clicked the little blue ? at the top of the Ubuntu screen) and read the discussion about the file format, but there was no information about installing downloaded tar.bz2 files. Did a Google search and came up with about a million hits, none of the first 50 or so seemed appropriate to the task. Searched the Forum and came up with a lot of "use Synaptic" hits which also don't seem to help much because Synaptic only lists the current version. Stumped!:confused:

BTW I have already uninstalled the current version of Firefox using Synaptic so think I'm ready to install the older version.

---

### Post by ajgreeny on 2010-08-22
Just make a launcher in your menu or desktop for that firefox script and you will not get the dialog box asking you what to do, but it will just open firefox for you.  You can use an appropriate icon for the launcher as well by clicking on the icon top left of the launcher properties dialog.

I have used this method in the past to run firefox and never actually installed, so can't help with that query, though I can assure you that unless you have other users on the computer, there is not a great deal of advantage to installing, compared with running it as user.

---

### Post by lwalper on 2010-08-23
Tried that for version 3.0.9, but still having trouble with vmware so thought I'd get a pre-version 3. Downloaded version 2.0.0.9, untarred the folder, double clicked the appropriate file and nothing happens -- well not nothing = the dialog asking whether I want to run the program pops open, but then nada, zip, nothing. Any other suggestions?

---

### Post by ajgreeny on 2010-08-23
> **lwalper said:**
> Tried that for version 3.0.9, but still having trouble with vmware so thought I'd get a pre-version 3. Downloaded version 2.0.0.9, untarred the folder, double clicked the appropriate file and nothing happens -- well not nothing = the dialog asking whether I want to run the program pops open, but then nada, zip, nothing. Any other suggestions?
I imagine that is a dependency of some sort missing from your system.  You can try running the script in terminal to see any errors with ```
sh /path/to/firefox
```where **/path/to/firefox** is the full pathway to your untarred folder and firefox script.

---

