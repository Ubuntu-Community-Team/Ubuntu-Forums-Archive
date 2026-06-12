---
title: "Installing Gnome in U12.04. Two methods? What's the difference?"
date: 2012-06-03
forum: General Help
---

### Post by charleswb on 2012-06-03
I orginally found these two in a sticky in General Help.

The sticky says to install Gnome for Ubuntu Classic interface do the following (see indented):[INDENT]For U11.10 use this: sudo apt-get install gnome-session-fallback

For U12.04 use this:  sudo apt-get install gnome-panel
[/INDENT]What is the difference between the two methods? 

I accidentally used "sudo apt-get install gnome-session-fallback" on one of my U12.04 computers and it works fine.

I then realized I was supposed to use " sudo apt-get install gnome-panel" for U12.04. So on my next U12.04 computer I used that, and it also works fine.
  
Can I use "sudo apt-get install gnome-session-fallback" on U12.04? It seems to work same as the other method. Am I missing something?

---

### Post by 3rdalbum on 2012-06-03
Gnome Session Fallback depends on Gnome Panel, and Gnome Panel "recommends" Gnome Session Fallback.

Therefore, no matter which one you install, you'll end off with the other one too. No difference.

I tend to tell people "gnome-session-fallback", because it's clearer to them that they're installing a new session rather than just a single panel. Also, gnome-session-fallback will probably ALWAYS depend on everything that you need for a Classic session, whereas Gnome Panel's dependencies might be changed in the future to not include the whole session.

But for 12.04, and possibly for later versions, there's no difference.

---

