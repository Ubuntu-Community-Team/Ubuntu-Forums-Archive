---
title: "xfce4-screenshooter copy to clipboard from command line"
date: 2010-03-10
forum: General Help
---

### Post by gabello on 2010-03-10
Hi,

My xfce4-screenshooter GUI has the option Copy to the Clipboard, but I could not find this option in its' command line help.

I'm trying to bind printscreen key with this. I know that in order for the option to work I need to have the application always running (in GUI thre is option Close the application after screenshot , again somenthing that I can not find in command line).

---

### Post by kerry_s on 2010-03-10
by command line help you mean "man xfce4-screenshooter" or "xfce4-screenshooter --help"?

---

### Post by gabello on 2010-03-10
Yes, terminal command line help.

I manged to get an item (of xfce4-screenshooter) on my panel that after some configuration does what I need, but I would like to bind this action to the Printscreen key (thus I need the command for it)

---

### Post by kerry_s on 2010-03-10
it's in the help commands.

```
xfce4-screenshooter -whs $HOME/Desktop
```

---

### Post by gabello on 2010-03-14
Thank you, but this command does not put the printscreen in the clipboard (so I can paste it somewhere else). This command just saves the printscreen (without a save dialog) in the given directory.

---

### Post by kerry_s on 2010-03-14
> **gabello said:**
> Thank you, but this command does not put the printscreen in the clipboard (so I can paste it somewhere else). This command just saves the printscreen (without a save dialog) in the given directory.

then it don't do that. look around for a different screen-shoot tool. i know gnome's has that option cause i can see it, you can also check out scrot or import which are command line, i don't know if they have that option though.

---

### Post by gabello on 2010-03-14
I know that there is other software able to do this, I just want to do it with this one. And the soft **can** do this (see the print screen from GUI with copy to clipboard option). 

Also, as I said, I was able to have a launcher in the panel to do exactly what I need, and I just want to associate this action to the printscreen key

---

### Post by kerry_s on 2010-03-14
you try just putting the command that calls that? (right click your launcher> properties for the command)

---

### Post by gabello on 2010-03-14
It is not that kind of launcher (where you specify the command). I added it by right click on panel->add new items ->Screnshoot (and then configure the options for it)

---

### Post by kerry_s on 2010-03-14
> **gabello said:**
> It is not that kind of launcher (where you specify the command). I added it by right click on panel->add new items ->Screnshoot (and then configure the options for it)

my bag, for got about the plugin. try "xfce4-screenshooter" just use alt+f2 no need to use the term.

---

### Post by denham2010 on 2010-03-15
UPDATE - Sorry, scratch the following.....there is no way to pass a clipboard option through the cli.......unless you add the option to the source code and compile it yourself.....alternatively, go to the xfce website and request the feature......

Ok,

I have had a look at the source code for the screenshooter, and here is your solution:

```
xfce4-screenshooter -fh
```
for full screen to clipboard

```
xfce4-screenshooter -wh
```
for active window to clipboard

```
xfce4-screenshooter -rh
```
for selected region to clipboard

of course include -d <delay> if you want to have a delay before the screenshot is taken

According to the source, you must include a region (-f fullscreen, -w window or -r region) to prevent the dialog poping up, and, of course, adding h (hide save dialog) to that ensures the image goes to the clipboard.

Cheers.

---

### Post by gabello on 2010-05-28
> **denham2010 said:**
> 
According to the source, you must include a region (-f fullscreen, -w window or -r region) to prevent the dialog poping up, and, of course, adding h (hide save dialog) to that ensures the image goes to the clipboard.

Cheers.

Adding -h does not ensure that the image gets to clipboard, it just saves the image in the home directory without a save dialog.

---

### Post by vtel57 on 2011-02-12
> **gabello said:**
> Hi,

My xfce4-screenshooter GUI has the option Copy to the Clipboard, but I could not find this option in its' command line help.

I'm trying to bind printscreen key with this. I know that in order for the option to work I need to have the application always running (in GUI thre is option Close the application after screenshot , again somenthing that I can not find in command line).

I know this is a really old thread, but I found myself needing to find the answer to this recently, so I thought I'd post the answer here for future seekers of this info.

To bind a key on your keyboard (usually PrintScreen/SysRq) to your xfce4-screenshooter application go to:

**[COLOR="Green"]Xfce Main Menu --> Settings --> Keyboard --> Application Shortcuts tab[/COLOR]**

Add [COLOR="Magenta"]*xfce4-screenshooter*[/COLOR]. A pop up will appear asking you what key you want to bind it to. Just click the key of your choice and you're all set.

Regards,

~Eric

---

