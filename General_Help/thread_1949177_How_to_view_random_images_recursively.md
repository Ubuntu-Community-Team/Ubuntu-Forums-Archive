---
title: "How to view random images recursively?"
date: 2012-03-29
forum: General Help
---

### Post by Rytron on 2012-03-29
Hi.

Does anyone know how to view random images recursively? A GUI or terminal method?

Lets say I will use eog (Eye of GNOME) or gthumb to view the images.

Cheers.

---

### Post by irw on 2012-03-29
I don't know how to do this with eog or gthumb, but I use feh:

```
feh -rzsZFD 5 /home/ian/Pictures/
```

recursive, random, fullscreen slideshow; change every 5 seconds

h - pause
m - menu
< - rotate left 90
> - rotate right 90
+/- speed up/slow down delay

Ian

---

### Post by TeoBigusGeekus on 2012-03-29
You can use the shuf command with find. 
Let's say that you want to view random images (jpgs and pngs) from ~/Pictures, ~/My Photos and ~/Camera Shots. You can use something like
```
eog $(find ~/Pictures "~/My Photos" "~/Camera Shots" \( -iname "*.png" -or -iname "*.jpg" \) | shuf -n1)
```

---

### Post by Rytron on 2012-04-01
Thats odd, I never got email notifications for these posts. [Edit - it actually was my spam filter acting up]

Thanks guys for the code lines. ):P

---

### Post by Rytron on 2012-04-02
> **TeoBigusGeekus said:**
> You can use the shuf command with find. 
Let's say that you want to view random images (jpgs and pngs) from ~/Pictures, ~/My Photos and ~/Camera Shots. You can use something like
```
eog $(find ~/Pictures "~/My Photos" "~/Camera Shots" \( -iname "*.png" -or -iname "*.jpg" \) | shuf -n1)
```

I tried this modification of your code.

```
eog $(find ~/Pictures \( -iname "*.png" -or -iname "*.jpg" \) | shuf -n1)
```

It opens a picture (the same photo every time) from 2003 and then opens photos in order after that (all from 2003 folder). :|

---

### Post by Adrian98 on 2012-04-02
I have used the third party applications to view the random images recursively!! ):P

---

### Post by Rytron on 2012-04-02
> **Adrian98 said:**
> I have used the third party applications to view the random images recursively!! ):P

Hi. Could you name them?

---

