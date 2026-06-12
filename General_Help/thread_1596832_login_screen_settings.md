---
title: "login screen settings"
date: 2010-10-14
forum: General Help
---

### Post by lazylew on 2010-10-14
I'm the only one using this pc, so I want to enable automatic login.
When I open the "login screen settings" though, it's greyed out (inactive) and the "unlock" doesn't do anything.

I also have something about "keyring" asking my password each time just after login, which isn't pleasant.

Any solutions for either or both issues?

---

### Post by requeth on 2010-10-14
Your administrator account that's setup during install of Ubuntu can't be used as an auto-login account. If you create another account, even with the same permissions, it'll show up in the login screen page. Make sure to check the box when creating the user saying "do not ask for password on login". I can't find a way to set that check box after the account is created, thus not being able to select your admin account.

I had the keyring problem a few versions back and I think I had to change the root password to match my admin password.

---

### Post by cavalier911 on 2010-10-14
[LEFT]See thread #2 for solution:
[http://ubuntuforums.org/showthread.php?t=1505281](http://ubuntuforums.org/showthread.php?t=1505281)[/LEFT]

---

### Post by lazylew on 2010-10-14
> **cavalier911 said:**
> [LEFT]See thread #2 for solution:
[http://ubuntuforums.org/showthread.php?t=1505281](http://ubuntuforums.org/showthread.php?t=1505281)[/LEFT]
 If you mean the post by Cavalier 911, it's a bit too cryptic - might be due to the late hour here ;-) I'll look at it again tomorrow and see if it makes sense.

---

### Post by lazylew on 2010-10-14
> **requeth said:**
> Your administrator account that's setup during install of Ubuntu can't be used as an auto-login account. If you create another account, even with the same permissions, it'll show up in the login screen page. Make sure to check the box when creating the user saying "do not ask for password on login". I can't find a way to set that check box after the account is created, thus not being able to select your admin account.

I had the keyring problem a few versions back and I think I had to change the root password to match my admin password. I went to "users & groups" and set myself as admin and also set it so that I should be able to login without passwd, but to no avail; I still get the user login.

---

### Post by cavalier911 on 2010-10-14
I have the greyed out "Don't ask for password on login" checkbox.
There are a couple bug reports about it.
I'm using lubuntu 10.07 Lucid.


```
sudo nano /etc/xdg/lubuntu/lxdm/lxdm.conf
```:

```
[base]
autologin=_**USERNAME GOES HERE**_
session=/usr/bin/startlubuntu
numlock=1
greeter=/usr/lib/lxdm/lxdm-greeter-gtk

[server]
# arg=/usr/bin/X -nr vt1

[display]
gtk_theme=Clearlooks
bg=/usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png
bottom_pane=1
lang=1
theme=Lubuntu

[input]


```

This will work if update-alternative is correctly linking /etc/xdg/lubuntu/lxdm/lxdm.conf to /etc/lxdm/default.conf

To fix run what's in **bold** and choose the number by /etc/xdg/lubuntu/lxdm/lxdm.conf and hit Enter

rj@lubuntu:~$ **sudo update-alternatives --config lxdm.conf **
There are 2 choices for the alternative lxdm.conf (providing /etc/lxdm/default.conf).

  Selection    Path                             Priority   Status
------------------------------------------------------------
* 0            /etc/xdg/lubuntu/lxdm/lxdm.conf   60        auto mode
  1            /etc/lxdm/lxdm.conf               50        manual mode
  2            /etc/xdg/lubuntu/lxdm/lxdm.conf   60        manual mode

Press enter to keep the current choice
[*], or type selection number:

---

### Post by lazylew on 2010-10-15
> **cavalier911 said:**
> 
...Selection    Path                             Priority   Status
------------------------------------------------------------
* 0            /etc/xdg/lubuntu/lxdm/lxdm.conf   60        auto mode
  1            /etc/lxdm/lxdm.conf               50        manual mode
  2            /etc/xdg/lubuntu/lxdm/lxdm.conf   60        manual mode

Press enter to keep the current choice
[*], or type selection number:
I wasn't sure which one to pick, so left it at *
It works :)

It did somehow alter my task panel as well (browser icon changed to not working eg) and I still get the keyring passwd question, but login is automatic now. Thanks!

Still I'm considering a change to Xubuntu (not because of the login thing though)
I'm in an experimental mood ;-)

---

### Post by SteveDee on 2010-10-15
> **lazylew said:**
> ... I still get the keyring passwd question, but login is automatic now...



The user keyring is held in:
```

 $Home/.gnome2/keyrings/default.keyring

```

Deleting this file forces a request for fresh network keyphrase next time system starts. If you then use a blank password, it will stop asking you for a password.

---

### Post by cavalier911 on 2010-10-15
Thanks SteveDee for pointing me in the right direction.

This should stop prompt for password on network connect:

Check your network connection permissions.
Right click NetworkManager applet next to clock choose Edit Connections ...
Pick the tab that has your connection, highlight the connection, click the Edit button on the right
Authenticate to escalate your permissions
Check  **Connect automatically** and **Available to all Users**
Click Apply

To fix the browser icon:
Move the old panel file out in case you want to reference it for your custom configs.
```
mv ~/.config/lxpanel/Lubuntu/panels/**panel** ~/
``````
lxpanelctl restart
```

Enjoy Xubuntu :)

---

### Post by lazylew on 2010-10-15
> **SteveDee said:**
> The user keyring is held in:
```

 $Home/.gnome2/keyrings/default.keyring

```Deleting this file forces a request for fresh network keyphrase next time system starts. If you then use a blank password, it will stop asking you for a password.
I don't see "default.keyring" but "login.keyring" and "user.keystore". Opening it with cat shows gibberish code.
Anyway, since I changed to Xubuntu earlier today, I think the problem is gone anyhow.
Thanks :-)

---

### Post by lazylew on 2010-10-15
> **cavalier911 said:**
> ...To fix the browser icon:
Move the old panel file out in case you want to reference it for your custom configs.
```
mv ~/.config/lxpanel/Lubuntu/panels/**panel** ~/
``````
lxpanelctl restart
```Enjoy Xubuntu :)
Thanks cavalier911. The network settings were already like that.
The Lubuntu folder is completely empty, no panel(s), but never mind, I'll probably stick to the Xubuntu I have now :-)

Some other strange behavior though; I copied the code from [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce) to remove Ubuntu and Lubuntu (leaving off the end part ```
&& sudo apt-get install xubuntu-desktop
``` the second time).
It seems "purified" enough, but when I choose Ubuntu at boot, it takes me to the automatic login screen of Lubuntu :shock: (still, there is Thunar and such, so it seems to be Xubuntu rather than Lubuntu).
Then I logout to choose Xubuntu for login, which is, you guessed it, not automatic but requires name and passwd. So somehow I have to get the login to recognize that Xubuntu is my default. 

Off topic, but also strange, is that when I pick Openbox session from the menu "other", I have two separate monitors like I want. When I stay in regular Xubuntu though, I see everything twice (once per monitor, of course ;-))
and... (almost done ;-)) the file manager doesn't see my two hard disks where I have my data. Ubuntu and Lubuntu, when they were in charge, did see these though :confused: (EDIT: I could even see my Home from Crunchbang, the other OS I dual boot with) [COLOR=Red]2nd EDIT[/COLOR]: I stumbled on Gigolo and found out I could properly mount the HD's :-)

[COLOR=Red]3rd EDIT:[/COLOR] Somehow I messed things up by choosing the drivers for NVidia
Now there's only one monitor working - time to start from scratch I think, and reinstall from CD.

---

