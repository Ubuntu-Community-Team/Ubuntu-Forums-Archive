---
title: "Help with loading screen"
date: 2006-06-20
forum: General Help
---

### Post by yesindeed on 2006-06-20
Is there a way to switch the ubuntu loading screen (the one where it says stuff like "loading drivers..." ) to a more traditional text-based one where it shows everything thats going on?

---

### Post by xXx 0wn3d xXx on 2006-06-20
Yes there are two methods to accomplish this.

1. Remove usplash:
> sudo apt-get remove usplash

2. Type:
> sudo gedit /boot/grub/menu.lst
Scroll down a bit and look for stuff like this:
> #defoptions
And remove the word "splash" from that line.
Then run:
> sudo update-grub
in terminal

---

