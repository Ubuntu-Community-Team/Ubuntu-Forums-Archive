---
title: "grub boot uuid incorrect?"
date: 2011-10-29
forum: General Help
---

### Post by adza on 2011-10-29
hi there, 

after fresh install of 11.10, system boots to grub rescue prompt only with message 'UUID doesn't exist for xxx-xxx-xx' etc... 

I've check the grub.cfg file and it has the correct entry listed for the location of /boot.. so i'm wondering where grub is getting this incorrect UUID from in the boot sequence? 

Anyone had similar issues to this?? Is there other points in grub i need to check other than /boot/grub/grub.cfg?

---

### Post by oldfred on 2011-10-29
Separate /boot confuses the issue a bit with standard desktops.

Post this to see where everything is at:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

