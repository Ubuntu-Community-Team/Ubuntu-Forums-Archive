---
title: "How to configure Login Screen Mouse??"
date: 2010-11-11
forum: General Help
---

### Post by drknot on 2010-11-11
I've looked and can't find an answer yet.

Once I login I have my left-handed mouse and preferred pointer

BUT during log-in log-out the ?session manager screen reverts to the standard pointer, and worse, to a right handed configuration.

I've been through gconf-editor options but can't find a suitable variable to tweak.

Please let me know if it is possible to change the options for the login screen in such a way - and how to sort out my mouse!

Thanks in advance

---

### Post by sisco311 on 2010-11-11
Hi, 

Add gnome-mouse-properties and gnome-appearance-properties to GDM's autostart:
```
sudo ln -s /usr/share/applications/gnome-settings-mouse.desktop /usr/share/gdm/autostart/LoginWindow/
sudo ln -s /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```

Log out.  After the login window appears the two windows should also appear. Configure GDM how you want, then close the windows and log back in. When you're done and want the window to stop opening with GDM run this:
```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-settings-mouse.desktop
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

### Post by drknot on 2010-11-11
Works beautifully. Many thanks.

---

### Post by drknot on 2010-11-13
Follow up :

still a small issue

I've successfully changed the appearance of the pointer.

The Left handed /Right Handed radio buttons have no effect whatsoever in the login screen so only part solved I am afraid.

Thanks

---

### Post by Belfry on 2010-12-03
I modified /etc/gdm/Init/Default,  adding the following line to the end:
```
/usr/bin/xmodmap -e 'pointer = 3 2 1'
exit 0 #this line should already be present
```

Important: this setting is global, and reverses the mouse buttons on all accounts. So right-handed users need to set their mouses for left-handed operation and vice-versa.

---

