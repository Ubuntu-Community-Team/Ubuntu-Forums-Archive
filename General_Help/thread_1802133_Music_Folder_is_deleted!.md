---
title: "Music Folder is deleted!"
date: 2011-07-11
forum: General Help
---

### Post by hyfanious on 2011-07-11
Hi I deleted my music folder suddenly
It was empty so I am not worry about data losing
but after that recreate a folder with same name its default icon wont come back
what should I do?
I am aware that I can set icon manually but I am looking for a method that ubuntu recognize that by itself.

---

### Post by WorMzy on 2011-07-11
Run
```
xdg-user-dirs-update
```

---

### Post by hyfanious on 2011-07-11
> **WorMzy said:**
> Run
```
xdg-user-dirs-update
```
Not Working :(

---

### Post by Habitual on 2011-07-11
did you logout and back in after running that?

Plus I think you'd have to remove the Music folder you created then run xdg-user-dirs-update, and logout/in, but I am not certain.

Others may be more certain than I.

---

### Post by hyfanious on 2011-07-12
> **Habitual said:**
> did you logout and back in after running that?

Plus I think you'd have to remove the Music folder you created then run xdg-user-dirs-update, and logout/in, but I am not certain.

Others may be more certain than I.
Yeah
I tried all these possible ways
Nothing Changed :(

---

### Post by mcduck on 2011-07-12
Check *~/.config/user-dirs.dirs* file, and make sure you have the following line in it:

```
XDG_MUSIC_DIR="$HOME/Music"
```

---

### Post by hyfanious on 2011-07-12
> **mcduck said:**
> Check *~/.config/user-dirs.dirs* file, and make sure you have the following line in it:

```
XDG_MUSIC_DIR="$HOME/Music"
```
Thats Righttttt
Thanks veryyyyy muchh

---

### Post by hyfanious on 2011-07-12
But one another question
seeing that file I am just curious if it is possible add more folders?
I mean , I have a folder named "Funny"
is that possible add this folder address to that file and also set a permanent icon for that like the music folder??

---

### Post by mcduck on 2011-07-12
> **hyfanious said:**
> But one another question
seeing that file I am just curious if it is possible add more folders?
I mean , I have a folder named "Funny"
is that possible add this folder address to that file and also set a permanent icon for that like the music folder??

Well, you *could* define one, but as nothing is actually looking for a folder called "Funny" that wouldn't make any difference, and you wouldn't get any special icon for it.

The folders in that file are the ones defined by the freedesktop.org's XDG base directories specification.

[http://www.freedesktop.org/wiki/Home]("http://www.freedesktop.org/wiki/Home")

If you just want a special icon for your "Funny" folder, you can set one in the folder's properties. (or use emblems, like I do ;))

---

