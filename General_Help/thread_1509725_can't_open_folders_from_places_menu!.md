---
title: "can't open folders from places menu!"
date: 2010-06-14
forum: General Help
---

### Post by boddhisatva on 2010-06-14
Something very strange has happened to my system (Lucid / Gnome / 64 bit): when I try to open a location from Gnome Menu, message pops up saying: "Can't open location [file:///...]. No program is registered to open this type of file." Or something in this vein, I'm translating the message from Polish. So I can't open locations via the main menu, but the bookmarks work fine in an open Nautilus window. It looks like the system doesn't know it should open a location with Nautilus... I looked through file associations in Ubuntu Tweak, but couldn't find anything corresponding to "file:///..." or anything resembling opening a location (I'm not exactly a Linux guru). Also, the folder shortcuts in Cairo-Dock don't work, the same goes for the FolderView screenlets. However, in the MainMenu screenlet, the location shortcuts do work. There has to be some obvious explanation of this anomaly, but I lack a deeper knowledge of the system to work it out. I can't say at which point it started exactly, I think it was around the time I started dragging extra shortcuts to the Cairo-Dock shortcuts applet, but that may be a coincidence. Any ideas, please?

---

### Post by arrange on 2010-06-14
Can you post the contents of the *~/.local/share/applications/mimeapps.list* file?

---

### Post by boddhisatva on 2010-06-15
These are the contents of the file. The Nautilus added/removed are probably there because I played with them in Ubuntu Tweak.

```
[Added Associations]
audio/x-scpls=totem.desktop;vlc.desktop;rhythmbox.desktop;gedit.desktop;
all/allfiles=nautilus-browser.desktop;
all/all=nautilus-browser.desktop;
uri/mmst=nautilus-browser.desktop;
uri/mmsu=nautilus-browser.desktop;

[Removed Associations]
uri/mms=nautilus-browser.desktop;


```

---

### Post by arrange on 2010-06-15
[COLOR="Gray"]when I try to open a location from Gnome Menu,[/COLOR]
Do you mean *Home*, *Documents* etc? Then try adding a line to the file```
inode/directory=nautilus-folder-handler.desktop
x-directory/normal=nautilus-folder-handler.desktop
```

---

### Post by boddhisatva on 2010-06-15
I'm afraid that doesn't help.

---

### Post by boddhisatva on 2010-06-15
As extra info, the same message appears when I use "open as administrator" in the context menu on any folder.

---

### Post by arrange on 2010-06-15
"open as administrator" ??

Could you change the system language temporarily to English and give us precise wording of the error message? Also - could you describe the problem in more detail? Give one specific example step by step how you can trigger the error.

---

### Post by boddhisatva on 2010-06-15
I mean "open as root" :), the Nautilus extension.

I tried to change the language settings (System > Administration > Languages), but it's not possible - I can't even select a language permanently, and "Apply..." doesn't work (Ubuntu is still far from perfect). So I deleted the default language, hoping English would be automatically selected upon restart. However, that was a risky assumption - after reboot the system wouldn't start. So I had to reinstall it. Which wasn't so bad, since I had another problem with logging in, and looking for a solution would have probably taken longer than the reinstall. Now it's OK, but the folder shortcut issue persists, so the problem must be in my Home directory, which has been left intact. 
Anyway, I can't give you the exact English equivalent of the error message, unless you know how to change the system language. The closest equivalent would be "Can't open location "file:///home...". No program is registered (associated) to open this file type.". And it happens when I go to Places menu and select any shortcut, i.e. Home, Music, Videos...

---

### Post by arrange on 2010-06-15
You change the language at the login screen... Sorry, I thought it was obvious.

I don't know what could be the problem then. Please restart the computer, open the [Terminal](https://help.ubuntu.com/community/GnomeTerminal), and type```
strace -e trace=open -p `pidof nautilus`
``` 
Leave the Terminal open and try to launch let's say *Places &#8594; Documents*. You should see the error messages + some output in the Terminal. Copy the output here or to [Ubuntu pastebin]("http://paste.ubuntu.com/").

---

### Post by boddhisatva on 2010-06-15
The error message pops up, but there is no output in the terminal. I have the impression it's not really an "error", it looks like Gnome has lost the file association, because it's the same kind of behaviour as when a file has no associated program to open it. But I may be wrong.

---

### Post by boddhisatva on 2010-06-15
I've switched the system into English (I couldn't do it previously via login screen as I had problems with the login function, I could only login automatically after reboot). The message says: "Could not open location 'file:///home/pawel/Documents'. No application is registered as handling this file"

---

### Post by arrange on 2010-06-15
Can you try this solution?
[http://ubuntuforums.org/showpost.php?p=7308922&postcount=9](http://ubuntuforums.org/showpost.php?p=7308922&postcount=9)

---

### Post by boddhisatva on 2010-06-16
It's worked!
And it was so simple... :)
Thanks a lot for quick responses and all the trouble you went to with this issue!

---

### Post by pariah62038 on 2010-06-17
I have the same problem, that solution didn't work for me though. For me, the problem seems to be that wine is trying to open the folders and isn't succeeding.

---

### Post by boddhisatva on 2010-06-18
I also remember seeing Wine associated with folders somewhere, so it's strange it's not working for you. Maybe you should try changing those associations in Ubuntu Tweak.

---

### Post by pariah62038 on 2010-06-18
What category would I go under to edit that?

---

### Post by boddhisatva on 2010-06-18
> **pariah62038 said:**
> What category would I go under to edit that?

System > File associations manager (or whatever it's called in English - the first item anyway)
There under 'All' you've got, among others, "folder" - should be set to Nautilus.

---

### Post by pariah62038 on 2010-06-18
Thanks, that worked, don't know what could've caused that though.

---

### Post by boddhisatva on 2010-06-19
Well, that's often the case... The causes are unfathomable :)

---

### Post by Fluffgar on 2010-10-20
> **arrange said:**
> Can you try this solution?
[http://ubuntuforums.org/showpost.php?p=7308922&postcount=9](http://ubuntuforums.org/showpost.php?p=7308922&postcount=9)

Oh, thankyou. Places menu had stopped working for me (displayed list but did nothing when clicked on an item). Fortunately I already had links to a couple of folders on the Desktop so I could get to the things I needed to by a round about way. 

Using this solution when I was in my home folder I just right-clicked on a folder in there, selected Open with > Other application... and chose nautilus by browsing to '/usr/bin/nautilus'. 

Seems to be back to normal now :)

---

