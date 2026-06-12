---
title: "Documents folder recovery"
date: 2011-04-26
forum: General Help
---

### Post by sea_dawg on 2011-04-26
Good afternoon,

I have somehow 'disappeared' my Documents folder.

I was working on an Open Office document, when I chose "File/Save As" this is the very unwelcome message that came up:

/home/ray/documents  

does not exist.  

Looking in Places, sure enough it is gone!  Looking in Trash the newest file / folder is April 17.  Today is April 26.

Any ideas on how to get it back?  How I may have done this?

I guess I'll find out how good my backups are.....

I need to hit the road for the rest of the day and may not see your responses until tomorrow.

Ubuntu 10.10 on a Lenovo R61i

Thanks!

Edit:
Well, now I've really embarrassed myself.  I did find the contents of /home/ray/documents.  I'll have to put it down to 'mouse tripping'  

Earlier I had needed to empty out a USB drive so I could use it this afternoon.

1 - Using Nautilus I created a folder in /home/ray/documents called called "8G holder" to hold the contents of the 8GiB USB drive for the evening.

2 - The new folder did not appear to be created, so I did it again.  Moved all of the USB contents over, wiped the USB drive and set it aside for use.

It now seems that through mouse tripping I some how renamed documents, to "8G holder", created a second folder named "8G holder" in the first one.

So now my question is much simpler.  It is OK to rename the top "8G holder" to "Documents" and expect all to return to normal?

Given that Linux is case sensitive should the name be "documents" or "Documents" ?

This one is clearly a wetware (me) problem!

Thanks again.

---

### Post by Krytarik on 2011-04-26
Glad that you found your data!

Yeah, name it "Documents", and make sure that it's correctly listed in "~/.config/user-dirs.dirs", like this, this is the default config:
```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
[COLOR=Blue][B]XDG_DOCUMENTS_DIR="$HOME/Documents"
[/B][/COLOR]XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```Greetings.

---

### Post by sea_dawg on 2011-04-27
Krytarik,

Thank you for the fast response and clear instructions.  Problem solved!

Sorry for the delay in getting back to you, I've just now gotten back to the computer in question.

---

### Post by Krytarik on 2011-04-27
> **sea_dawg said:**
> 
Sorry for the delay in getting back to you, I've just now gotten back to the computer in question.
Yeah, I was assuming that anyway, since you foretold that.

You're welcome!

---

