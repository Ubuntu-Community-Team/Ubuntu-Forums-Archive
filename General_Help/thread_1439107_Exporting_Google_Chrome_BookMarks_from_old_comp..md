---
title: "Exporting Google Chrome BookMarks from old comp."
date: 2010-03-25
forum: General Help
---

### Post by MonteCarloZ on 2010-03-25
I need help guys and girls. My laptop died about 2 weeks ego but the hard drive is fine and is now in a external usb enclosure. 
I have 2 options to getting to the drive from girl friends laptop.
Option one is to book Ubuntu Live CD and access it from there.
Option two is to boot from that hd with "recovery" mode and jump to command prompt. It will not boot into X obviously because its a complete different computer. 
So what can I do to export my bookmarks, PLEASE HELP ME.

Thank you.

PS: I am a bit of n00b so I need exact command to use.

---

### Post by waynefoutz on 2010-03-25
open up Chrome, hit the shift,ctrl, and B keys all at once, to open the bookmark manager. When that pops up, click on tools along the top, and choose "export bookmarks". navigate it to your desktop, click "save" to save the bookmarks.html file to your desktop. Copy that to an external drive, a thumb drive, or even email it to your self. When you install Chrome on the new computer, repeat everything above, but this time choose "import bookmarks" and have it load the bookmarks.html file. This method pretty much works the same on every browser, and every browser can load that file.

---

### Post by MonteCarloZ on 2010-03-25
I cannot open chrome that is the problem. My laptop is broken, I scavenged the hard drive out of it. The only way I can get to that hd if I boot from Live CD and plug the hd though usb. Or book from the hd on another laptop but X will not start do to diff. hardware.

---

### Post by waynefoutz on 2010-03-25
The only way you are going to get Chrome to generate the Bookmarks.html file is if you open the program. You should be able to do that with a live cd, as long as the OS is the same.

---

### Post by MonteCarloZ on 2010-03-25
I can probably install chrome on live cd. How do I copy chrome data from old hard drive to live cd ?

---

### Post by atomizer on 2010-03-25
According to [this link]("http://webtrickz.com/export-chrome-datasettings-from-windows-to-ubuntu/") , the bookmarks are in the folder ```
/home/[user]/.config/google-chrome/Default

```
the easiest way is with a live cd , browse to the hd and copy the 'Default' folder to a stick. (don't forget to do 'show hidden files' at the 'View' options else you won't see the .config directory)

After new install you can copy them back.

---

### Post by MonteCarloZ on 2010-03-25
Ok thank you sir, let me try that.

---

### Post by rpared01 on 2010-03-25
i had one of my laptops give out on me and the HD was ok, i just pop into another laptop with completely different specs and it booted up just fine.

---

### Post by MonteCarloZ on 2010-03-25
Ok took me a while but here is what I had to do.
Boot into old hard drive from a usb inclosure. Boot via recovery kernel and go into root command prompt since X will not start.
Go to /home/[user]/.config/google-chrome/Default 
There is a Bookmark file and Bookmark.bak file. Bookmark file is write protected but .bak file is not. So I coppied .bak to a thumb drive. Boot into Ubuntu via Live CD. Install Chrome, rename bookmark.bak to just Bookmark. Replace this bookmark file with file that was just created when I installed Chrome.
Viola! My bookmarks are now working, then I do a normal export to html and back that up on the thumb drive again.

---

