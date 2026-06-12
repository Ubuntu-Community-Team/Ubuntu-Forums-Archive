---
title: "Disable login screen on return from suspend / hibernate"
date: 2010-01-08
forum: General Help
---

### Post by SamBam77 on 2010-01-08
I would like to disable the login screen when the computer returns from suspension and hibernation, so that it will automatically log me back in.  I am using Ubuntu 9.10.
 

 When I come back from suspension, for some reason, my key board does not work in the login screen and I cannot type my password.

---

### Post by mgmiller on 2010-01-08
Applications > Accessories > Passwords and Encryption Keys
You will find your log in password, just click to change it and after entering your existing password, make the new one blank.  It will warn you about using a new unsecure login, just tell it yes.  I have my notebook setup this way along with auto log in in System > Administration > Log in Screen.  I know it's not a secure, but it sure is convenient.

Edit:

I just discovered that this has stopped working on my laptop.  I don't know why, it works fine on my desktop machine as well as on anther desktop I set up for a friends father.

hmmmm....

---

### Post by SamBam77 on 2010-01-08
Thanks for your reply, however this solution was unsuccessful for me.  I am still prompted for a password at the login screen.

---

### Post by Ginsu543 on 2010-01-08
Go to Application --> System Tools --> Configuration Editor. Under apps --> gnome-power-manager --> lock, you will see check marks beside "hibernate" and "suspend." Simply uncheck them and you will be able to come back from hibernation and suspension, respectively, without having to log back in.

---

### Post by SamBam77 on 2010-01-09
> **Ginsu543 said:**
> Go to Application --> System Tools --> Configuration Editor. Under apps --> gnome-power-manager --> lock, you will see check marks beside "hibernate" and "suspend." Simply uncheck them and you will be able to come back from hibernation and suspension, respectively, without having to log back in.
I have already tried this method and unchecked those boxes, but it still prompts me to log back in when I return from suspension / hibernation.

---

### Post by nathan726 on 2010-06-04
Open gconf-editor and enable /desktop/gnome/lockdown/disable_lock_screen

---

### Post by roscopico on 2010-06-19
This is the correct answer, which I've been looking for for about a week.

Thanks!:guitar:

---

### Post by nathan726 on 2010-06-20
I don't know if this effects anyone else, but I noticed that disabling lock screen caused my screen to flash off and on before it hibernates.
So to make hibernation a bit more graceful I wrote the following script...
```
#!/bin/sh

case "${1}" in
        hibernate)
             xset -display :0.0 dpms force standby
                ;;
        thaw)
        xset -display :0.0 dpms force on
                ;;
esac

```Save the script as  /etc/pm/sleep.d/10_suspend_screen
and make the file executable with "sudo chmod +x /etc/pm/sleep.d/10_suspend_screen"

---

### Post by Piper64 on 2010-12-19
Quite brilliant nathan726. Many thanks. I have recently started using my Acer One zg5 netbook as an ereader and this tweak will add to the experience.
Happiness is: eventually solving a ubuntu problem with the help of others.
By the way, the last word in the executing command should be screen not monitor. It worked as you said.

---

### Post by nigel23 on 2011-01-24
how do you save a script?

---

### Post by nathan726 on 2011-01-31
> **nigel23 said:**
> how do you save a script?

Press Alt+F2 and type in "gsku gedit" (without quotes) and enter your password when required

Then copy and paste the above code to the text editor window

Go to File -> Save As and then in the "name" box type: /etc/pm/sleep.d/10_suspend_screen

Click save

Then to make the script work you have to open a terminal (Applications > Accessories > Terminal) and type in:
sudo chmod +x /etc/pm/sleep.d/10_suspend_screen

---

### Post by earlf on 2011-02-02
Thanks [nathan726]("http://ubuntuforums.org/member.php?u=849234"). I edited the gconf and it worked. I didn't notice too much flickering though. (I'm on 10.10).

---

