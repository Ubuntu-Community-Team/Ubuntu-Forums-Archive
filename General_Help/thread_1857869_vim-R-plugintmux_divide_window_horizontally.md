---
title: "vim-R-plugin/tmux: divide window horizontally"
date: 2011-10-11
forum: General Help
---

### Post by CryptKeeper777 on 2011-10-11
I've managed to successfully install vim-R-plugin with the help of this forum. When I start the plugin with \rf, the vim-window is vertically divided and R starts in the lower panel. How can I change this behavior so that the terminal window is divided horizontally instead of vertically (preferably with the new panel in which R starts on the left of the initial vim panel)?

I suppose this could be achieved by editing the command which initiates tmux (which divides the terminal window), so I looked though the vim-R-plugin-files, but I didn't find anything...

---

### Post by jalvesaq on 2011-10-11
The meaning of horizontal is ambiguous. If the two panels are side by side they are horizontally aligned relative to each other, but they are divided by a vertical line. Tmux and Vim documentations use opposite meanings for “vertical” and “horizontal”. Tip: The Vim-R-plugin has an option to do what you want.

---

### Post by CryptKeeper777 on 2011-10-11
I know the terms aren't really clear; what I want is one window (preferably R) on the left and the other on the right (preferably vim). 

Where is that option you mentioned? I've looked through the vim-R-plugin manual before I opened the thread but I didn't find anything...

---

### Post by jalvesaq on 2011-10-11
> **CryptKeeper777 said:**
> I know the terms aren't really clear; what I want is one window (preferably R) on the left and the other on the right (preferably vim). 

Where is that option you mentioned? I've looked through the vim-R-plugin manual before I opened the thread but I didn't find anything...

Put this in your vimrc:

```
   let vimrplugin_screenvsplit = 1
   let g:ScreenImpl = 'Tmux'
```

More info:

:h vimrplugin_screenvsplit

---

### Post by CryptKeeper777 on 2011-10-11
> **jalvesaq said:**
> Put this in your vimrc:

```
   let vimrplugin_screenvsplit = 1
   let g:ScreenImpl = 'Tmux'
```More info:

:h vimrplugin_screenvsplit
Thanks a lot, now it works. Only detail: The new panel with R is opened to the right of the vim panel. But pressing <Ctrl><a>+<o> switches the panels. Then all is perfect.

---

