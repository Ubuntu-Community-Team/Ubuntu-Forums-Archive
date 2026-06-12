---
title: "Search programs: fast for music data"
date: 2006-04-28
forum: General Help
---

### Post by jms830 on 2006-04-28
I'm looking for a search program that can _quickly_ search a large amount of data and return results, like a list of folders that match. I want this because I prefer to search through my music by folders of artists and albums (very organized) rather than have a music library progam open all the time. Using gnome's search is very slow for this purpose. Thanks.

and it's my 100th post!

---

### Post by jpkotta on 2006-04-28
find will work if you want to search by filenames.  locate is much faster than find, but its results don't always match the current state of the file system (the database is updated daily).  find or locate combined with other programs like sed and awk and id3info will let you search the meta data.

---

### Post by jms830 on 2006-04-28
Hmm. Maybe this is a better idea of what I want: I want a search tool that is fast like *locate* but can be told (as default setting) to look only in certain folders. Also, if I could chose to have it only show folders and not files as a default setting, that would be good too.  However, I don't want it to be a command line program, as I want a list of folders to pop up that i can click on and they will open in nautilus.

I have been messing around with deskbar-applet but whenever I make that search for something it opens gnome-search-tool which starts in the Home folder, which is not where I want it to look, nor can I customize it very much. Maybe there's a replacement or a better search program I can integrate? Thanks

---

