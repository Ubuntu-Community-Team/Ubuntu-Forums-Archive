---
title: "How to always run OpenOffice with an option (avoid restoration)"
date: 2009-12-29
forum: General Help
---

### Post by mod-jkl on 2009-12-29
Hi,

I'm using OpenOffice with Jaunty, OpenOffice can be run with the -norestore option which avoid the restoration screen.

Is it possible to set something so OpenOffice is always launched with this option ?

Thanks for any help

---

### Post by gletob on 2009-12-29
Change the command in the Applications menu.

Right click Applications > Edit Menus > Office > OpenOffice.org Word Proc/Spread > properties > then add the -norestore argument to the end of the command string.  Befor the %F though.

Repeat this process for each OpenOffice.org menu item.

If you have a shortcut on the panel Right click it > properties > and do the same in the command field.

---

### Post by mod-jkl on 2009-12-29
Yes, but I'd like that, when an attachment (.doc for instance) is double clicked in thunderbird, openoffice is launched with this option.

---

### Post by Hagar Delest on 2009-12-29
Why do you want to use OOo with this option? If it has to do with a recovery loop at startup, try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

---

### Post by mod-jkl on 2009-12-29
This pc is used by non tech persons, so I just want to avoid the restore screen when a thunderbird attachment (.doc) is double clicked.

If you open an attachment (.doc) from thunderbird and reboot the pc, next time you double click an attachment, you will have the restore screen, that I'm looking to avoid (preferably by a method documented in openoffice, like the -norestore option)

---

### Post by Hagar Delest on 2009-12-29
Well, rather strange, I've never got that screen after having opened an attachment. Is the file closed correctly before the computer is rebooted?

---

### Post by mod-jkl on 2009-12-29
No, the files are still open when the reboot happens ..
I don't close thunderbird, firefix etc ... before doing a reboot.

---

### Post by Hagar Delest on 2009-12-29
But why reboot the PC without closing files before? Are you talking about crashes or is it by intention (but why)?

---

### Post by mod-jkl on 2009-12-29
Well, it's not a reboot in fact, it's more power of, wait one day , power on ..

The user power on this pc, read his mails, open email attachment with OpenOffice, when this is done, shut down the pc and do the same thing the next day..and then, when opening emails attachment (.doc, .pps), there is the restoration screen that I'd like to avoid becaus it is confusing for a person who is not comfortable with computers..

---

### Post by Hagar Delest on 2009-12-29
Well, why not educate them??? Such rude power off can lead to damages both for the software (profiles corruption, not only OOo), performance loss (due to temporary files that could remain, cleaning operation needed at startup, ...) and for the hardware (if a writing operation is under progress when power is shut down).

I hope they handle their car with more care (or there are lucky car dealers around then).

---

### Post by xifer on 2009-12-29
create a simple shell script with the required command line options. 

that is - edit the text file /usr/bin/ooffice and if the command is, e.g., writer then add in your required command.

Should work but don't quote me on it...

Alternatively, you might be able to set this option in the file

/usr/share/applications/openoffice.org-writer.desktop

---

### Post by xifer on 2009-12-29
> **Hagar de l'Est said:**
> Well, why not educate them??? Such rude power off can lead to damages both for the software (profiles corruption, not only OOo), performance loss (due to temporary files that could remain, cleaning operation needed at startup, ...) and for the hardware (if a writing operation is under progress when power is shut down).

I hope they handle their car with more care (or there are lucky car dealers around then).


Oh come on! The system should cleanly close all open applications.  I certainly can't be bothered closing maybe a dozen apps if I want to reboot...

---

### Post by mod-jkl on 2009-12-29
> **xifer said:**
> create a simple shell script with the required command line options. 

that is - edit the text file /usr/bin/ooffice and if the command is, e.g., writer then add in your required command.

Should work but don't quote me on it...

Alternatively, you might be able to set this option in the file

/usr/share/applications/openoffice.org-writer.desktop

Yes, I thought to that, but if they are some updates on openoffice, that would be deleted ....

There is a solution that consist of removing a file named recovery.xcu in the openoffice profile directory, that works but it is not documented, that's why I was looking for to use the -norestore option which is documented..  I prefer to use documented solutions when it's possible.

---

### Post by mod-jkl on 2009-12-29
> **xifer said:**
> Oh come on! The system should cleanly close all open applications.  I certainly can't be bothered closing maybe a dozen apps if I want to reboot...

Thank you, I don't close my applications also before shut down a pc. Also, some users are very uncomfortable with pc (you have to teach to those persons to realize that, maybe you know what I mean), so it's better to avoid everything that is not necessary to make the whole thing not too complicate.

---

### Post by xifer on 2009-12-29
> **mod-jkl said:**
> Yes, I thought to that, but if they are some updates on openoffice, that would be deleted ....

There is a solution that consist of removing a file named recovery.xcu in the openoffice profile directory, that works but it is not documented, that's why I was looking for to use the -norestore option which is documented..

So make sure the change is re-applied - if that is really the case.  Most installs do not overwrite user preferences without prompting.  have a startup script apply the change...

---

### Post by mod-jkl on 2009-12-29
Yes, that can be a solution..

---

### Post by Hagar Delest on 2009-12-30
> **xifer said:**
> Oh come on! The system should cleanly close all open applications.  I certainly can't be bothered closing maybe a dozen apps if I want to reboot...
:lol:
So if you have modified 10 documents, you'll get 10 pop ups asking if you want to save the changes! So much for not being bothered by closing a dozen apps!!! Or do you want also the OS to have some mind reading feature to answer for you what documents are worth saving or not?

Or ask the Ubuntu team to create a new shut down option that closes all applications by denying all dialogs asking for changes.

I don't understand: you don't want to use a method that is not documented (even if that works) and you don't want to educate others. :confused:

---

