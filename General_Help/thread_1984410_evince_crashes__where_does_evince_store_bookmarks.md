---
title: "evince crashes / where does evince store bookmarks?"
date: 2012-05-21
forum: General Help
---

### Post by entropy1 on 2012-05-21
I have been using evince to view a certain .pdf file.  Then I started using the bookmark feature.  Then I re-generated the .pdf file, and now evince either crashes on opening the file, or opens but crashes when I click on a bookmark.  I think the problem is with the bookmarks.  When I copy the file to another location and open it, the bookmarks are gone, and evince is fine with the file.

Where does evince store bookmark information on files that it has opened?  If I can delete that information, I think it might fix my problem.  I am using ubuntu 12.04 64-bit.

---

### Post by entropy1 on 2012-05-22
bump...

---

### Post by entropy1 on 2012-05-28
Anybody?

---

### Post by m1xram on 2012-06-24
This seems relevant, see [Evince List]("http://comments.gmane.org/gmane.comp.gnome.apps.evince.general/1613").

I did 

[INDENT]gvfs-info -a "metadata::evince::bookmarks" /home/me/mag/*.pdf[/INDENT]

It doesn't show the filename but it gets the info. Turn it into a BASH for loop or use the output from find. How about adapting...

[INDENT]```
while read l ; do 
  echo -n "$l:" 
  gvfs-info -a "metadata::evince::bookmarks" "$l" 
done < <(find /home/me/mag/ -name '*.pdf' | sort)

```[/INDENT]

---

