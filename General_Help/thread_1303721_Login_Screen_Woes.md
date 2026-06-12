---
title: "Login Screen Woes"
date: 2009-10-28
forum: General Help
---

### Post by realistik on 2009-10-28
I'm about 2 weeks into using Xubuntu Karmic now and after getting my onboard sound working, it didn't take long to tweak out everything else the way I like it. At this point the only thing I'm not liking is the login screen (the XP user-switcher style thing) but as I understand it, downgrading to a Jaunty GDM would mean I'd also have to downgrade X.org, which ain't gonna happen. I can live with the login screen, but I have one problem that's driving me nuts.

The icon for my user account is the default silver "little person" icon and for the life of me I can't figure out how to change it. After some googling, it seems that I should be able to get it working by putting a png I want to use in ~/.face, but that didn't work. The next thing I tried was making a copy called <my username>.png and putting it in /usr/share/pixmaps/faces/ but still...nothing.

Is it even currently possible to change the icons in Xubuntu? If not, will it be possible when 9.10 is final tomorrow? If anybody has any tips that I may have missed in my googling, or better yet, some secret command-line switch that will turn the face browser off and get me back to that nice clean little box on the corner of the screen asking for my username that was in Jaunty, I'd certainly be pleased to hear about it!

Thanks for your time, reader, and have a nice day! :)

---

### Post by realistik on 2009-10-28
As luck would have it, you can't use a PNG file for this. Converting my ~/.face to JPG fixed it right up.

---

