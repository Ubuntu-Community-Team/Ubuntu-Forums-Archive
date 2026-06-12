---
title: "How to reset Tangerine Folder scan?"
date: 2012-08-15
forum: General Help
---

### Post by Bazon on 2012-08-15
Hello!

I got the following trouble:
Tangerine only scans a part of my music collection in the selected folder, about 1000 of 5000 files are missing. 

Looking in the log files, I found several warnings, most of them concerning playlists: files in them are not found, because the refer to an old, absolute path.
OK, tangerine, you're right, these playlists are old trash, so I searched in my music folder for all .pls and .m3u playlists and deleted them. 

Anyway, killing tangerine and starting it again in a terminal leads to the SAME warnings as before, i.e. warnings about playlists. playlists I deleted before.

So my question is:
[B]How can I get tangerine to really rescan the selected folder and forget previous searches?
And how can I get it to find all my files, not only most of them?[/B]

thanks!

---

### Post by Bazon on 2012-08-15
OK, found it:

1. scanned songs are in ~/.config/tangerine
2. I didn't really delete the playlists, only moved them to trash. Whyever, they didn't occur in my trash, but in a .trash0001 folder in my music folder. So they were still in my music folder and tangerine found them. Deleting that .trash0001 folder helped, the playlists aren't found anymore and only about 100 songs are missing now....

---

