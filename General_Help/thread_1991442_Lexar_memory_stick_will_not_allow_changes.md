---
title: "Lexar memory stick will not allow changes"
date: 2012-05-30
forum: General Help
---

### Post by sofasurfer on 2012-05-30
My Lexar memory stick will not allow me to copy files to it. Thats funny because I did the other day. I have noticed this before also. Whats going on?

---

### Post by coffeecat on 2012-05-30
You haven't given us much to go on. Do you mean that when you plug it in, a file browser window opens but you can only read files, not write to the device? Or do you mean that when you plug it in, no file browser opens at all and the device is not automounted?

Plug the Lexar stick in and then post the output of these two commands:

```
sudo fdisk -lu
mount
```

If you highlight the terminal output with the mouse, you can right-click -> copy for pasting into your post.

---

