---
title: "Customize login screen in Ubuntu 11.04"
date: 2011-05-02
forum: General Help
---

### Post by garble on 2011-05-02
I used Ubuntu Tweak to change the background of the login screen, but the highlighting on the names and buttons is still orange. I want to change this.

Does 11.04 support GDM themes? Will GDM themes from gnome-look.org work properly in 11.04? Is there another way to do this without GDM themes?

---

### Post by zvacet on 2011-05-02
You can change that under appearance.Select some other theme and customize it.

---

### Post by garble on 2011-05-02
I think you misunderstood my question. I am asking about the login screen where you enter your username and password.

Look at this screenshot I found online. See how the highlighting on the buttons and menus is orange? I want to change that color.

[http://4.bp.blogspot.com/-SC0X_SIdupw/TZIsmY73jyI/AAAAAAAACA8/l2ZCvM8OdJw/s1600/Ubuntu-GNOME.png](http://4.bp.blogspot.com/-SC0X_SIdupw/TZIsmY73jyI/AAAAAAAACA8/l2ZCvM8OdJw/s1600/Ubuntu-GNOME.png)

---

### Post by garble on 2011-05-02
After some more Googling, I found the solution:

[http://ubuntuforums.org/showpost.php?p=10240432&postcount=3](http://ubuntuforums.org/showpost.php?p=10240432&postcount=3)

---

### Post by zvacet on 2011-05-03
Yes,I misunderstood your question.Glad you find solution.it is good thing to know.Tnx.

---

### Post by supravat on 2011-05-09
step 1: sudo cp /usr/share/application/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow

Step 2: log out your current session

Step 3: Now change what ever you want..
step 4: Login
Step 5: sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop

---

### Post by Conisant on 2011-05-16
Hey there,

well there is an other way to access the settings for gdm, eventho it takes a few more steps, but you can easily install themes with it.

I bloged about it at [URL="http://blog.azieger.de/index.php?archives/7-English.html&serendipity[lang_selected]=en"]http://blog.azieger.de/index.php?archives/7-English.html&serendipity[lang_selected]=en
[/URL] 
1. $ sudo gedit /etc/passwd
change
gdm: x:106:114:Gnome Display Manager:/var/lib/gdm:/bin/false
to something like
gdm: x:106:114:Gnome Display Manager:/var/lib/gdm:/bin/bash
2. $ xhost +LOCAL:
3. $ sudo su gdm[/CODE]
4. $ export DISPLAY=:0.0 
5. $ gnome-control-center

Well after you're done change back the passwd to revoke shell access for gdm.

---

### Post by dancer_69 on 2011-06-01
Can you please explain better the procedure?
xhost +LOCAL: gives:
non-network local connections being added to access control list
and if I ignore it and go to next command I get
Unknown identity: gdm[/CODE]

---

