---
title: "Startup"
date: 2010-12-02
forum: General Help
---

### Post by shashanksingh on 2010-12-02
Suppose I want the terminal to start automatically.
Where do I write those scripts??? (/init.d ??)

I could then write just one script for all the startup applications I need....

---

### Post by karthick87 on 2010-12-02
Goto **System>>Preferences>>Startup Applications **

[IMG]http://imgur.com/viRKu.png[/IMG]

Click **Add **and write **Terminal** in the name field and in command write **gnome-terminal**

---

### Post by shashanksingh on 2010-12-02
Thank you..
Any command line way for it???

I mean writing your own scripts...
Wanted to learn that.

Anybody knows where does ubuntu load its exectables to run on startup????

---

### Post by Mosabama on 2010-12-02
If you want to run some command when you login, add that command to the file .bash_profile.
it doesn't exist by default in Ubuntu 10.10, so if its not there just create it and add the commands you want.

edit: this file has to be in your home directory.

---

### Post by Mosabama on 2010-12-02
or you can add what ever you want at the end of .profile file in your home directory.

remember to add & at the end of the command so your command will run in the background. other wise the program will open and the system will wait for you until you close it then will continue loading other things.

for example if you want to start skype when ubuntu desktop loads add the following to .profile:

```
skype &
```

---

### Post by sisco311 on 2010-12-02
> **shashanksingh said:**
> Thank you..
Any command line way for it???

I mean writing your own scripts...
Wanted to learn that.

Anybody knows where does ubuntu load its exectables to run on startup????

See: 
[http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html](http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html)
and
[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)

The system wide autostart directory is /etc/xdg/autostart and the autostart directory in the user's home directory is ~/.config/autostart/.

By placing an application's .desktop file in one of the Autostart directories the application will be automatically launched during startup of the user's desktop environment after the user has logged in.

---

### Post by shashanksingh on 2010-12-03
> **sisco311 said:**
> See: 
[http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html](http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html)
and
[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html)

The system wide autostart directory is /etc/xdg/autostart and the autostart directory in the user's home directory is ~/.config/autostart/.

By placing an application's .desktop file in one of the Autostart directories the application will be automatically launched during startup of the user's desktop environment after the user has logged in.

Thanks a lot
Precise

---

