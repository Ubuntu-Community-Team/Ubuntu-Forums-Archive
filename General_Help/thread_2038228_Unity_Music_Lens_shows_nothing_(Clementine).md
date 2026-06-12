---
title: "Unity Music Lens shows nothing (Clementine)"
date: 2012-08-06
forum: General Help
---

### Post by MrsUser on 2012-08-06
Hello,

I have a problem with the music lens in Unity. It doesn't show anything. Does this have to do with the fact that I use Clementine instead of Rhythmbox? And if so, how can I make Unity music lens to work with Clementine? Because I don't want to use Rhythmbox (I think it sucks big time).

Using Ubuntu 12.04 64-bit and Clementine 1.0.1

---

### Post by kev77 on 2012-08-06
Open terminal and enter these lines of code one at a time;

```
sudo add-apt-repository ppa:markjtully/ppa
sudo apt-get update
sudo apt-get install clementine-scope
```


Thanks to askubuntu  [http://askubuntu.com/questions/61679/how-to-change-the-search-location-of-unitys-music-lens-with-clementine-instead]("http://askubuntu.com/questions/61679/how-to-change-the-search-location-of-unitys-music-lens-with-clementine-instead")


Logout and login for the changes to take effect.

---

### Post by MrsUser on 2012-08-07
Thank you. This works. However, it's buggy as hell. Every time I do a search through this lens, I get an "internal error" box  :-/

[IMG]http://i.imgur.com/cS5vX.png[/IMG]

This renders the lens unusable. I hope Ubuntu will get native lens support for other players than Rhythmbox.

---

