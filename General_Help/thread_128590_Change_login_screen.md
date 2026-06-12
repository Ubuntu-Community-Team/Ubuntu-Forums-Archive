---
title: "Change login screen?"
date: 2006-02-11
forum: General Help
---

### Post by palomar on 2006-02-11
How do I change the login screen in Kubuntu 5.10? As I can remember from other Linux distributions I have used it was very simple, but I can't find it.

At 'System settings' -> Login Manager there is a menu option called 'GUI style'. But when I chose another theme it makes no difference (after loging off and restart X).

This is not a very serious problem, but the login screen is the first impression of my computer and I think the current default screen is very ugly :p That's why I want to change it ;)

---

### Post by jonathan_c on 2006-02-11
Step 1. Download a KDM login theme from [http://www.kde-look.org/]("http://www.kde-look.org/index.php?xsortmode=down&page=0") and extract the contents to /usr/share/apps/kdm/themes

Step 2. Edit /etc/kde3/kdm/kdmrc and under [X-*-Greeter] section change Theme= to point to your new theme (make sure its the full path to the theme directory)

Step 3. Test by: KDE Menu > Switch User > Start new session or just logout/login your current session

Step 4. Enjoy

---

### Post by palomar on 2006-02-12
thnx :)

---

### Post by Parkotron on 2006-02-12
Try the KDM Theme Manager. You can get it from [http://www.kde-apps.org/content/show.php?content=22120](http://www.kde-apps.org/content/show.php?content=22120) . Saves editing files by hand.

---

