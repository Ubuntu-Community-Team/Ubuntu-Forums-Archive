---
title: "customise my  login screen"
date: 2010-12-12
forum: General Help
---

### Post by kindmoji on 2010-12-12
Hello,

I'm a new user of ubuntu and i love it, now i wanted to change my login screen but i tried a lot of tricks and methods that there is in various forums , i couldn't make it , Please guide me. I'd appreciate your attention.

I use Ubuntu 10.10

To tell you the truth I use Ubuntu Tweak but there isn't anything about login screen in this useful application!

Best wishes

---

### Post by argedion on 2010-12-12
not sure how you want to customise you login screen if you just want to change the background there are a few things you can do.

1.Run the following in terminal,

Add the repository,
```
sudo add-apt-repository ppa:tualatrix/ppa
```

Update your repository,
```
sudo apt-get update
```

Install ubuntu-tweak
```
sudo apt-get install ubuntu-tweak
```

alternatively you can run this at the terminal
```
sudo -u gdm dbus-launch gnome-appearance-properties
```

These will allow you to change the login screen background image. If you want to change more than that I'm not sure exactly how to go about other things yet.

---

### Post by kindmoji on 2010-12-12
Dear argedion ,

I use your code , but this error appeared "

No protocol specified
No protocol specified
Cannot open display: 
mojtaba@mojtaba-desktop:~$ No protocol specified

(gnome-appearance-properties:4147): Gtk-WARNING **: cannot open display: :0.0 "

now what can I do for making this ?!

---

### Post by tajiknomi on 2010-12-12
> **kindmoji said:**
> Hello,

I'm a new user of ubuntu and i love it, now i wanted to change my login screen but i tried a lot of tricks and methods that there is in various forums , i couldn't make it , Please guide me. I'd appreciate your attention.

I use Ubuntu 10.10

To tell you the truth I use Ubuntu Tweak but there isn't anything about login screen in this useful application!

Best wishes

[SIZE=2]First open a Terminal window (Applications -> Accessories -> Terminal) then copy+paste the following line:

[/SIZE]```
[SIZE=3]sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow[/SIZE]
```[SIZE=2]Now close the Terminal window and logout, when logged out the Appearance window pops up. Here you can make the changes you want and when your done you can login as usual. To prevent the Appearance Manager from opening when you login, open a Terminal window (Applications -> Accessories -> Terminal) then copy+paste the following line:

[/SIZE]```
[SIZE=3]sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop[/SIZE]
```Good luck:p

---

### Post by argedion on 2010-12-12
> **kindmoji said:**
> Dear argedion ,

I use your code , but this error appeared "

No protocol specified
No protocol specified
Cannot open display: 
mojtaba@mojtaba-desktop:~$ No protocol specified

(gnome-appearance-properties:4147): Gtk-WARNING **: cannot open display: :0.0 "

now what can I do for making this ?!

which code gave you trouble? Downloading ubuntu tweak or opening the apperance dialog box as the root user? 
also did you copy and paste? or did you type the command? its probably best to copy and paste. 

tajiknomi that is a good one i added it to my collection :)

---

### Post by kindmoji on 2010-12-13
Dear tajiknomi,

I am really confused , i copy past your code in to console and log out and then log in but nothing happened!!

bye the way i don't have any apperance dialog box in my ubuntu tweak program.

---

### Post by tajiknomi on 2010-12-13
> **kindmoji said:**
> Dear tajiknomi,

I am really confused , i copy past your code in to console and log out and then log in but nothing happened!!

bye the way i don't have any apperance dialog box in my ubuntu tweak program.

[SIZE=2]Try once again, copy the first code and put it in terminal,once you press enter, it will ask for a password, 

Then you have to log-out, once you are log-out, ***Appearance-menu*** will ***appear***, and you can select your Desire Background their....
[/SIZE]

---

### Post by Frogs Hair on 2010-12-13
If you have Ubuntu Tweak installed , open it and select login settings . Unlock the screen using your password  and select the background  image , then migrate to the directory where the desired image is stored and open . This will allow you to change the background image but not the greeter.

---

### Post by tajiknomi on 2010-12-13
> **Frogs Hair said:**
> If you have Ubuntu Tweak installed , open it and select login settings . Unlock the screen using your password  and select the background  image , then migrate to the directory where the desired image is stored and open . This will allow you to change the background image but not the greeter.

[SIZE=2]+1 for that, because its an easy way [/SIZE]:p

---

### Post by kindmoji on 2010-12-13
this is my "Ubuntu Tweak" screen, you see ther is no login screen option !!!!

---

### Post by tajiknomi on 2010-12-14
> **kindmoji said:**
> this is my "Ubuntu Tweak" screen, you see ther is no login screen option !!!!

[SIZE=2]Which version of Ubuntu are you using...?[/SIZE]

[SIZE=2]If you are using Lucid,maverick,[/SIZE][COLOR=#666666] [SIZE=2][COLOR=Black]Hardy, Intrepid, Jaunty and Karmic,

Then Download this One > [/COLOR][/SIZE][/COLOR][http://dl.dropbox.com/u/16158781/ubuntu-tweak_0.5.7-1_all.deb](http://dl.dropbox.com/u/16158781/ubuntu-tweak_0.5.7-1_all.deb)

[SIZE=2]Its has that option[/SIZE]...[SIZE=2]I think you are using Old version of ubuntu-tweak ,thats y..[/SIZE].

---

### Post by brianw0667 on 2010-12-14
Ubuntu Tweak still does not allow the theme to be changed for the GDM login screen just the logo and the background.  

This really sucks that the customization is being taken away from users and we only have one choice.  Might as well just have a text login if you can't customize it the way you want.

---

