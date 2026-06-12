---
title: "Connecting to remote Byobu session"
date: 2012-07-31
forum: General Help
---

### Post by caleb9 on 2012-07-31
Hi. I've been searching around for a solution for my problem but found nothing. Does anyone know how to resize remote byobu window? The problem is as follows: I have a Gentoo desktop running a byobu session, and I'm trying to connect to it from my Ubuntu laptop via ssh. So to avoid byobu-within-byobu problem, I start regular Terminal on the laptop, and ssh to the desktop. Now the problem is that remote byobu windows are of different size than what can be displayed on my laptop screen. I've attached a screenshot showing the issue.
I have no idea how to resize such window. i tried many key combinations, including Ctrl+Left/Right but nothing seems to work. I'd appreciate any help, thanks.

---

### Post by nothingspecial on 2012-07-31
byobu has an option to use a backend of either screen or tmux. I have never found a reliable way to do this with tmux but if you exit byobu then run

```
byobu-select-backend
```

and choose screen (it defaults to tmux) then you can redraw the screen with Ctrl-A Shift-F when you log in from different machines.

Both tmux and screen have advantages and disadvantages, but if this is something you do often then screen is the choice.



......unless someone knows how to do it with tmux in which case I'm all ears :)

---

### Post by Kirboosy on 2012-07-31
> **nothingspecial said:**
> byobu has an option to use a backend of either screen or tmux. I have never found a reliable way to do this with tmux but if you exit byobu then run....

+1 **BUT** just in case that doesn't work check out this [thread]("http://ubuntuforums.org/showthread.php?t=2001637") ;)

[X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution#Setting_resolution_changes_in_xorg.conf_--_resolution_lower_than_expected")

---

### Post by caleb9 on 2012-07-31
Thanks, that would be just what I need, but I've changed the backend on server to screen and the result is that when I connect to it, it seems to start a new byobu session instead of connecting to the already running one. Any ideas how can I force it to select the right one?

---

### Post by caleb9 on 2012-07-31
> **nothingspecial said:**
> byobu has an option to use a backend of either screen or tmux. I have never found a reliable way to do this with tmux but if you exit byobu then run

```
byobu-select-backend
```

and choose screen (it defaults to tmux) then you can redraw the screen with Ctrl-A Shift-F when you log in from different machines.

Both tmux and screen have advantages and disadvantages, but if this is something you do often then screen is the choice.



......unless someone knows how to do it with tmux in which case I'm all ears :)

Thanks, that would be just what I need, but I've changed the backend on server to screen and the result is that when I connect to it, it seems to start a new byobu session instead of connecting to the already running one. Any ideas how can I force it to select the right one?

(sorry for double post but I'm new to this forum and can't seem to find a way to delete a post ;( )

---

### Post by Kirboosy on 2012-07-31
> **caleb9 said:**
>  Any ideas how can I force it to select the right one?

See if this answer helps any.

[Ask Ubuntu]("http://askubuntu.com/questions/94564/how-to-run-multiple-byobu-sessions-at-once")

---

### Post by caleb9 on 2012-07-31
> **Caboose885 said:**
> +1 **BUT** just in case that doesn't work check out this [thread]("http://ubuntuforums.org/showthread.php?t=2001637") ;)

[X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution#Setting_resolution_changes_in_xorg.conf_--_resolution_lower_than_expected")

Thanks though I don't think forcing a specific resolution is the problem here. The remote byobu window is not full-screen but just arbitrary size, and the two screens (desktop and laptop) differ in resolution a lot.

---

### Post by caleb9 on 2012-07-31
> **Caboose885 said:**
> See if this answer helps any.

[Ask Ubuntu]("http://askubuntu.com/questions/94564/how-to-run-multiple-byobu-sessions-at-once")

Ok so I've set byobu-select-backend to screen, then started byobu with byobu-shell on the server. On the client after ssh it doesn't start byobu automatically anymore so I do byobu-select-session and it connects to the right one. Unfortunately Ctrl+a F doesn't resize the window, like there was no reaction to it ;(.

---

### Post by Kirboosy on 2012-07-31
Try opening the ssh connection from TTY1 session and see if the formatting issues still occur. 

If my memory jogs me correctly I always had formatting issues on my server when I had a monitor hooked up to it....or was it if I had xserver running.... I really don't remember anymore. My Ubuntu Server sits in the corner headless and no GUI. 

I will keep poking around the Internet and see what I can turn up

---

### Post by caleb9 on 2012-07-31
Ok the problem seems to be on my Gentoo box, as even testing it locally on two separate terminals (of differing sizes) I'm able to resize with Ctrl+a F on Ubuntu and not able to do it on Gentoo. On Ubuntu this shortcut works despite the backend selected. This is interesting considering that on Gentoo the byobu version is newer (5.18) than on Ubuntu (5.17).
That said, probably I should look for solution on Gentoo's forums, though people there don't seem to care much about byobu :(.

---

### Post by angelv on 2012-11-21
Hi, I have the same problem with Ubuntu 12.10. I didn't have it until now (when I was running Ubuntu 11.10 in two machines), but right now I also have that window full of dots, and no way to resize it. I'm going to investigate, since I use this daily, and not being able to resize the window to its full size is quite annoying...

---

### Post by angelv on 2012-11-21
I just found out that this only seems to happen with tmux. Did you try to select screen as the backend?

[http://askubuntu.com/questions/220104/how-to-resize-byobu-in-ubuntu-12-10](http://askubuntu.com/questions/220104/how-to-resize-byobu-in-ubuntu-12-10)

---

