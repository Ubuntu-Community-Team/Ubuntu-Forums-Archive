---
title: "Browser pixelated"
date: 2011-02-11
forum: General Help
---

### Post by troysos on 2011-02-11
I've searched this problem but people seem to have pixelated on their entire system. I only have it inside my browser FF. I'm dual booting with W7 and the browser looks clean and clear when zoomed with Windows. I need the pages to be zoomed a little to read them. It's really strange because when I uploaded pictures, the pictures looked clearer than they do on W7. Even when I have the pictures zoom over 300%, it just looks great. Thank you!

---

### Post by cottfcfan on 2011-02-11
I had the same problem with firefox.
Add this ppa to your sources list, then update & upgrade Firefox and problem should have gone:

ppa:firefox-smooth-scaling/ppa 

Alternatively give Opera a spin, ive been very impressed with it lately:

[http://www.opera.com/browser/](http://www.opera.com/browser/)

---

### Post by troysos on 2011-02-11
Thank you for helping me. Is this something I need to install? Is this something I need to run in the terminal? I'm not sure where to go to get what I need to fix the problem.

---

### Post by cottfcfan on 2011-02-11
Open a terminal and type:
```
sudo add-apt-repository ppa:firefox-smooth-scaling/ppa 
```
Then:
```
sudo apt-get update && sudo apt-get upgrade
```
That should update Firefox & your ready to go.
Firefox may now be called Namoroka or something but ignore that.

---

### Post by troysos on 2011-02-11
Thank you that worked with the scaling problem. I now don't have the close, minimize or maximize buttons on any of my windows? I can't grab the screen and move it around on any of my screens like the browser, pictures, music. Do know how to get those back?

---

### Post by cottfcfan on 2011-02-11
> I now don't have the close, minimize or maximize buttons on any of my windows? I can't grab the screen and move it around on any of my screens like the browser, pictures, music.

Ive no idea why that should happen, never happened to me.
Have you tried simply rebooting?

edit.. Ive just read your post again.
Updating Firefox would not cause that to happen.

---

### Post by troysos on 2011-02-11
Is there a way I can remove what I did?

---

### Post by troysos on 2011-02-11
Never Mind! I think it was the theme that I have installed. I changed to the default theme and then back to the theme I like and Its working fine now. Thank you! :P

---

### Post by cottfcfan on 2011-02-11
Glad you sorted it, you had me worried i'd helped screw your system up for a minute.

---

