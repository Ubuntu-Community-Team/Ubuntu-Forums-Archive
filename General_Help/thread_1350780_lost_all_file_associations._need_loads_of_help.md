---
title: "lost all file associations. need loads of help"
date: 2009-12-09
forum: General Help
---

### Post by exsecrare on 2009-12-09
All file-type associations have been lost. all attempts to fix the issue have failed.

any help on the forums and over ICQ would be greatly appreciated

the problem arose after installing a new theme.

---

### Post by mionescu on 2009-12-09
Can you be more specific? Are you using Ubuntu (gnome) or Kubuntu (kde)? You can not open any file?

---

### Post by t0p on 2009-12-09
Yes, more detail is needed.  I don't know what you mean when you say "all file-type associations have been lost".  Precisely what has been lost?

You said this happened after you installed a theme.  Can you describe exactly what happened?  How did you install the theme?  What happened?  How do you know it was installation of the theme that caused this problem?

---

### Post by gadolinio on 2009-12-09
+1. Please give more information in order for us to figure out what happened.

---

### Post by exsecrare on 2009-12-09
I'm using Ubuntu 9.10 and what i mean is that when i click on a file (mp3, jpg, etc.) it doesn't make the association with any programs. 
for example, when i attempt to open a .jpg it shows the file type as being unknown and doesn't even give me options of recommended programs. It's like this with nearly all file types i've tried. with the exception of .png

file types i've tried: iso, jpg, mp3, wav, bmp.

---

### Post by imtheguru on 2009-12-09
Sounds like a broken mimeapps.list
Check the file ~/.local/share/applications/mimeapps.list

If the associations are empty or broken, create a new user and copy over the above file from the new user to your current user (use /tmp for temporary storage).

> **t0p said:**
> Yes, more detail is needed.  I don't know what you mean when you say "all file-type associations have been lost".  Precisely what has been lost?No further detail is required.

> **mionescu said:**
> Can you be more specific? Are you using Ubuntu (gnome) or Kubuntu (kde)? You can not open any file?Mimetypes are dictated by FreeDesktop.org and are common for KDE, Gnome and XFCE.

Cheers.

---

### Post by mionescu on 2009-12-09
Try to right-click on one of these files, select "Properties", and then go to the "Open with" tab. Are there any applications there? if not, you should be able to add them.

Someone else asked you as well, what theme did you install? How did you install it?

---

### Post by mionescu on 2009-12-10
Is your problem related to 
[http://ubuntuforums.org/showthread.php?t=1349801](http://ubuntuforums.org/showthread.php?t=1349801)
?

---

