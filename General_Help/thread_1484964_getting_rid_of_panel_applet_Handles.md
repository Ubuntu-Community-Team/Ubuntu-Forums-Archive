---
title: "getting rid of panel applet Handles"
date: 2010-05-16
forum: General Help
---

### Post by TheNessus on 2010-05-16
in Gnome, every applet has an ugly handle to its left, some themes have it more ugly than others.
Where can I find an option to disable the handles? in the theme rc file? if so, where exactly?

any help would be appreciated.

---

### Post by warfacegod on 2010-05-16
Maybe you should get a pot holder for the handles? Post a screenshot  because I don't think anybody will know what handles are.

---

### Post by TheNessus on 2010-05-16
The thing left of each applet.
marked in red.

[IMG]http://a.imagehost.org/0610/hand1.png[/IMG]
[IMG]http://h.imagehost.org/0409/hand2.png[/IMG]

[IMG]http://i.imagehost.org/0460/hand3.png[/IMG]

---

### Post by warfacegod on 2010-05-16
That's what I thought you were referring to but I didn't want to make an assumption. They bother me, with certain themes, as well. I don't know how to get rid of them or if its even possible. I setting my panels to transparent (I prefer that look anyway) and use Dust Theme controls and they are hardly noticeable with the right background.

You might consider going to /usr/share/themes and finding the appropriate .jpeg or .png and editing it out.

---

### Post by TheNessus on 2010-05-16
I could play all day trying to find what to change, but strangely I don't find anything. There are no .png or .jpeg's of that in either /home//themes or in usr/share/themes, and the gtkrc and panrlrc files are too confusing and I don't know enough in these rc files to know what to change or remove, and when I do change things and restart gnome-panel or change a theme there appears to be no difference. It's mind-boggling, really. 

That's the sort of thing that can push me back to KDE altogether :)

---

### Post by John Bean on 2010-05-16
Does "Lock to panel" make a difference?

---

### Post by TheNessus on 2010-05-16
No, it doesn't.

Which is interesting, because these handles are meant for catching and moving the applets, so why do they show even when the applets are locked?

Maybe I should suggest it to be changed for next release?

---

### Post by John Bean on 2010-05-16
> **TheNessus said:**
> No, it doesn't.

Which is interesting, because these handles are meant for catching and moving the applets, so why do they show even when the applets are locked?

Maybe I should suggest it to be changed for next release?

That's why I asked. I don't see them in the (default) theme I'm using now but had a vague recollection of them being affected by lock status when I've seen them in the past. On reflection I think I was probably remembering Windows where the handles do vanish if you lock the taskbar, which does seem sensible.

---

### Post by kerry_s on 2010-05-16
have you tried right clicking the handles-> properties, see if it has handle settings?

---

### Post by TheNessus on 2010-05-16
> **kerry_s said:**
> have you tried right clicking the handles-> properties, see if it has handle settings?

most applets have only an 'about' option
never saw a handle option

---

### Post by kerry_s on 2010-05-17
> **TheNessus said:**
> most applets have only an 'about' option
never saw a handle option

it was worth a check. :)

since you've never seen a handle option, i'll show you xfce4-panel.

---

### Post by warfacegod on 2010-05-17
Deleting this *might* help:

```
/usr/share/icons/hicolor/scalable/apps/gnome-panel-separator.svg
```

---

### Post by TheNessus on 2010-06-17
Any idea then?

in the theme "egtk" there is no such a 'hande' or whatever it is called.

Does anyone here have any exp in designing a gtk theme?

---

### Post by wojox on 2010-06-17
Right click and remove from panel works for me. Unless it's the Window List.

---

### Post by TheNessus on 2010-06-17
What? No. I don't want to delete an applet. Just its ugly handle.

---

