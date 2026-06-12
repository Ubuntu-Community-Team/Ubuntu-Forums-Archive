---
title: "move notifications in gnome shell"
date: 2011-10-17
forum: General Help
---

### Post by Eraemaajaervi on 2011-10-17
hi,

switched to 11.10 and installed gnome-shell. it has a few drawbacks and the biggest is the huge notification area which covers about 40px at the bottom of the screen, which is very annoying when working in full-screen terminal.

how do i move the notifications?
nice would be an icon in the top bar (there is so much space there, unused). even moving that thing in the lower right corner would already help...

i'm familiar with css, so maybe someone could point out the relevant classes in the gnome-shell.css



and since i'm already at it: has anyone found an alternative way of showing all running applications (like a taskbar) he prefers to the native gnome shell solution?

thanks

---

### Post by Eraemaajaervi on 2011-10-18
just a small bump.


no ideas how to solve this?

---

### Post by markbl on 2011-10-31
I've recently adopted gnome shell also, on ubuntu 11.10. I really like it much better than Unity but the notification system needs work. Having the notifications dump themselves over the bottom terminal command line where we spend much of our day is very annoying. I am surprised the gnome developers have not fixed this for themselves yet.

---

### Post by Trilby on 2011-12-19
I know it can be done (ie move notifications to the top bar) since I've seen others with that set up. I've not worked out quite how to do it yet myself. If I do, I'll post it here.

UPDATE 1: There us some information here: [http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html) but I've tried the solution and it does nothing. If someone else could see what they get from:

```

sudo add-apt-repository ppa:webupd8team/gnome3
sudo apt-get update
sudo apt-get install gnome-shell-classic-systray

```

Then press alt-f4 and enter ' r ' to refresh the interface.

---

### Post by thaelim on 2011-12-19
After installing the extension using that method, you need to enable it using gnome-tweak-tool. Having said that, I'm not sure this extension actually moves the notifications, only the notification *icons*

---

### Post by Trilby on 2011-12-19
> **thaelim said:**
> After installing the extension using that method, you need to enable it using gnome-tweak-tool. Having said that, I'm not sure this extension actually moves the notifications, only the notification *icons*

Having now enabled it (#-o), I see what you mean. Better than nothing I suppose. It'll do for the moment but I'll keep looking for something more complete.

EDIT 1: I also tried this: [http://www.webupd8.org/2011/06/move-icons-from-message-tray-to-top.html](http://www.webupd8.org/2011/06/move-icons-from-message-tray-to-top.html) but it broke the shell interface to a degree of inoperability.[URL="http://www.webupd8.org/2011/06/move-icons-from-message-tray-to-top.html"]
[/URL]

---

