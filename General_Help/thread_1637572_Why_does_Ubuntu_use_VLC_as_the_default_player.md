---
title: "Why does Ubuntu use VLC as the default player"
date: 2010-12-04
forum: General Help
---

### Post by Mindswap1 on 2010-12-04
Hi guys I was wondering why VLC is not the default player for Ubuntu 10.10. Is it not good? Is the default one installed in 10.10 better?

---

### Post by endotherm on 2010-12-04
vlc is a good product, but it is kind of monolithic at times, because it is fully self-contained. Totem is a gnome-project application, so it integrates better into the gnome desktop. you can also use differant backends with totem (gstreamer, xine, etc) and its easy to load external technologies like codecs. my guess is that gstreamer is a big part of why it is default. anyway, from a systems integrators perspective, mplayer or totem just seem like a more flexible choice. when a change happens in the upstream, that the ubuntu guys don't think jives with the Ubuntu desktop, they have a lot more choices with a more modular player. vlc's selfcontained nature makes it really easy to port across platforms, but it limits its potential for integration.

my other thought, is that when correctly configured, totem provides a better picture quality than vlc. Personally I use smplayer most. it plays high res content the smoothest (since it uses mplayer as the backend) but also has a nice ui, and plenty of features. since it is well integrated, it's easy to cue up video across smb or nfs shares, a feature I really need. 

vlc is my fall-back for anything I have trouble playing. it is likely the most portable video player available, and it does play almost anything. but I feel like its only optimal in pessimistic circumstances. 

so those are just my thoughts on the matter. I have no relationship with canonical, so these are just the reasons I would choose not to use vlc as my distro default.

---

### Post by hawthornso23 on 2010-12-04
Also having a more modular player is better if patents and legal issues are a concern. You then have the option of not loading codecs that have legal issues by default, and leaving the decision as to whether to download and install these up to the computer owner.

Whereas with VLC it is everything or nothing.

---

