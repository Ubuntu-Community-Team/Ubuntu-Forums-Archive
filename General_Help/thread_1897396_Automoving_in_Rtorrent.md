---
title: "Automoving in Rtorrent"
date: 2011-12-19
forum: General Help
---

### Post by jonwestin on 2011-12-19
Hey,

Im running a small HTCP with Ubuntu on and Im using rtorrent with rutorrent webGUI to download stuff. I have a file tree that I really want to keep in order with movies and tv-shows sorted under different directories. Right now Im just downloading stuff to default "Download" folder and I either let stuff stay there to seed for a while then move them to the directory where I want to keep them. My problem is that I would like to be able to seed while moving stuff to my file tree (eg ../Videos/Movies etc).
I could use the datadir plugin for rutorrent but right now I cant get it to work. What I really would like though is to be able to create a sub-directory in my watch folder for every TV show im currently following and have rtorrent automatically move the finished file. 

Say Im following the new season of Californication. Then I would like to be able to create the directory /Torrents/Series/Californication/Season 5/ and put the torrent file there.
Rtorrent scans all /Torrent/Series/* for new files, and moves the finished file to /Vidoes/Series/Californication/Season 5
And this without me having to create a new watch command in .rtorrent.rc

Is this possible?

---

### Post by hwttdz on 2011-12-20
Not familiar with rtorrent (though it's on the to do list).  

You could make links from your various folders to the files in downloads, because any media player/file browser should handle the links well, and leave the files themselves in downloads.  And I'd also run a periodic find for files more than say 3 months old in downloads, and then remove the link and move the file to its final location and remove it from rtorrent.  

This gets you, 
1) apparent files where you want them from the get go
2) seeding while they're in the folder you want them to go to
3) no accumulation of files in the downloads directory (as they do eventually get moved out after seeding).

Thoughts?

---

### Post by jonwestin on 2011-12-21
> **hwttdz said:**
> Not familiar with rtorrent (though it's on the to do list).  

You could make links from your various folders to the files in downloads, because any media player/file browser should handle the links well, and leave the files themselves in downloads.  And I'd also run a periodic find for files more than say 3 months old in downloads, and then remove the link and move the file to its final location and remove it from rtorrent.  

This gets you, 
1) apparent files where you want them from the get go
2) seeding while they're in the folder you want them to go to
3) no accumulation of files in the downloads directory (as they do eventually get moved out after seeding).

Thoughts?

That makes good sense actually, I found a similar thought while looking around. Right now I solved the problem with rssdler ([http://code.google.com/p/rssdler/](http://code.google.com/p/rssdler/)) for automatical downloading with rtorrent and SortTV ([http://sourceforge.net/projects/sorttv/](http://sourceforge.net/projects/sorttv/)) for moving the files, works like a charm! No seeding though but I guess I can live with that. Although I might be able to edit the SortTV script to make links instead of moving the files! If there isnt already a function for that built in..

Rtorrent is really nice, Ive set it up a few times by now so just ask if you need any help.

---

### Post by jonwestin on 2011-12-21
:shock:

---

