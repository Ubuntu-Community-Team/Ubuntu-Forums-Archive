---
title: "How to get the gnome-colors login screen"
date: 2010-01-20
forum: General Help
---

### Post by jeremy1138 on 2010-01-20
So, I was looking around on google when I stumbled on a website that showed some screen shots of the gnome-colors theme.

[http://www.webupd8.org/2009/07/gnome-colors-customization-of-themes.html](http://www.webupd8.org/2009/07/gnome-colors-customization-of-themes.html)

I installed gnome-colors, shiki-colors and arc-colors and I'm able to set the new desktop themes and wallpapers just fine but I don't understand how to apply the login screen themes shown on the above referenced page.  The directions say to go to System –> Administration –> Login Window but the closest thing I have under System –> Administration is Login Screen which does not include an option to change the theme.  Do I need to install something else to get this working?  Thanks!

---

### Post by tad1073 on 2010-01-20
this link might help
[http://ubuntuforums.org/showthread.php?t=1333683](http://ubuntuforums.org/showthread.php?t=1333683)

---

### Post by Revolutionary101 on 2010-01-20
The instructions are intended for Ubuntu 9.04, that is why you can't change the login theme the way they instruct you to do.

---

### Post by jeremy1138 on 2010-01-20
> **tad1073 said:**
> this link might help
[http://ubuntuforums.org/showthread.php?t=1333683](http://ubuntuforums.org/showthread.php?t=1333683)

That seems really hacky...  Is there a way to change the login screen theme via a normal ui accessible from the system menu that shows available themes and allows you to choose one?  I believe that we used to have that at one time right?

---

### Post by jeremy1138 on 2010-01-20
> **Revolutionary101 said:**
> The instructions are intended for Ubuntu 9.04, that is why you can't change the login theme the way they instruct you to do.

I understand that.  The reason for my post is to try to find the *proper* way to do this in the current version of Ubuntu...

---

### Post by Jackzor on 2010-01-20
As far as I know you can not yet change the login screen very well.. The way that I have found to make some changes would be to log out and open tty1-6 either one and login.

Then type 

```
export DISPLAY=:0.0

sudo -u gdm gnome-control-center

```

Then hit Alt-f7 to go back to the GUI login.

---

### Post by tad1073 on 2010-01-20
> **Revolutionary101 said:**
> The instructions are intended for Ubuntu 9.04, that is why you can't change the login theme the way they instruct you to do.

I am on 10.04 alpha 2 and used that tutorial to customize GDM . What it does is applies the theme you choose from Appearance Preferences>Theme tab to GDM.

---

### Post by tad1073 on 2010-01-20
> **jeremy1138 said:**
> That seems really hacky...  Is there a way to change the login screen theme via a normal ui accessible from the system menu that shows available themes and allows you to choose one?  I believe that we used to have that at one time right?

There is no ui to change gdm as of now.

---

### Post by jeremy1138 on 2010-01-20
> **tad1073 said:**
> There is no ui to change gdm as of now.

Well that's disappointing...  Oh well, I guess I will deal with it the way it is.  The login screen really isn't that important to me to customize anyway.  Thanks for the responses folks.

---

### Post by qwerty2009 on 2010-01-20
its easy in karmic - press alt + f2 to get the run box up and paste this command "gksudo -u gdm dbus-launch gnome-appearance-properties" without quotes

---

