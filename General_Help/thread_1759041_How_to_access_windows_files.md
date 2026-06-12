---
title: "How to access windows files?"
date: 2011-05-15
forum: General Help
---

### Post by 5pki66 on 2011-05-15
Hi!

I have both Windows And Ubuntu 11.04 installed. Right now I'm using Ubuntu, but when I wanted to listen to my music I can't seem to find it. It is located on the C-drive in Windows, but I can't find any ways to access that drive. I've also just started using Ubuntu (like 2 hours or so) so I do not know much about it.

So if there is anyone who can give me a detailed and "noob"-friendly instruction on how to deal with this, I would be very happy! :D

---

### Post by sikander3786 on 2011-05-15
Welcome to the forums :-)

Is this a Wubi install or a proper dual boot setup?

If a proper install, you'll see your Windows partition under the Place menu in top panel. Click it and it would open all the files on it.

However, mounting the Windows partition under Ubuntu is not recommended (IMO) as Windows doesn't like many changes to its partition. And moreover, you could accidentally delete any of the key files needed for Windows to work properly.

So, the proper way of sharing files between Ubuntu and Windows is to create a separate NTFS data partition and use it for storing files. You can then set Ubuntu to automatically mount the NTFS partition during boot. NTFS-config tool is available in Software Center to make life easier.

---

### Post by Rubi1200 on 2011-05-15
If you did install with Wubi, the files can be found like this:
Places > Computer > File System > Host

And welcome to the forums from me too :-)

---

### Post by 5pki66 on 2011-05-15
Thanks for the welcomes! :D 

Rubi1200 that was just what I was looking for! Thank you so much, I can listen to my music now! :D I did install it with Wubi.

You just made my day!

---

### Post by Rubi1200 on 2011-05-16
> **5pki66 said:**
> Thanks for the welcomes! :D 

Rubi1200 that was just what I was looking for! Thank you so much, I can listen to my music now! :D I did install it with Wubi.

You just made my day!

Excellent! I am really pleased this worked for you :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

