---
title: "Writing to Camera's SD card"
date: 2006-02-18
forum: General Help
---

### Post by jdmml on 2006-02-18
I own a camera and have a secure memory stick... I wish to write files to the memory stick. When I plug the camera in it is found in KDE and i can browse directories at camera://

However when trying to copy a file on to the memory card in konqueror i get "Writing to camera is not supported." All help is greatly appreciated...

Jon

---

### Post by macdo on 2006-02-19
Try copying as root
for example: 
```
sudo cp example.file /media/camera/example.file

```
If that works, then you probably need to edit your /etc/fstab to give users write permissions...

HTH
--
macdo

---

