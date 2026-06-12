---
title: "Home Folder Organization Issues"
date: 2012-08-02
forum: General Help
---

### Post by JosephBeck on 2012-08-02
So here is my problem. I am in my home folder and I am trying to organize all the subfolders. This is what I am trying to do:

1)Remove the Desktop icon from the home folder and side bar.(Red In Image)
2)Create a folder and have it be in sidebar, not bookmarks (Blue In Image)
3)Organize my folders manually and have them align to a grid.
4)Organize sidebar folders to my own order. 


Is there anyway to do any of this? For such a great OS the ability to organize is  rather subpar. I tried to accomplish this last night and ended up deleting my home folder and nearly losing years upon years of files. Tempted to leave Ubuntu even though I like it so much, just too many problems so far with it. I'm hoping to fix it all soon or just pick a different distro of linux. Also kindly ignore my runescape EpicBot xD. I don't really play but use an account to make gold and give it away.

[IMG]http://i49.tinypic.com/pw46g.png[/IMG]

---

### Post by YankeePride13 on 2012-08-02
> **JosephBeck said:**
> I tried to accomplish this last night and ended up deleting my home folder and nearly losing years upon years of files.

Highly, highly recommend backing up your stuff so that you don't have to worry about accidently deleting all of your files.

---

### Post by JosephBeck on 2012-08-02
> **YankeePride13 said:**
> Highly, highly recommend backing up your stuff so that you don't have to worry about accidently deleting all of your files.

Yeah, I wasn't expecting it to happen. I had changed to tree mode instead to view the sidebar and accidentally moved the home folder into file system and tried deleting it (forgetting that there is a home folder in file system by default). Needless to say I had to come here to the forums for help and in the end found my own round about way of getting my files back from the non-accessible root .trash folder. Scared me half to death so I'll be backing up my 27gb of files on an old computer before I do all that above, I just need to find out HOW to do that stuff before I try and do it. I'm also seeing if Mint or OpenSUSE would fit my tastes better before I go wreck anything.

---

### Post by JosephBeck on 2012-08-02
Bump. Any help?

---

### Post by searchfgold6789 on 2012-08-02
> **JosephBeck said:**
> So here is my problem. I am in my home folder and I am trying to organize all the subfolders. This is what I am trying to do:

1)Remove the Desktop icon from the home folder and side bar.(Red In Image)
2)Create a folder and have it be in sidebar, not bookmarks (Blue In Image)
3)Organize my folders manually and have them align to a grid.
4)Organize sidebar folders to my own order. 


Is there anyway to do any of this?

I don't think you can remove the desktop icon from view, because it's actually a folder.

I think you can actually click'n'drag a folder into the sidebar.

Right click a white area, select "arrange by". I think there is a "Custom" option there if you want to arrange things yourself.

Forgive me for speculating. I don't use the Gnome version.

---

### Post by JosephBeck on 2012-08-03
> **searchfgold6789 said:**
> I don't think you can remove the desktop icon from view, because it's actually a folder.

I think you can actually click'n'drag a folder into the sidebar.

Right click a white area, select "arrange by". I think there is a "Custom" option there if you want to arrange things yourself.

Forgive me for speculating. I don't use the Gnome version.

I use Unity. You can click and drag after the first bookmark is added but thats a bookmark that goes above where it says computer, Im trying to get it below that. And yes, I can manually move them around but they don't align to a grid so it is always uneven.

---

### Post by mc4man on 2012-08-03
If you don't want a desktop icon in the sidebar then disable the FM from handling the Desktop
(dconf-editor > org.gnome.desktop.background, enable then disable as in screen

If you then also don't want a Desktop folder in Home folder then edit
~/.config/user-dirs.dirs & edit the line to 
XDG_DESKTOP_DIR="$HOME"
screen 2
If you want to control all placement in sidebar then try Marlin as a FM, though still being developed, it just uses 'personal' section where anything can go & be re-ordered. (available from a ppa

For fooling around I'd suggest creating a new user & doing so there to see & possibly figure out what you want (if possible
Mess up the new user then just remove & try again or try elsewhere, ect.

---

### Post by JosephBeck on 2012-08-03
> **mc4man said:**
> If you don't want a desktop icon in the sidebar then disable the FM from handling the Desktop
(dconf-editor > org.gnome.desktop.background, enable then disable as in screen

If you then also don't want a Desktop folder in Home folder then edit
~/.config/user-dirs.dirs & edit the line to 
XDG_DESKTOP_DIR="$HOME"
screen 2
If you want to control all placement in sidebar then try Marlin as a FM, though still being developed, it just uses 'personal' section where anything can go & be re-ordered. (available from a ppa

For fooling around I'd suggest creating a new user & doing so there to see & possibly figure out what you want (if possible
Mess up the new user then just remove & try again or try elsewhere, ect.

Thank you very much,I'll experiment with that and hope it works. I really don't get why they didn't put in an align to grid feature for folders when you arrange them manually. Sadly removing the icon from the sidebar makes it unable to place icons on my desktop x-x.

---

