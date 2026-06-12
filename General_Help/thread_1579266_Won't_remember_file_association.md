---
title: "Won't remember file association"
date: 2010-09-21
forum: General Help
---

### Post by finny388 on 2010-09-21
I am trying to use VLC playlists.

Either xspf or m3u.

Creating them is fine but the only they will launch is if I "Open With" VLC.

Having "Remember this application for "XSPF playlist" files." checked  seems to make the assignment b/c when I right-click to get properties VLC is chosen under the "Open With" tab.

The icon doesn't change from the music note image either (I thought I'd get some VLC icon)

I understand this is a bug and you must edit ".local/share/applications/mimeapps.list"

But don't know what to enter there for XSPF or M3U files.

Ubuntu 10.04.1
VLC 1.2.2

---

### Post by mc4man on 2010-09-21
You shouldn't have to manually set in mimeapps if using a r. click -> properties -> open with to set default

Anyway - 
m3u
audio/x-mpegurl=

xspf
application/xspf+xml=

---

### Post by finny388 on 2010-09-21
oh I agreed

but setting it doesn't change anything, I still have to manually select VLC to open it with.

> m3u
audio/x-mpegurl=

xspf
application/xspf+xml= 

so I add:
```
audio/x-mpegurl=VLC
application/xspf+xml=VLC
```

to the file?

---

### Post by mc4man on 2010-09-21
> so I add:
No, use ( copy and paste as is - 2 separate lines 
```
audio/x-mpegurl=vlc.desktop;
application/xspf+xml=vlc.desktop;

```

---

### Post by finny388 on 2010-09-22
Hmmph,

That didn't change its behaviour either.

When I double click the xspf file, it asks "Display/ Cancel/ Run in Terminal/ Run".

I choose Run but nothing happens (I don't have rhythmbox installed)

Here is my mimeapps.list:```
[Added Associations]
video/x-ms-wmv=vlc.desktop;
video/x-msvideo=vlc.desktop;
video/x-flv=totem.desktop;vlc.desktop;
application/x-shellscript=gedit.desktop;openoffice.org-writer.desktop;
text/x-uri=gedit.desktop;openoffice.org-writer.desktop;
application/xspf+xml=vlc.desktop;firefox.desktop;gedit.desktop;openoffice.org-writer.desktop;
audio/x-mpegurl=totem.desktop;vlc.desktop;rhythmbox.desktop;gedit.desktop;openoffice.org-writer.desktop;
application/x-wine-extension-inf=gedit.desktop;
application/x-extension-part=vlc.desktop;

audio/x-mpegurl=vlc.desktop;
application/xspf+xml=vlc.desktop;
```

I rebooted and no change. is the empty line messing it up? I don't understand why I can
[LIST]
[*]add it to the mimeapps file
[*]make it default it when using "Open With"
[*]select it within the "Open With" tab of file properties.
[/LIST]
and still it has the music note icon and won't open.

Nautilus Screenshot:
[IMG]http://img710.imageshack.us/img710/1396/screenshotoib.png[/IMG]
:(

---

### Post by mc4man on 2010-09-22
For some reason your .m3u's and .xspf's are marked as 'executable' which is interfering with what you hope (and should) happen, (they are seen as executable text files

Do this - 
r. click on one -> properties -> permissions and uncheck the "allow executing file as program", then test that out.


Edit:
if you look you already had the 2 lines in mimeapps so you could delete the 2 old ones (in blue ) or the 2 new ones - your choice
> [Added Associations]
video/x-ms-wmv=vlc.desktop;
video/x-msvideo=vlc.desktop;
video/x-flv=totem.desktop;vlc.desktop;
application/x-shellscript=gedit.desktop;openoffice.org-writer.desktop;
text/x-uri=gedit.desktop;openoffice.org-writer.desktop;
[COLOR="Blue"]application/xspf+xml=vlc.desktop;firefox.desktop;gedit.desktop;openoffice.org-writer.desktop;[/COLOR]
[COLOR="Blue"]audio/x-mpegurl=totem.desktop;vlc.desktop;rhythmbox.desktop;gedit.desktop;openoffice.org-writer.desktop;[/COLOR]
application/x-wine-extension-inf=gedit.desktop;
application/x-extension-part=vlc.desktop;

---

### Post by finny388 on 2010-09-22
Okay, so this could be the issue:

when I try to uncheck it it immediately rechecks it.

perhaps I must be super? I'm the sole user on this machine. If it matters this file is on a fat32 external drive.

can I use chmod, what syntax?

thanks!

---

### Post by mc4man on 2010-09-22
> when I try to uncheck it it immediately rechecks it.

perhaps I must be super? I'm the sole user on this machine. If it matters this file is on a fat32 external drive.

can I use chmod, what syntax?
you can't set permissions on a FAT32 volume.

This is a udisks bug where all text files on removable media (VFAT) are set to executable, it's been fixed in 10.10

To workaround - 2 ways
After setting the default in properties to a player (which you've done), d. left click on a .m3u or .xspf
In the pop up choose "Display", that will open the default based on mimetype, ie. your player 

Or to remove the pop up step

Open File Management, if not in the Preferences menu go 
```
nautilus-file-management-properties
```

In behavior tab set to 'view...' see screen

(if never in FM before have a look around - useful place

Edit:
if still having issues it should be possible to patch the udisk source to prevent this - though I'm  fairly sure the above mentioned will work out

-- it's a very simple fix to the source, 2 lines (the mount options)
I don't see where this can be configured directly, but it's a simple build to do
( this fix should be applied in lucid, probably won't --

wrote a quick patch for current lucid udisks - takes about 5 min to build a new package start to finish

---

### Post by finny388 on 2010-09-22
An extra click to choose Display every time is fine. Especially when 10.10 is next month.

I'm glad I mentioned the file format.

Well done mc4man, thanks for your help

will mark solved...

---

