---
title: "lubuntu / chrome / docx"
date: 2011-08-03
forum: General Help
---

### Post by milton_boon on 2011-08-03
In lubuntu 11.04 the default browser is chrome.

Chrome opens docx files in file-roller. I don't get any choice with the formats people send me and need to open these files nicely from the browser.

Can you suggest how I might get chrome to open them with abiword? 

This works in the desktop fine but in chrome I can't find any "open with" etc type settings in chrome.

Cheers,

MB

---

### Post by kerry_s on 2011-08-03
grab this extension->
[https://chrome.google.com/webstore/detail/nnbmlagghjjcbdhgmkedmbmedengocbn?hl=en-US&hc=search&hcp=main#](https://chrome.google.com/webstore/detail/nnbmlagghjjcbdhgmkedmbmedengocbn?hl=en-US&hc=search&hcp=main#)

restart the browser, then test a docx file.

---

### Post by milton_boon on 2011-08-03
I believe chrome uses xdg-open to launch external applications so I suppose the question reduces to "why isn't xdg-open" handling docx correctly, it appears to work for .doc files.

---

### Post by milton_boon on 2011-08-03
> **kerry_s said:**
> grab this extension->
[https://chrome.google.com/webstore/detail/nnbmlagghjjcbdhgmkedmbmedengocbn?hl=en-US&hc=search&hcp=main#](https://chrome.google.com/webstore/detail/nnbmlagghjjcbdhgmkedmbmedengocbn?hl=en-US&hc=search&hcp=main#)

restart the browser, then test a docx file.

Kerry, I'm sure this will work but it isn't what I am after.  I'd like to open the files in abiword...

The default for .doc files is download and then if the download button at the bottom is clicked then the file is opened in abiword, for .docx it is opened in file-roller.

---

### Post by kerry_s on 2011-08-03
look into xdg-mime
i think that is used to set the default app for xdg-open

---

### Post by Hatsune Miku on 2011-08-03
> **milton_boon said:**
> In lubuntu 11.04 the default browser is chrome.

Chrome opens docx files in file-roller. I don't get any choice with the formats people send me and need to open these files nicely from the browser.

Can you suggest how I might get chrome to open them with abiword? 

This works in the desktop fine but in chrome I can't find any "open with" etc type settings in chrome.

Cheers,

MB

Just Open it in google-docs. Or install Open/Libre Office

---

### Post by milton_boon on 2011-08-03
> **Hatsune Miku said:**
> Just Open it in google-docs. Or install Open/Libre Office

I want to open docx files with chrome using abiword. Anyone got an answer to this problem?  The alternatives posted so far aren't solutions.

I'm using lubuntu on a low end machine that runs very slowly with either libre office or firefox but runs fine with abiword / chrome.  

I want chrome to behave correctly with docx files and call abiword, just like it does with doc files.

xdg-open appears to be the problem but it is by no means clear how to get xdg-open to select abiword instead of file-roller for docx files.

---

### Post by kerry_s on 2011-08-03
> **milton_boon said:**
> I want to open docx files with chrome using abiword. Anyone got an answer to this problem?  The alternatives posted so far aren't solutions.

I'm using lubuntu on a low end machine that runs very slowly with either libre office or firefox but runs fine with abiword / chrome.  

I want chrome to behave correctly with docx files and call abiword, just like it does with doc files.

xdg-open appears to be the problem but it is by no means clear how to get xdg-open to select abiword instead of file-roller for docx files.

i told you xdg-open uses xdg-mime to set the application.
from the terminal it looks like the command would be something like:
xdg-mime default abiword *.docx

i'm not going to take the time to read the manual, cause i open mine in google docs in the browser, it works right & i don't want to mess mine up trying to figure out yours. :D

---

### Post by milton_boon on 2011-08-15
The problem is here that xdg-mime and its man pages are completely inpenetrable...

---

### Post by kerry_s on 2011-08-15
> **milton_boon said:**
> The problem is here that xdg-mime and its man pages are completely inpenetrable...

:lolflag:
a lot of man pages are like that.
hey, i was looking through /usr/share/applications & saw a defaults.list, perhaps you could try manually editing that to set what you like. just a thought, no idea if it would do anything.

---

### Post by milton_boon on 2011-08-15
I think you are missing the point - the man pages here are not typical, thgey don't provide enough information to drive the application.

The application is not symmetric - you might expect the diagnostic information it produces to be sufficient to make the settings (at least for something it already gets right) but it isn't [ie "xdg-open query filetype blah.doc" might reasonably be expected to give sufficient information to set the mime type for blah.doc but it isn't].

There is missing information...

---

### Post by milton_boon on 2011-08-15
The nearest I've got so far is this:

xdg-mime default abiword.desktop "*.docx" 

which produces no output and is ignored by chrome.

The man pages are extremely unhelpful.  I needed to strace xdg-open to find out where it store the information it is apparently setting.

(for reference ~/.local/share/applications/mimeapps.list)

lxde is opening docx correctly but chrome is not (but then lxde was always doing this correctly after selecting open with).

I'm not sure but this problem might be due to what xdg-open falls back on.  xdg-open uses variopus things to probe file magic to determine the type.  Under gnome it uses gnome-vfs, I don't know what it uses in kde but gnome-vfs is not installed with lubuntu so it might be falling back on "file" which is a bit rusty and ids docx as a zip file (which of course it is).


Anyone know how to get chrome in lubuntu to open docx files with abiword, exactly the same way it opens doc files?

---

