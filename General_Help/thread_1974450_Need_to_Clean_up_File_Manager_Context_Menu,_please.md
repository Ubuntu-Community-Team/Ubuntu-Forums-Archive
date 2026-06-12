---
title: "Need to Clean up File Manager Context Menu, please Help! (Open With...)"
date: 2012-05-06
forum: General Help
---

### Post by ohnonot on 2012-05-06
i have been searching for this but could not find anything appropriate.

it seems i can add items to the file open right click menu via the "Open with..." dialog, but cannot remove them?
also some programs leave their own stuff there (file-roller: "Extract here" - but i uninstalled file-roller).

where are these things stored and how can i clean it up?

thanx.

PS: i think i remember that gnome/nautilus offers a gui for that but not here on xfce 4.8.

---

### Post by westie457 on 2012-05-06
Hi, try this.

Open the File Browser right-click any file and select 'Properties', then in the pop up window select the 'Open with' tab to see which apps will open that file and others of that type.

Right-click any app in the list, you should get one option to 'Forget Association', click that. Job done.



Edit: These  instructions are for Nautilus. No idea if they work within xfce or lxde. The OP added extra info before this reply got posted.

---

### Post by ohnonot on 2012-05-07
> **westie457 said:**
> Hi, try this.

Open the File Browser right-click any file and select 'Properties', then in the pop up window select the 'Open with' tab to see which apps will open that file and others of that type.

Right-click any app in the list, you should get one option to 'Forget Association', click that. Job done.



Edit: These  instructions are for Nautilus. No idea if they work within xfce or lxde. The OP added extra info before this reply got posted.
oh wow, so you were really quick to answer that.
but sadly, yes, i'm using thunar and pcmanfm and both offer a possibility to add more applications through file right click -> properties, but not to remove them.

any idea how to do that the non-gui way?

---

### Post by westie457 on 2012-05-07
The procedure is slightly different using the default file-browser in Xubuntu. It goes like this:-

Select file, right-click choose Properties.

The first tab of the new window -roughly in the middle- you should see 'open with' and a button with the name of the default/last used app to open that file. Click on that, it opes up a list of all apps that can open that type of file. Pick one, right-click, this shows the option to 'Remove Launcher'.

Hope this helps.

There probably is a way to remove file associations in the terminal - CLI - I do not know how to do it though.

---

### Post by ohnonot on 2012-05-11
thanks.
the option "remove launcher" only comes up thus: right click file, go to "open with"->"open with other application...".
unfortunately it's always greyed out. i tried a root window, too.
i did manage to remove some entries by deleting some files (user .desktop files in ~/.local/share/applications iirc)

i guess it's possible to further shorten that list by tweaking mime types (ubuntu-tweak).

one question remains, how to remove obsolete entries from the context menu or how to customize it in general...

---

