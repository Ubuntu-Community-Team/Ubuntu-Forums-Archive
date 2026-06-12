---
title: "Ubuntu_usb_8gb_ghost image"
date: 2012-07-18
forum: General Help
---

### Post by tfernandes on 2012-07-18
[FONT=Comic Sans MS]Hi all,[/FONT]
[FONT=Comic Sans MS][/FONT] 
[FONT=Comic Sans MS]I'm running Ubuntu LTS 12.04 on a USB _ 8 GB. Works fine. [/FONT]
[FONT=Comic Sans MS][/FONT] 
[FONT=Comic Sans MS]I want to move to 16 GB USB. [/FONT]
[FONT=Comic Sans MS][/FONT] 
[FONT=Comic Sans MS]I dont want to re-install ubuntu on the 16GB and re-apply patches, upgrades. [/FONT]
[FONT=Comic Sans MS][/FONT] 
[FONT=Comic Sans MS]Kindly suggest if i can make an image of the 4 GB usb and put it on the 16gb USB if possible.[/FONT]
[FONT=Comic Sans MS][/FONT] 
[FONT=Comic Sans MS]Does redobackup work to re-image[/FONT]
 
[FONT=Comic Sans MS]regards, [/FONT]
[FONT=Comic Sans MS]thaddeus[/FONT]
[FONT=Comic Sans MS][/FONT]

---

### Post by Paddy Landau on 2012-07-18
Copy the entire 8Gb disk to the 16Gb one.

```
sudo cp --archive source target
```

It should work.

---

