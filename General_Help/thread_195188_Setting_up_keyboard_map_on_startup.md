---
title: "Setting up keyboard map on startup"
date: 2006-06-12
forum: General Help
---

### Post by aoberoi on 2006-06-12
I have a Logitech keyboard (Cordless Desktop Pro) that has some multimedia keys that I'd like mapped so i can use them when im in Ubuntu. I figured out that the way i can make them work is if i run ```
xmodmap ~/.Xmodmap
``` to map my keys to the custom map i stored in my home folder and then go to System->Preferences->Keyboard Shortcuts and map the keys to the action i want in there.

My question is, how can i automatically run all of that without my input at the beginning of every time i log in? Is there a script i can write to make the Keyboard Shortcuts part to happen too? Where would i put this script and how exactly would i write it (I've never written shell script before i just happen to know what it is)?

Anyone that has any advice for me would be much appreciated. Thanks

---

### Post by blackjack6.21.91 on 2006-06-14
Sounds like a bash shell script should do the trick.  And generally they're not at all hard to make.  [Here]("http://linuxhelp.blogspot.com/2005/10/10-seconds-guide-to-bash-shell.html")s a guide I'm quite fond of.  You could put the script wherever you'd like, just go to
System -> Preferences -> Sessions, and add the files location to the startup programs tab.  Hope I'm helpful,

blackjack

---

### Post by aoberoi on 2006-06-16
thanks for your reply,

i figured out the problem by changing the contents of the following file:
/etc/X11/xkb/symbols/inet

In that file the keycodes were stored wrong under the logitech entry. I modified those to match the mapping i knew was correct and poof .. upon restarting x i didnt have to worry about it.

---

