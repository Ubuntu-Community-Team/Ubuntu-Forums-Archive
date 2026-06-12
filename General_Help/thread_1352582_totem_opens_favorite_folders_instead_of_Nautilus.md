---
title: "totem opens favorite folders instead of Nautilus"
date: 2009-12-11
forum: General Help
---

### Post by BobSongs on 2009-12-11
When I click:
[INDENT]**Places** > **Downloads**
[/INDENT]or
[INDENT] **Places** > **Videos**
[/INDENT]or
[INDENT]**Places** > **Documents** (etc.)[/INDENT]
rather than Nautilus opening the appropriate folder, **totem** tries to open the folder. totem will fill itself with the files it finds in the folder and complain that it doesn't have a plug-in to open text files, etc.

What can I tweak in order to restore browsing to **Nautilus** from **totem**?

---

### Post by audiomick on 2009-12-11
Hallo BobSongs,
I have no help, but maybe the same problem.
I updated a laptop for a friend via fresh install from 8.04 to 9.10 after shrinking the /home partition, which was reused, and enlarging the / partition.

After the fresh install, the "places" menu started behaving in a similar manner.
The link to "filesystem" works, some others do nothing, and several cause Rhytmnbox to open and want to play something.
I'm stumped, so I will be watching to see if you get a reply.

---

### Post by BobSongs on 2009-12-12
>> bump <<

---

### Post by Wardje on 2009-12-12
I believe this needed an edit of ~/.local/share/applications/mimeapps.list

So boot up a terminal and type
```
cd ~/.local/share/applications
vim mimeapps.list
```
*Note: you can of course use another text editor than vim. eg: nano, gedit, ...*

Look for a line that says
```
inode/directory=STUFFHERE;
```
Most likely, the STUFFHERE part will start with "totem.desktop;". Remove the totem entry (entries are seperated by ;, be sure to remove everything of the totem entry). Either way, what you want is the nautilus entry to be the first (if there is no nautilus entry whatsoever, put "nautilus-folder-handler.desktop;" right after the "=". Then save.


If this is a systemwide problem, you might have to edit this file instead
```
/etc/gnome/defaults.list
```

---

### Post by BobSongs on 2009-12-12
[FONT=Verdana]Ahh! Thanks, Wardje. Let me spew the contents of that file:

```
[Added Associations]
application/x-extension-drive=totem.desktop;
inode/directory=totem.desktop;nautilus-folder-handler.desktop;kde4-dolphin.desktop;kde4-gwenview.desktop;kde4-kfmclient_dir.desktop;Thunar-folder-handler.desktop;
x-content/audio-cdda=sound-juicer.desktop;
x-content/video-dvd=totem.desktop;
x-content/audio-player=rhythmbox.desktop;
x-content/image-dcf=f-spot-import.desktop;
```Seems you nailed it on the head. There it is: "totem.desktop". Seems my ~ folder is revealing that I've tried adding several desktops. I'll clean out the superfluous entries.

Thanks again!!

**Edit:** 

The [COLOR=DarkSlateGray]**~/.local/share/applications/mimeapps.list**[/COLOR] file was edited in [COLOR=DarkSlateGray]**gedit**[/COLOR] without root privileges. The line ```
inode/directory=totem.desktop;nautilus-folder-handler.desktop;kde4-dolphin.desktop;kde4-gwenview.desktop;kde4-kfmclient_dir.desktop;Thunar-folder-handler.desktop;
```was simply changed to```
inode/directory=nautilus-folder-handler.desktop;
``` I logged out of the account and logged back in. Things seem to be working perfectly. The only "change" is that Nautilus doesn't seem to show any "eject" buttons next to removable drives. However, these show up on teh desktop. And that's good enough for me.[/FONT]

---

### Post by Orfintain on 2009-12-15
thanks so much 

I was having the same problem with rhythmbox doing the same thing

---

### Post by audiomick on 2009-12-20
> **Wardje said:**
> I believe this needed an edit of ~/.local/share/applications/mimeapps.list

So boot up a terminal and type
```
cd ~/.local/share/applications
vim mimeapps.list
```
*Note: you can of course use another text editor than vim. eg: nano, gedit, ...*

Look for a line that says
```
inode/directory=STUFFHERE;
```
Most likely, the STUFFHERE part will start with "totem.desktop;". Remove the totem entry (entries are seperated by ;, be sure to remove everything of the totem entry). Either way, what you want is the nautilus entry to be the first (if there is no nautilus entry whatsoever, put "nautilus-folder-handler.desktop;" right after the "=". Then save.


If this is a systemwide problem, you might have to edit this file instead
```
/etc/gnome/defaults.list
```

THANKS! Needed that for a computer that I look after for a friend. It worked.

---

### Post by xavierneuman on 2010-12-29
I had the same problem and found an easier solution (for absolute beginners, at least).

You right click on any folder* and go to the "Open with other application".
There you select File Browser and check the box "Remember this application for 'folder' files".

There you have it. It worked for me.

*If you haven`t got a folder on your desktop, you can open Nautilus from the terminal and right clicking any folder you have.

---

### Post by kendoori on 2011-02-12
> **xavierneuman said:**
> I had the same problem and found an easier solution (for absolute beginners, at least).

You right click on any folder* and go to the "Open with other application".
There you select File Browser and check the box "Remember this application for 'folder' files".

There you have it. It worked for me.

*If you haven`t got a folder on your desktop, you can open Nautilus from the terminal and right clicking any folder you have.

This worked for me too... I'd been doing some cleanup of my "Open With" and somehow messed up associations with folders. This fixed that.

---

### Post by alfh on 2011-02-13
When you want to open a folder with totem or some other application, the intuitive way is right-click folder and choose "open with..."

Then if you keep the "remember this program..." option totem will become the default program to open that folder and users get confused because suddenly default behaviour changed.

So what's counter-intuitive here is that the "remember" box is checked by default - and maybe that the description is a bit misleading. It could read something like "change default program for this folder" instead.

---

### Post by jerrard on 2011-02-13
Hi All,

I think i have a similar problem and i thought i had found the answer but....

when i try to boot up a terminal and type

cd ~/.local/share/applications
vim mimeapps.list


it says:

The program 'vim' can be found in the following packages:
 * vim
 * vim-gnome
 * vim-tiny
 * vim-gtk
 * vim-nox
Try: sudo apt-get install <selected package>


hmmm. so, i tried:

/etc/gnome/defaults.list

and it said:

bash: /etc/gnome/defaults.list: Permission denied


argh! I am such a noob! CAn someone please help?

Many Thanks!

---

### Post by jerrard on 2011-02-13
p.s this is a problem which i caused. I was happily clicking away with somewhere and did something with file associations.....doh!

---

### Post by jerrard on 2011-02-14
***bump***

---

### Post by Vaphell on 2011-02-14
what is your issue? folders opened not with file browser but with APP_X?
if so, skip that thing you are doing and follow advice from post #8

---

### Post by cjastram on 2013-02-13
I had this problem in KDE on a new install of the KDE software on an Ubuntu 12.12 installation.  (My installation is a little odd, since it was originally 8.04, and I have upgraded ever since, so there could be some oddities).

I solved it by removing .local/share/applications altogether and logging out / back in.  You might rename the folder instead of removing it in case something goes wierdly wrong, but this worked for me.

cej102937

---

