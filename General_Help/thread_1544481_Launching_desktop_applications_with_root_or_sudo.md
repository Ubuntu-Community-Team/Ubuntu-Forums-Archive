---
title: "Launching desktop applications with root or sudo"
date: 2010-08-02
forum: General Help
---

### Post by akash.mahakode@gmail.com on 2010-08-02
Hi, 

I have added eclipse to menu in Applications in gnome.
i.e. Applications--> Programming --> Eclipse
I did this by creating "/usr/share/applications/eclipse.desktop" file.

This eclipse can be launched as the currently logged in user, I would like to launch Eclipse with sudo or root.

Please guide to achieve this.


-akash

---

### Post by mcduck on 2010-08-02
It's simple, really. just use "gksudo" instead of "sudo", and you'll get a window asking you for the password before launching the application.

Actually you should always use gksudo instead of sudo with graphical applications, as "sudo" isn't made for that purpose and starting GUI apps with it can in some cases have some nasty results (like configuration files in your user's home becoming owned by root, in worst case preventing the user from logging in any more).

---

### Post by akash.mahakode@gmail.com on 2010-08-02
Hi,

Thanks for the information.... But by using "gksudo" I will be able to launch applications from terminal only. I need to launch the application from Applications menu with root access.

Where should I put "gksudo"?


-akash

---

### Post by mcduck on 2010-08-02
Put the "gksudo" in the command used to launch the application (the "Exec=..."-line, if you are creating the .desktop file by hand). It works just fine in launchers.

---

### Post by akash.mahakode@gmail.com on 2010-08-02
Hi,

Thanks a lot. Its working...

Lets go for treat :D



-akash

---

### Post by akash.mahakode@gmail.com on 2010-08-03
Hi,

The problem that I am facing now is-

After restart, Applications--> Programming --> Eclipse icon got disappeared from Applications menu.

But when I edited /usr/share/applications/eclipse.desktop and saved it. Then Everything was displayed in Application menu.

Is there a way by which I can preserve the Application menu items?

-akash

---

### Post by akash.mahakode@gmail.com on 2010-08-03
Hi Mcduck....


do you have any idea about this?



-akash

---

### Post by mcduck on 2010-08-03
No, not really. I've never seen that happening. But I did see somebody else having similar problem with some menu entries not staying in the menus. You could try to find that thread in case there's some solution.

You could also try adding it into your menu using Gnome's menu editor (right-click the Applications-menu and select "Edit Menus"), just to see if it stays in your menu that way.

---

### Post by akash.mahakode@gmail.com on 2010-08-03
Hi McBuck,

When I manually, run following command---
desktop-file-install <desktop_file>

Eclipse appears again in menu.

I think there may be some registry which would responsible to reload it after restart.



-akash

---

