---
title: "Using Text Editor as preffered application for scripts"
date: 2010-12-07
forum: General Help
---

### Post by timgood on 2010-12-07
I have some assorted shell scripts and PERL scripts that I sometimes need to edit. When I right click on them within Nautilus, it offers to open them in Notepad. I can select Text Editor and put a tick in the box to 'remember this application', but it doesn't remember and next time I have Notepad again. It's a pain to have to navigate to Text Editor every time I need to open one of these files. Is there any way to make it stick? Help would be much appreciated.

---

### Post by timgood on 2010-12-08
bump...

---

### Post by daqron on 2010-12-18
Yeah, I don't really understand Ubuntu making notepad the default text editor, considering every text editor imaginable, including all of the ones that Linux has standard, would be a better choice.

But anyway did you try some of the suggestions here? [http://ubuntuforums.org/showthread.php?t=299086](http://ubuntuforums.org/showthread.php?t=299086).

---

### Post by tfultz33 on 2010-12-18
I have this in my ~/.bashrc file if that helps:

EDITOR=gedit

---

### Post by timgood on 2010-12-18
Thanks for this - will try these suggestions out...

---

### Post by cgroza on 2010-12-18
Ubuntu has no Notepad application. If it had it would get sued by Microsoft for stealing the name!

---

### Post by Krytarik on 2010-12-18
> **cgroza said:**
> Ubuntu has no Notepad application. If it had it would get sued by Microsoft for stealing the name!
Are you joking? There is definitely one Notepad, from WINE.

---

### Post by mc4man on 2010-12-18
> I can select Text Editor and put a tick in the box to 'remember this application', but it doesn't remember and next time I have Notepad again.
If you're on maverick then the 'remember...' option would typically change the default. (really shouldn't

Anyway the more 'proper' way to set a new default for a filetype is - 
right click on a file -> **properties** -> open with, ect.

---

