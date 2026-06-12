---
title: "Oneiric File Association"
date: 2011-10-14
forum: General Help
---

### Post by thunderbirdje on 2011-10-14
Since upgrade from 11.04 to 11.10, when opening for example a external hard drive, it opens in VLC. Or when clicking 'show file in folder' in a Chromium windows, the file opens in VLC as well instead of nautilus. So I always have to close VLC and go to 'HOME' > 'and browsing to the corresponding folder/external hard drive' to open the file properly.

I already reinstalled VLC, behaviour is still the same.

Is there a general association in Ubuntu to 'open files'? this is maybe set to VLC. I know it can be done per extension, I don't know how to set it for general files/opening drives?

---

### Post by drs305 on 2011-10-14
I have moved this from the Oneiric Known Bugs thread, which is for posting solutions.

It sounds like you have a file association problem. Try opening the Nautilus file browser and right clicking on any folder icon.

Right click and look for "Open with other application".

In my Oneiric the choice is now "Files". I think it used to be "File Manager".

Once you have highlighted it, press the Select button and see if your folders now open with Nautilus.

---

### Post by outofthecave on 2011-10-16
I have a very similar problem: I want text files (*.txt and no extension) to be opened with emacs when I double-click them, not with gedit.  How do I set that?
I already tried this: right-click any text file in nautilus, choose 'open with other application', select emacs.  The file opens with emacs, fine.  But the next time I double-click the same text file, it opens with gedit again.  This is really annoying!

---

### Post by mc4man on 2011-10-16
> **outofthecave said:**
> I have a very similar problem: I want text files (*.txt and no extension) to be opened with emacs when I double-click them, not with gedit.  How do I set that?
I already tried this: right-click any text file in nautilus, choose 'open with other application', select emacs.  The file opens with emacs, fine.  But the next time I double-click the same text file, it opens with gedit again.  This is really annoying!
Not the same issue as the OP who has an improper line in mimeapps.list - 
Just right click > **Properties** > Open with, pick emacs & click on the set as default

---

### Post by outofthecave on 2011-10-17
> **mc4man said:**
>  click on the set as default
But there is no checkbox or button 'set as default' in Oneiric Ocelot and exactly that is my problem.

---

### Post by drs305 on 2011-10-17
> **outofthecave said:**
> But there is no checkbox or button 'set as default' in Oneiric Ocelot and exactly that is my problem.

Did you right click the file > select Properties > Open With > find the app you want either from the list or by clicking on 'Show other applications' >  *and then highlight the app*? The 'Set as Default' will be greyed out until you highlight something, at which point the button should become active unless the highlighted app is already the default.

---

### Post by davidcm on 2011-10-17
I'm have exactly the same problem. No way to change the default file association.

In my case I want to make VLC media player the default for playing .avi

In Oneiric/Unity  in the "Open With Other Application..." dialog, **there is no "Set As Default" button/checkbox**, grayed out or otherwise.

This is yet another annoyance of this latest so-called upgrade to 11.10. No way to do many of the most basic things. I'm now forced to open up the "Open With Other Application..." dialog and select the VLC player every time I want to play an avi. In what way is this an improvement?

I've been using Ubuntu since 6.04 and loved it. Now they've taken my desktop away and replaced it with Unity, I'll probably go back to Windows, where at least I have *some* control over the way I want to work.

---

### Post by mc4man on 2011-10-17
> **davidcm said:**
> I'm have exactly the same problem. No way to change the default file association.
.I'm really failing to see what's so hard about reading a posted line that says
right click > **[SIZE="3"]Properties[/SIZE]** > open with  ect.
posts 4 & 6

---

### Post by davidcm on 2011-10-17
No you're right it's not difficult.

I'm just so punch drunk trying to work out how to use Unity, I can't read straight.

Thanks for the help.


(Actually I gave up on Unity and am running Gnome shell and that works fine for me.)

---

### Post by Morbius1 on 2011-10-17
What does seem to be missing is the ability through a right click to create your own file association.

Back in the olden days you could:
Right click a file > Open with > Other Application > Use a custom command > and then make it the default.

---

### Post by outofthecave on 2011-10-20
Thanks, drs305!  Your solution worked for me.

---

### Post by JamesFlamingo on 2011-10-20
Confuses lots of people when they remove file association from "Open With other Application" menu option.

---

### Post by seyacat on 2011-10-20
Open With Other Apllication dont have custom command menu option!

---

### Post by nochiel on 2011-10-22
> **thunderbirdje said:**
> Since upgrade from 11.04 to 11.10, when opening for example a external hard drive, it opens in VLC. Or when clicking 'show file in folder' in a Chromium windows, the file opens in VLC as well instead of nautilus. So I always have to close VLC and go to 'HOME' > 'and browsing to the corresponding folder/external hard drive' to open the file properly.

I already reinstalled VLC, behaviour is still the same.

Is there a general association in Ubuntu to 'open files'? this is maybe set to VLC. I know it can be done per extension, I don't know how to set it for general files/opening drives?

I have exactly the same probelm after upgrading.  It's absurd and infuriating.  I edited my local mimeapps.list but upon loging out the whole file is reset, causing the problem to persist.

---

