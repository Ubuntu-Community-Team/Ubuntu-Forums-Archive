---
title: "vim copy paste"
date: 2010-06-01
forum: General Help
---

### Post by l3ecl on 2010-06-01
I'm having trouble pasting from a terminal to another source besides a terminal.
I copy the whole document by typing the command " :1,%y " in vim, but then I can't seem to paste it. I can't paste it to my email or gedit, but I can paste it inside the same terminal I copied it from. 
Any ideas?

---

### Post by sdennie on 2010-06-01
I'm not sure about your command (everyone has their own subset if vim knowledge) but, if I type: 1GvG$"+y, it successfully copies an entire file to the system clipboard and I can then Ctrl-V it into anything I want.  That's essentially, "Go to the first line, visually select everything to the last line.  Extend the selection to the end of the last line.  Copy the visual selection to the system clipboard"  I'm sure there is a more succinct way to do it and the "+y I actually stole from the gvim menu so, I don't actually know what it does.  ;)

---

### Post by l3ecl on 2010-06-02
I did what you mentioned, and the lines were yanked. It even says so under vim, but I can't paste them anywhere except the terminal. So I'm able to yank lines but unable to paste. I've tried ctr+v, right click paste, edit->paste, but none work.

---

### Post by PGScooter on 2010-06-02
I think that there are a couple of different clipboards in ubuntu. You could try installing a clipboard manager.
For example. Install parcellite, open it up, right click on the icon on the panel, go to Preferences, click on the check boxes next to both clipboards and click on sync.
Does that do it?

---

### Post by l3ecl on 2010-06-28
sad to say it still did not work =(

---

### Post by l3ecl on 2010-06-29
does any1 else have this problem? i would really like a solution. to reiterate, i can copy from terminal Y, it actually says X lines yanked, but then i can only paste it in the same terminal Y, never to terminal A B C or D

---

### Post by hugmenot on 2010-06-29
Just read :help quoteplus

Summary: The X server has two clipboards, PRIMARY and CLIPBOARD. Primary is usually copied to by selecting text, and CLIPBOARD is what GUI apps use when you copy text. In vim you have to yank to the » + « register to yank to that clipboard. You choose the register with the doulbe quote, hence use "+y as the command to copy to the system clipboard.

---

### Post by lamachine on 2011-02-26
I've installed vim-gtk and vim-gnome but I can't get copying and pasting through the system clipboard. 
Ex: 
Moving the cursor to the line where the text to copy starts. 
Pressing: "+[count]yy (i.e. double-quote followed by + followed optionally by number of lines to yank and then two y's to yank those lines). On the end should those [count] lines be in the clipboard but nothing &#8230;
I've also tried the hugmenot a    nd sdennie advice none of them is working.

---

### Post by asmoore82 on 2011-02-26
You can copy at the Gnome Terminal "level" independent of Vim with Ctrl+Shift+c.

I use Vim "yanking" within Vim but the Gnome Terminal shortcut for everything else.
Also, if it's a one time only paste, you can use the X11 mechanism -
highlight any text and middle-click or wheel-click anywhere to paste.
You actually can paste it multiple times, but you have to be very
careful not to highlight any other text.

---

### Post by hugmenot on 2011-02-26
> **asmoore82 said:**
> You can copy at the Gnome Terminal "level" independent of Vim with Ctrl+Shift+c.


Yeah, but that works only for one screenful.

I think it is 

```
"+y5j
```

To copy five lines down. Or

```
5"+yy
```

to copy five lines linewise. i.e. count comes first

---

### Post by lamachine on 2011-02-27
@asmoore82 thx for the Ctrl+Shift+c hint but you still have to use the mousse for highlighting the text.   
 My point is to get to clipboard visual block selected by vim command.  
 @hugmenot the "+y1j or 1"+yy is not working for me. To execute them as command :1"+yy and :"+y1j doesn't work either.

---

### Post by TeoBigusGeekus on 2011-02-27
```
vim --version
```
If your output has the line
```
-xterm_clipboard
```
you're out of luck: you need to recompile vim with the flag +xterm_clipboard from source.
An alternative is to use gvim.Uninstall vim and install gvim, but don't use it; gvim installs its own version of vim which supports the X and system clipboards. Just start vim (gvim's version) the same way you used to and
```
gg"+yG
```
Copy a whole file and paste it anywhere with right-click>paste
```
gg"*yG
```
Copy a whole file and paste it anywhere with middle-click.

---

### Post by sweetleaf on 2011-02-27
> **TeoBigusGeekus said:**
> 
An alternative is to use gvim. Uninstall vim and install gvim, but don't use it; gvim installs its own version of vim which supports the X and system clipboards. 

```
sudo aptitude install vim-gnome
```

Thanks very much, TeoBigusGeekus. This solved a frustrating problem. Now I can copy text from vim and paste it into firefox.

---

