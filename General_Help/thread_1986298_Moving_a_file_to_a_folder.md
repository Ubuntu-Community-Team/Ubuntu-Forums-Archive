---
title: "Moving a file to a folder"
date: 2012-05-24
forum: General Help
---

### Post by garyzw on 2012-05-24
I am looking for a way to move a file by right clicking on it and "move to" a folder that is in the root. 

I have a desktop wallpaper and I would like to right click and have an option to move it to the ".background" folder Is there a script that could do that? The script would have to sudo move the file.

---

### Post by PhantomTurtle on 2012-05-24
I'm not sure how you can add that to the menu but I know how to copy it with root privilages. To do it in Terminal run the following command,
```
cp ~/Pictures/nameofpicture ~/.backgrounds/nameofpicture
```

For root add sudo in front of it.

To do it graphically open Terminal and type in the following,
```
gksudo nautilus
```

This will open nautilus with root privileges. Be careful though, you don't want to delete anything important.

---

### Post by ajgreeny on 2012-05-24
Why bother moving it?  You can use any image as wallpaper from any folder on your system, no matter if it is in root filesystem or your home.

---

### Post by garyzw on 2012-05-24
> **ajgreeny said:**
> Why bother moving it?  You can use any image as wallpaper from any folder on your system, no matter if it is in root filesystem or your home.

I have a picture folder on another drive that I keep my pictures in-- problem is when I re-boot my computer those drives are not auto-mounted and I get a black background.

---

### Post by garyzw on 2012-05-24
That worked--thanks.


> **PhantomTurtle said:**
> I'm not sure how you can add that to the menu but I know how to copy it with root privilages. To do it in Terminal run the following command,
```
cp ~/Pictures/nameofpicture ~/.backgrounds/nameofpicture
```

For root add sudo in front of it.

To do it graphically open Terminal and type in the following,
```
gksudo nautilus
```

This will open nautilus with root privileges. Be careful though, you don't want to delete anything important.

---

### Post by garyzw on 2012-05-24
This seems to be the easiest solution-- In my Home folder I made a folder called Wallpaper and just copied it there-- thanks! 

> **ajgreeny said:**
> Why bother moving it?  You can use any image as wallpaper from any folder on your system, no matter if it is in root filesystem or your home.

---

