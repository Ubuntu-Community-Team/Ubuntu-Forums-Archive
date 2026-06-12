---
title: "Screenshot Program?"
date: 2009-12-13
forum: General Help
---

### Post by Grifulkin on 2009-12-13
I have a question I use openbox and am wondering is there any good lightweight screenshot program?  Right now I'm using gimp to take screenshots but I don't like it very much, preferably gtk but qt is fine.  I am looking for something that I can map my Print Screen button to, to take the screenshot.

And speaking of the Print Screen button I haven't tried to map anything to it yet, but is it a special button or can I just do a keybind="Print Screen" in my rc.xml?

Thank you in advance.

~Grif

---

### Post by ~sHyLoCk~ on 2009-12-13
You can map it to execute scrot. It's possible I think.

---

### Post by crimesaucer on 2009-12-13
> **~sHyLoCk~ said:**
> You can map it to execute scrot. It's possible I think.

I agree.

---

### Post by earthpigg on 2009-12-13
```
[chris: ~]$ grep screeny .bashrc
alias screeny='scrot -d 5 -q 100'
[chris: ~]$ 
```

:D

---

### Post by MooPi on 2009-12-13
I haven't bound a key for mine but my Openbox setup I also use lxpanel and I wrote a desktop script that resides there.
Sceenshot.desktop
> [Desktop Entry]
Name=Screenshot
Exec=/home/paul/documents/scripts/Scrott.sh
Type=Application
Categories=Graphics
Icon=camera-photo.svg

---

### Post by Isengrin on 2009-12-13
I like gscreenshot (AUR). It's a small, lightweight and practical GTK interface for scrot.
[[img]http://img69.imageshack.us/img69/4046/thumbgscreenshot.png[/img]](http://subwonderland.totalh.com/Screenshots/gscreenshot.png)

And yes, you can map your key in rc.xml. But not as 'Print Screen', just 'Print'.

If it doesn't work, try ```
xev
``` to see how it's called in your system.

Luck, fellow archer.

Edit: actually, xev alone is pretty intimidating. In case you need it, use:
```
xev | grep -A2 --line-buffered '^KeyRelease' | sed -n '/keycode /s/^.*keycode \([0-9]*\).* (.*, \(.*\)).*$/\1 \2/p'
```

---

### Post by Grifulkin on 2009-12-13
> **Isengrin said:**
> I like gscreenshot (it's in AUR). It's a small and practical GTK interface to scrot.
[[img]http://subwonderland.totalh.com/Screenshots/thumb_gscreenshot.png[/img]](http://subwonderland.totalh.com/Screenshots/gscreenshot.png)

And yes, you can map your key in rc.xml. But not as 'Print Screen', just 'Screen'. If it doesn't work, try ```
xev
``` to see how it's called.

Luck, fellow archer.

Thank you, yeah I have the scrot command that I am going to use wrote a script and am now going to map it to print screen now that I know it isn't called "Print Screen."

Also thank you everyone for the input.:D

---

### Post by Grifulkin on 2009-12-13
Solved:

So I have this as my screenshot script I called it screenshot.sh
```
!# /bin/bash

scrot '%Y-%m-%d-%H-%M.png' -e 'mv $f ~/Pictures/Screenshots'

```

Change ~/Pictures/Screenshots to /path/to/file accordingly.

and I added ```
<keybind key="Print">
  <action name="Execute">
    <execute>/path/to/screenshot.sh</execute>
  </action>
</keybind>
```

this to my rc.xml file.

Now whenever I press the screenshot button the screenshot just ends up in my ~/Pictures/Screenshots folder, very easy and uncomplicated.

:D just in case someone wanted to know how to do it.

---

### Post by Tibuda on 2009-12-13
I bind this oneline script to a hotkey (PrintScreen):
```
scrot -d 3 -e 'gpicview $f' '/tmp/scrot.png'
```
It takes the shot in 3 seconds, saves it in /tmp and open it on gpicview. Then I can save it where I want using gpicview.

EDIT: Grifulkin, you could just save the shot right on your folder, without moving it:
```
scrot '~/Pictures/Screenshots/%Y-%m-%d-%H-%M.png'
```

---

### Post by joey-elijah on 2009-12-13
I don't consider Shutter to be overly heavy - it can be mapped to the print screen button (with options for it to take whole desktop or just a window) etc

Well worth checking out. Also has a great editor built in, too.

---

