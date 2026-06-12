---
title: "Blank screen after GRUB after uninstalling KDE"
date: 2011-06-24
forum: General Help
---

### Post by MiThRaZoR on 2011-06-24
And by blank screen I mean after I pick whatever I want on GRUB. There's NOTHING.

I even tried going in recovery mode. But same thing.


Right now I'm using an older recovery. The newest thing is completely broken. And the regular one for the Ubuntu version doesn't work either.

Any help would be appreciated.

---

### Post by oldfred on 2011-06-24
Post this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by MiThRaZoR on 2011-06-24
Thanks for your help so much. But I got it to work! But honestly. I have no idea how I did it. I was just putting in random commands.

Is there any way to see what I typed in the terminal? (After rebooting)

I know it had something to do with the gnome environment. Nothing with the graphics card or anything.


I remember putting in these

```
sudo apt-get remove --purge ubuntu-desktop
sudo apt-get install ubuntu-desktop
```

```
sudo dpkg-reconfigure xserver-xorg
sudo dpkg-reconfigure gdm
```

I'm not sure what it was. I tried many other commands. But I'm PRETTY sure it was one of those.

I hope this helps anyone else that has the same problem.

---

### Post by oldfred on 2011-06-24
The command history lists the commands you have run. It saves something like 500 or 1000, but that can be reset. No sudo required.

```
history
```

---

