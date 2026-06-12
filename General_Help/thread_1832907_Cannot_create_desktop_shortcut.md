---
title: "Cannot create desktop shortcut"
date: 2011-08-25
forum: General Help
---

### Post by otester on 2011-08-25
I've tried the following methods:

1. Dragging the favicon to desktop.

[COLOR="SeaGreen"]Result:[/COLOR] Does nothing.

2. Right-click and "Create launcher..."
--Type: Application
--Name: x
--Command: /usr/bin/firefox [www.google.co.uk](www.google.co.uk)
--Comment: <left blank>

[COLOR="SeaGreen"]Result:[/COLOR] Gives me this error:

"Failed to create file '/home/x/Desktop/x.desktop.NN5O0V': Read-only file system"

3. Same as #2 but "firefox www.google.co.uk" inside "Command:" bit.

[COLOR="SeaGreen"]Result:[/COLOR] Same as #2.


Ubuntu 11.04 64-bit

---

### Post by MegaLoler on 2011-08-25
Are you able to make them elsewhere?  If so maybe your desktop permissions were somehow set to read only.

---

### Post by tzily on 2011-08-25
> **otester said:**
> 
"Failed to create file '/home/x/Desktop/x.desktop.NN5O0V': Read-only file system"


you're not reading the error
it says Read-only file system
you need read+write permissions

try gsudo nautilus and modify your permissions from properties for your folders/desktop ;) or modify your user privileges if they are not set from user settings

---

### Post by otester on 2011-08-25
> **MegaLoler said:**
> Are you able to make them elsewhere?  If so maybe your desktop permissions were somehow set to read only.

Tried elsewhere; home folder, documents, music, pictures, videos etc.

Still won't work.

Also when I open some applications (mostly ones that came with ubuntu) the window opens but it is white.

> **tzily said:**
> you're not reading the error
it says Read-only file system
you need read+write permissions

try gsudo nautilus and modify your permissions from properties for your folders/desktop ;) or modify your user privileges if they are not set from user settings

Like I said to previous quote, turns out terminal window is blank (not opening) as well :(

Gimp gave me this error:

> It appears that you are using GIMP for the first time.  GIMP will now create a folder named '/home/x/.gimp-2.6' and copy some files to it.

Creating folder '/home/x/.gimp-2.6'...
Cannot create folder '/home/x/.gimp-2.6': Read-only file system


---

### Post by tzily on 2011-08-25
find your user settings then and modify privileges if you get a password prompt

---

### Post by otester on 2011-08-25
> **tzily said:**
> find your user settings then and modify privileges if you get a password prompt

This fixed it, thanks! :popcorn:

---

