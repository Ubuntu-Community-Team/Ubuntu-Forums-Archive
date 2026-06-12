---
title: "XDMCP logs in with screen upside down and backwards"
date: 2009-07-22
forum: General Help
---

### Post by tjb_15 on 2009-07-22
I'm try to use XDMCP to login in to a remote computer. The login screen shows up normal after connecting. Once I login, this is what I see:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=122092&stc=1&d=1248309571[/IMG]
To close that window I have to click the bottom right corner (were the close button should be.)

Anyone have an Idea?

EDIT: It must be on the remote computer because when I connect to a different computer, everything is normal. Also notice in the screen shot that the mouse cursor is still right side up!

---

### Post by tjb_15 on 2009-07-23
Wow! No one has replied in a day. I figure that I will bump this from the 10th page and sit back and wait.... 

Thanks to who ever replys.

---

### Post by druhboruch on 2009-07-23
Very intriguing...

What video card are you using?

Could you post your gdm.conf and custom.conf?

---

### Post by tjb_15 on 2009-07-24
> **druhboruch said:**
> Very intriguing...

What video card are you using?

Could you post your gdm.conf and custom.conf?

It was the videocard on the remote computer. It has a 32mb Nvidia card. I had to disable the drivers. Works fine now.

---

### Post by magicmarkers on 2010-01-03
Care to tell us how?

---

### Post by tjb_15 on 2010-01-03
> **magicmarkers said:**
> Care to tell us how?
I can't quite remember. I had this problem almost six months ago. I think I disabled the restricted drivers and used the default drivers.

---

