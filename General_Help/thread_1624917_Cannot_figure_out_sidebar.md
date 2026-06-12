---
title: "Cannot figure out sidebar"
date: 2010-11-18
forum: General Help
---

### Post by wisnoskij on 2010-11-18
Hello,

I just installed Ubuntu Netbook Remix 10.10 (I think) x86.
and it seems to have changed from recent versions, as I am unable to do many things that are mentioned in instructions online that I am trying to follow.

The issues all stem from the side bar.
The following image seems to show what everyone else is working with.
[https://wiki.ubuntu.com/UNR?action=AttachFile&do=get&target=unr-favorites-small.png](https://wiki.ubuntu.com/UNR?action=AttachFile&do=get&target=unr-favorites-small.png)

But I am stuck with just a bar with a few shortcuts on it, like firefox.
and the only way that I can add to the bar is to get a program running and then it will appear in the bar and I can right click>"add to launcher" it.
But what I really want is a fully customizable menu, and I even have a application named Main Menu that appears to be the customization agent for the menu shown in the picture and I can add and remove items however I want with it (but I cannot get this menu to show up on my screen).

---

### Post by kerry_s on 2010-11-18
> [https://wiki.ubuntu.com/UNR?action=AttachFile&do=get&target=unr-favorites-small.png](https://wiki.ubuntu.com/UNR?action=AttachFile&do=get&target=unr-favorites-small.png)

that is the old version <10.04
the new netbook in 10.10 uses unity, it is very limited being the first version. when you add/remove stuff it takes a log out & back in for the menu to update. the right click a launched app & gconf-editor is the only way so far to get shortcuts on the panel.

there making another change to unity in the next release, it will soon be the default desktop, so hopefully they take more time to add features.

---

### Post by wisnoskij on 2010-11-18
thank you,
Just a note for anyone else in a similar situation, it seems that Applications on unity (the only graphical place to start programs) does not have a gconf entry, you have to type "gconf-editor" into the terminal.

---

