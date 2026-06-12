---
title: "Creating a shortcut with a pretty icon"
date: 2010-08-04
forum: General Help
---

### Post by Dr_Rent on 2010-08-04
Okay, so this is kind of a trivial issue I'm having with Kubuntu, but it irks me that I cannot find a solution for it. I downloaded the Firefox 4 beta, unpacked it, and created a symbolic link in the /bin/ folder to the "firefox" script that starts the browser. It works great, but I'd like to have Firefox show up in my "Favorites" panel when I click on the K button in the lower left corner of the screen. I couldn't figure out how to do that, so I copied the link to the desktop. Now, the desktop link is just using the default script icon depicting the black terminal window, but I'd really like for it to use the real Firefox icon in the /firefox/icons/ folder.

Of course, the best of all worlds would be if I could get a link to it in the Favorites pane WITH the correct icon. How can I do that?

EDIT: Alright, I finally figured it out. By right clicking on the "Desktop Folder" area of the desktop, I could create a new link to an application. I chose firefox, closed the window, right clicked on the newly created link, clicked properties, clicked the icon, and picked the right one. The icon apparently cannot be chosen when creating the link, only afterward...? Then by right-clicking on the K button I selected Menu Editor, which gave me the option of adding the newly created link to one of the submenus. After adding the icon to the submenu, one can then open the menu up in the applications panel, right click it, and add it to favorites. Seems like kind of a ridiculous process...

---

### Post by lovinglinux on 2010-08-04
Would be better to create a symlink on /usr/local/bin instead /usr/bin.

See my thread about Firefox 4 installation, optimization and customization: [http://ubuntuforums.org/showthread.php?t=1544124](http://ubuntuforums.org/showthread.php?t=1544124)

---

### Post by Dr_Rent on 2010-08-05
I'm still quite new to Linux, so would you mind explaining the thought-process behind putting it in the "local" folder?

---

### Post by lovinglinux on 2010-08-05
> **Dr_Rent said:**
> I'm still quite new to Linux, so would you mind explaining the thought-process behind putting it in the "local" folder?

In your first post you said you have created a symlink in /usr/bin/folder pointing to the "firefox" script that starts the browser. Instead of doing that, you should create the symlink pointing to /usr/local/bin, because /usr/bin/firefox is a file necessary for the default Firefox installed from the repositories. Replacing that file could cause issues with Firefox updates and it would probably be replaced, while /usr/local/bin/firefox is expected to be a file created by the user.

Besides, if you don't like your new Firefox version, you could simply delete /usr/local/bin/firefox, while if you create the symlink to /usr/bin/firefox, you would have to recreate the original symlink to the default installation, to make Firefox work again.

---

### Post by Dr_Rent on 2010-08-05
Ah, I wasn't aware the /usr/local/bin folder had that property. Thank you.

---

### Post by lovinglinux on 2010-08-06
> **Dr_Rent said:**
> Ah, I wasn't aware the /usr/local/bin folder had that property. Thank you.

Yes. If there is no firefox file in /usr/local/bin/, then the system starts Firefox from /usr/bin/firefox, but if there is, then /usr/local/bin/firefox takes precedence.

---

