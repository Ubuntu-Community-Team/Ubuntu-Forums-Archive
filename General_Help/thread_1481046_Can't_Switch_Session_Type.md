---
title: "Can't Switch Session Type"
date: 2010-05-12
forum: General Help
---

### Post by OBI_Ron on 2010-05-12
Hello Everyone,

So, I thought I'd try Gnome as the default session.  Using System...Administration...Login Screen, I selected Gnome as the default session.

When I rebooted, I see an ititial login screen, but when I click on anything, all I get is a black screen and a mouse pointer.

So now I am trying to switch back to the default. So I reboot, hit esc and drop into a root shell, type startx, and I get back to the default environment.

Now, however, When I try to use System...Administration...Login Screen, unlock does not work.  I also tried by using su to change from root to my regular ID, but still, when I click on unlock in the login screen settings dialog, nothing happens.

How can I correct this?  Is there a text file I can edit as root that will alow me to change things back to default?

Thanks in advance!!

---

### Post by MooPi on 2010-05-12
Your post is a bit confusing. What is your default desktop environment? If your using GDM or KDM  you should be able to change between desktop environments. We need more details to help.

---

### Post by OBI_Ron on 2010-05-12
> **MooPi said:**
> Your post is a bit confusing. What is your default desktop environment? If your using GDM or KDM  you should be able to change between desktop environments. We need more details to help.

Sorry for the confusion - It has been so-long since I first installed Ubuntu, I'm not sure what I have been using.  I recently upgraded from 8.04 to 10.04, and everything is working fine.

I just wanted to try a different session type, and like I said, it wont start, and wont allow me to switch back to anything using system administration login screen gui.

That is what I originally used, and when I changed it to Gnome, I had to click the unlock icon and enter the root password.  Now however, clicking on the unlock icon doesn't do anything - it doesn't allow me to enter th password so I can change it back.

I can post some screenshots when I get back home tonight.

Thanks!

---

### Post by OBI_Ron on 2010-05-12
Here is a screen shot of the dialog I am having trouble with.  When I first made the change, I clicked on "Unlock", then entered the root password, made changes, then exited.  Now if I want to change anything, clicking on "Unlock" does not allow me to enter the root password and make changes.

Any help would be greatly appreciated.
[http://picasaweb.google.com/ron.taulbee/Screenshots#5470517715545366802](http://picasaweb.google.com/ron.taulbee/Screenshots#5470517715545366802)

---

### Post by OBI_Ron on 2010-05-12
Solved

I edited /etc/gdm/custom.conf
from
AutomaticLoginEnable=true
To
AutomaticLoginEnable=false

And

from
DefaultSession=kde
To
DefaultSession=gnome

This now allows the gui to work, though I am at a loss foe why I would ever use it again

Thanks

---

