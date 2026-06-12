---
title: "Getting Ubuntu to open .txt and .doc files in different apps"
date: 2010-12-10
forum: General Help
---

### Post by peyre on 2010-12-10
I want Ubuntu to open .txt files in gedit (or maybe Mousepad) and .doc files in OpenOffice (or maybe AbiWord), but the OS treats them as the same type of file.  That is, if I tell it to open .txt files with gedit, it'll also use gedit for .doc files--and if I tell it to always open .doc files with OpenOffice, it'll turn around and open .txt files with OO as well.

Note: in case anyone was thinking this is a n00b question, I do know how to change the associations--the problem is that it uses the same association for both types of files.

I realize this is because Linux doesn't rely on file extensions for everything the way Windows does, so I'm not thinking this is some kind of bug in Ubuntu.  But it is possible to get the system to open .doc files with one application and .txt files with another--I suppose it's probably done at the desktop-environment level rather than the OS level.  The reason I know it's possible is I had it working under 10.04--but it broke when I upgraded.  

That wouldn't be a problem, except I didn't think to write down how I did it.  Now I'm having trouble Googling the instructions again, so I thought I'd ask the Ubuntu community.  Does anyone know how to do this?

---

### Post by 73ckn797 on 2010-12-10
Have you "right clicked" over the files and went to "open with other application"? You can tick the box at the bottom to handle that file type always. That works for me. The associated doc or txt files then behave properly after that. See attached screen shot.

---

### Post by peyre on 2010-12-10
:(  That's just the sort of answer I was hoping to head off by saying I know how to change associations, and that the problem is that whichever program I associate .txt with, Ubuntu will open .doc with--and vice versa.

---

### Post by 73ckn797 on 2010-12-10
Nevermind.

---

### Post by oldos2er on 2010-12-10
Maybe something here can help? [https://help.ubuntu.com/community/AddingMimeTypes](https://help.ubuntu.com/community/AddingMimeTypes)

---

### Post by nicks27 on 2010-12-14
I already had two separate entries for ".doc" and ".txt" in my [FONT=Courier New]/etc/mime.types[/FONT] file.
However,  this does seem to be a mime type problem (perhaps specific to the  Thunar file manager), and the solution here worked for me:
[INDENT][http://www.linuxquestions.org/questions/linux-desktop-74/thunar-has-welded-doc-and-txt-file-types-together-775406/](http://www.linuxquestions.org/questions/linux-desktop-74/thunar-has-welded-doc-and-txt-file-types-together-775406/)
[/INDENT]After  updating the mime database be sure to restart the Thunar process (or  just logout/restart) so it picks up the revised mime-types.

The  properties of ".doc" files should correctly show as "Kind: Word  Document" and you should be able to assign preferred applications  independently now.

---

### Post by peyre on 2010-12-14
Well now, that seems to have worked.  For those who'd like step-by-step instructions, I'll write down what I did.

[LIST=1]
[*]Press Alt-F2 to bring up the Run window.  Type in "gksudo [filemanager]", where [filemanager] is the file manager you want to use, e.g. nautilus.  I'm running Xubuntu, so I typed "gksudo thunar".
[*]Navigate to /etc, and open mime.types.  Search for "doc" and find the line referencing Word docs.  Mine looked like: ```
application/msword         doc dot
```[*]Change "application/msword" to "application/vnd.oasis.opendocument.text" (what I did was copy and paste in what was next to **odt** below).
[*]Close and save mime.types.  Now find a Word doc somewhere, right-click on it, and associate it with OpenOffice or AbiWord, per what 73ckn797 suggested above.
[/LIST]

---

### Post by ajoliveira on 2011-04-12
Hi

Interesting, did this and the mess-up between doc and txt remains, in fact the types were originally different in mime.types. Looks like a bug.

---

### Post by peyre on 2011-04-12
I hate to say it, but--while it worked for me at first--it stopped after a while.  Now I'm back to right-clicking and selecting the application I want to use.

---

