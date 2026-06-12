---
title: "Customizing the Karmic Login Screen?"
date: 2009-12-08
forum: General Help
---

### Post by Unanimated on 2009-12-08
I noticed that in Karmic, 'Login Screen' in the settings only gives you options for automatic login now. Previously, you could set that setting along with a theme and a bunch of other stuff. What happened to that screen? I mainly want to know because I liked applying custom login screens, and I accidentally clicked 'increase contrast between colors' on the login screen's accessibility options, and then turned it off, and now it's not the dark color that I liked.

But anyway, what happened to the original gdmsetup screen?

---

### Post by Unanimated on 2010-02-07
bump

---

### Post by Mr Nemo on 2010-02-07
I did the same thing with the login screen. Bump for answer.

---

### Post by thecliff on 2010-02-07
Stick with me here.  I found this online yesterday and it worked, but I cannot find the article now.  I am going through the CLI history to provide the necessary commands.  

Go to terminal and enter

```
export DISPLAY=:o.o

```Enter:

```
sudo -u gdm gnome-control-center

```Add this repository:

```
sudo add-apt-repository ppa:gdm2setup/gdm2setup

```Enter:

```
sudo apt-get update

```Install the app by entering:

```
sudo apt-get install python-gdm2setup

```Go to System > Administration > Log On Screen (GDM2Setup)

:P

Enjoy

---

### Post by Madmoose on 2010-02-08
Hey, 

This added the new menu, but it didn't actually change anything. Any of the options I choose don't seem to do anything to the login screen.

---

