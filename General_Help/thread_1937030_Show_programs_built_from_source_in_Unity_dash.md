---
title: "Show programs built from source in Unity dash?"
date: 2012-03-07
forum: General Help
---

### Post by PortableHuman on 2012-03-07
Hi folks,

I occasionally need to build something from source (I'm sure we all do), for whatever reason. 

I'd like to have these programs show up in Unity's dash search, like apps installed from the Software Center.

Any tips on getting this working? I'm sure it's just a question of creating the relevant files in the relevant place. I've googled, search forums, posted in other forums; no luck.

Thanks!

---

### Post by gordintoronto on 2012-03-07
This is probably the long way round, but Issue 12 of Full Circle Magazine describes how to create a .DEB file. After that, you could install it.

---

### Post by PortableHuman on 2012-03-07
Thanks for the reply. 

You see, that's the idea I initially had, which is why I used "checkinstall --install=yes" instead of "make install", which, as I understand, makes a .deb file for easier management of self-compiled packages. This makes the packages manageable in Synaptic, but that's about it. They're not searchable in dash. Mind you, I think I also did have to set up symlinks for them to /usr/local/bin in order to be able to run them from anywhere, but I don't have to do that with .deb files I download (e.g. Skype) -- I will investigate your suggestion!

---

### Post by stinkeye on 2012-03-07
If you add it to alacarte (main menu) dash will pick it up.
May need to install alacarte.

---

### Post by PortableHuman on 2012-03-07
> **stinkeye said:**
> If you add it to alacarte (main menu) dash will pick it up.
May need to install alacarte.

Ah, excellent, thanks. I'll give this a shot when I get home!

---

### Post by Cheesemill on 2012-03-07
Create a .desktop file for the application and put it in /usr/share/applications

Take a look at the .desktop files already in there to look at the format.

PS. I'm just guessing as I don't use Unity, but it's what I do for gnome-shell.

---

### Post by PortableHuman on 2012-03-07
> **Cheesemill said:**
> Create a .desktop file for the application and put it in /usr/share/applications

Take a look at the .desktop files already in there to look at the format.

PS. I'm just guessing as I don't use Unity, but it's what I do for gnome-shell.

Tried that as well, with no luck. Dash only finds the .desktop file, because it's a recent file, but not the program it is describing.

---

### Post by PortableHuman on 2012-03-07
OK, so I've sorted it out. Alacarte did the trick, although it wouldn't let me add a custom icon, so I had to manually add them to the .desktop files it creates in ~/.local/share/applications.

Since it works by making the appropriate .desktop files, I assume I must have been doing something wrong when I tried to make them by hand.

Either way, problem solved.

Thanks to all of you! :)

---

