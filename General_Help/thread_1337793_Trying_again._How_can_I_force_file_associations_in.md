---
title: "Trying again. How can I force file associations in Xubuntu?"
date: 2009-11-25
forum: General Help
---

### Post by slumbergod on 2009-11-25
This is the same thing that happened in Jaunty and it is still happening in Karmic.

I can seem to force .cbr, .bz, and .deb to stop opening in file-roller. I change them by right-clicking and choosing the "from now on open with this" dialog but they always seem to default back to the archive manager. 

Sure, it isn't that big a problem...I could right click open them from the list of associated problems. But it is annoying because double clicking them is more natural.

Does any Xubuntu user experience this? Does anyone know how to permanently fix this annoyance?

---

### Post by Zorael on 2009-11-25
You could go and edit the .desktop file for file-roller and remove the mimetypes you don't want your system to realize the app supports. It would be in **/usr/share/applications/** someplace, likely named **file-roller.desktop** or so.

Example taken from Ark's file (scroll right);
```
[Desktop Entry]
MimeType=application/x-gzip;application/x-tar;application/x-compressed-tar;application/x-bzip-compressed-tar;application/zip;[COLOR="Red"]application/x-bzip[/COLOR];application/x-rar;application/x-tarz;application/x-bzip2;application/x-java-archive;[COLOR="Red"]application/x-deb;[/COLOR]application/x-7z-compressed;application/x-compress;application/x-zip-compressed;application/x-lzma;application/x-servicepack;
GenericName=Archiving Tool
*[...]*
```
(Just guesstimating that those two mimetypes would translate to .bz and .deb.)

Some older settings might stick if you have user-specific settings in **~/.local/share/applications** overriding those in **/usr/share/applications**.

See [this](http://ubuntuforums.org/showthread.php?t=1326806) and [this](http://ubuntuforums.org/showthread.php?t=1333374) thread for more information.

---

### Post by slumbergod on 2009-11-25
Thanks for the suggestions! I will give them a try and see how it goes for a day or two. By then I'll know if the changes are going to stick. I'll post back here with my results.

[Solved] Yep, it is finally behaving. Thanks for the suggestion. I hadn't thought to try changing the .desktop file. It turned out to be easier than I expected.

---

