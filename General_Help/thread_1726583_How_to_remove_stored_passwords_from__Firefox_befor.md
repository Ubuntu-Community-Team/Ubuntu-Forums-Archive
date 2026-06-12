---
title: "How to remove stored passwords from  Firefox before returning computer?"
date: 2011-04-11
forum: General Help
---

### Post by tc101 on 2011-04-11
I am returning a computer to the dealer and I want to remove all
stored passwords from firefox.  How do I do that?  This is version 3.6.

I also would like to remove bookmarks and history.

---

### Post by ~Plue on 2011-04-11
just delete the .mozilla/firefox/ folder in your home directory and you're done

if you want to to do it selectively, open the firefox preferences window > privacy and security tab
bookmarks would need to be removed separately from the history though

---

### Post by Enigmapond on 2011-04-11
On the top bar of FF you see Edit. Go here then Security and saved passwords. Open and delete them all. For the others, go to Tools/Recent History and delete everything from the beginning of time.. :)

---

### Post by snowpine on 2011-04-11
Personally I would use a utility such as [dban]("http://dban.org") to remove all traces of personal information.

---

### Post by QLee on 2011-04-11
[QUOTE=tc101]I am returning a computer to the dealer and I want to remove all
stored passwords from firefox.  How do I do that?  This is version 3.6.

I also would like to remove bookmarks and history.[/QUOTE]
Well, you don't intend on leaving your user or your user's home on the system, do you?

---

### Post by tc101 on 2011-04-11
> just delete the .mozilla/firefox/ folder in your home directory and you're done

When I go to Places/Home Folder I don't see it.  I assume you mean some thing different by home folder.  How do I find it? 

> Well, you don't intend on leaving your user or your user's home on the system, do you?

How do I remove that?

---

### Post by tc101 on 2011-04-11
I found the mozilla folder under usr/share, but I can't delete it.  Do I have to enter my password?  I don't know how to do that.

---

### Post by bloodorange on 2011-04-11
You need to display hidden files.  If you're using Ubuntu and Nautilus as your file manager, go to View->Show Hidden Files, or press Ctrl+H.  If you're using a different file manager, it should have the same function somewhere.

---

### Post by bloodorange on 2011-04-11
No, don't delete anything in usr/share.

---

### Post by oldos2er on 2011-04-11
.mozilla is a hidden folder in your /home/user folder. Open Places, Home, and hit Ctrl-h to see it.

---

### Post by tc101 on 2011-04-11
Thank you all.  It is done now.

---

