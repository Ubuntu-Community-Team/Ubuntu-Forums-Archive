---
title: "General Error Mounting Filesystems"
date: 2011-12-04
forum: General Help
---

### Post by StartedTheFire on 2011-12-04
I've made a huge mistake.

Yesterday I was trying to mount an .iso and couldn't figure out how to do it, so I ended up doing something dumb like copying the iso to /etc/fstab. It did something but I looked back at it in the terminal and fstab isn't actually a folder.... I decided to just give up and assumed I hadn't caused anything to happen. But now it can't boot at all and I get "General error mounting filesystems" right after GRUB. I'm posting this from windows.

I googled the error and saw someone else mentioning /etc/fstab, so I realized what I had done. I'm making a new thread because I seem to be in a unique situation. Is there a way to reset fstab? What is fstab anyway?

The answer is probably just to "update 11.04 to 11.04" with my install disk (oneric is lame), but I'd like to know if I can do it less stupidly.

---

### Post by 2F4U on 2011-12-04
Did I understand this right, you copied the iso ON /etc/fstab, i. e. you replaced /etc/fstab with the iso?
If that is true, it is only natural that you cannot boot since /etc/fstab lists all accessible filesystems and Ubuntu needs this to boot up correctly.

---

### Post by StartedTheFire on 2011-12-04
Yes... I think that's what I did.

---

