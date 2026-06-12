---
title: "Changing default desktop back to Gnome"
date: 2011-06-07
forum: General Help
---

### Post by RunForIt222 on 2011-06-07
Today I installed Xubuntu desktop on my normal Ubuntu, to see what it's like, and to have the option to run a more minimal desktop when I want.

My only problem is that my login screen loads with the Xubuntu theme. This wouldn't be a problem except it makes it take significantly longer to boot into Ubuntu (Gnome). 

How can I change it back so that Gnome is the default, and XFCE only gets loaded if I pick it at login?

Also, what are my options with customizing Gnome at the login screen?

Thanks for any help.
~Jake

---

### Post by dwhite on 2011-06-08
> **RunForIt222 said:**
> Today I installed Xubuntu desktop on my normal Ubuntu, to see what it's like, and to have the option to run a more minimal desktop when I want.

My only problem is that my login screen loads with the Xubuntu theme. This wouldn't be a problem except it makes it take significantly longer to boot into Ubuntu (Gnome). 

How can I change it back so that Gnome is the default, and XFCE only gets loaded if I pick it at login?

Also, what are my options with customizing Gnome at the login screen?

Thanks for any help.
~Jake


have you tried selecting Gnome at the login screen? after selecting your login name and before putting in your password, along the bottom edge of the screen you may be able to select a menu giving various options, i suspect (but may be wrong since i have never done this myself...installing XFCE on normal ubuntu, though i'd like to try) you can choose between xfce, ubuntu, ubuntu safe mode, etc.

alternatively you can change what system you start in using the "Login Screen" app in system settings

---

### Post by yetiman64 on 2011-06-08
> **RunForIt222 said:**
> Today I installed Xubuntu desktop on my normal Ubuntu, to see what it's like, and to have the option to run a more minimal desktop when I want.

My only problem is that my login screen **loads with the Xubuntu theme**. This wouldn't be a problem except it makes it take significantly longer to boot into Ubuntu (Gnome). 

How can I change it back so that Gnome is the default, and XFCE only gets loaded if I pick it at login?

Also, what are my options with customizing Gnome at the login screen?

Thanks for any help.
~Jake

The bolded text indicates to me you no longer have a "purple" plymouth splash screen but the xubuntu background (a blue coloured background IIRC). To change this run the following code in a terminal,
```
sudo update-alternatives --config default.plymouth
```You will get a numbered list of the possible alternatives, input the number for Ubuntu in the terminal and press enter. This gives you back the purple theme of Ubuntu.

Next put in the terminal (this sets the change in place)
```
sudo update-initramfs -u -k all
```On your next boot of the system you should have the standard theme back and can still select which desktop you want to boot into at the login screen.

---

