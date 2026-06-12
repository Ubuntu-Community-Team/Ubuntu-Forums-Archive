---
title: "remove compiz completely"
date: 2010-03-18
forum: General Help
---

### Post by anantshri on 2010-03-18
Hi,

I am looking for an option to completely remove compiz.

I fired up synaptic and removed compiz completely.

Now i have just one problem.

Metacity is not fired up by default.

so i have desktop and winows also open but without borders. i.e without any desktop manager.

I know a workaround, i.e. to add metacity --replace in startup applications.
but this is work around and not the actuall work.


my system Ubuntu 9.10 x64

---

### Post by _h_ on 2010-03-18
In terminal:

metacity --replace

---

### Post by anantshri on 2010-03-18
that's exactly what i don't want to do.

I want a permanent solution.

I mean some package by which this removing compiz and autoreplacement of it with metacity takes place flawlessly.

or is it some file which is causing this problem.

---

### Post by shafin on 2010-03-18
run gconf-editor
in Desktop>gnome>windoow_manager set /usr/bin/metacity as default window manager.

---

### Post by Post Monkeh on 2010-03-18
gconf-editor

desktop-gnome-session-required components

change the window manager in there to whatever you like

---

### Post by anantshri on 2010-03-18
thanks for the quick reply 

just checking by rebooting the system.

---

### Post by Psumi on 2010-03-18
sudo apt-get purge compiz-core

it'll remove everything related to compiz.

---

### Post by cariboo on 2010-03-18
This is not a Cafe question, moved to General Help.

---

### Post by anantshri on 2010-03-18
compiz is removed completely.

gconf-editor value changed but this doesn't help.

my system boots with no desktop manager and when i type in metacity --replace in console then only i get the windows borders

---

### Post by Psumi on 2010-03-18
> **anantshri said:**
> compiz is removed completely.

gconf-editor value changed but this doesn't help.

my system boots with no desktop manager and when i type in metacity --replace in console then only i get the windows borders

Never change anything in gconf if you don't know what will happen.

---

### Post by anantshri on 2010-03-18
well this one i knew because i tried once before too.

so back to my old question why is my windows manager not yet shifted to metacity when compiz is removed / purged completely.

---

### Post by Psumi on 2010-03-18
> **anantshri said:**
> well this one i knew because i tried once before too.

so back to my old question why is my windows manager not yet shifted to metacity when compiz is removed / purged completely.

Wouldn't know because when I removed compiz in the way I mentioned, metacity was the default manager when I rebooted/logged out/in/etc.

---

### Post by anantshri on 2010-03-18
thanks for the response i will currently move back to adding an entry in startup to metacity --replace.

---

### Post by 5735guy on 2010-03-20
purge compiz-fusion
[http://ubuntuforums.org/showthread.php?t=546429](http://ubuntuforums.org/showthread.php?t=546429)

---

### Post by anantshri on 2010-03-20
that's already done

---

### Post by gwu777 on 2010-04-06
> **anantshri said:**
> thanks for the response i will currently move back to adding an entry in startup to metacity --replace.

I have exactly yhe same problem, I have checked all the above - metacity is the defauolt windows  manager and yet I have to run metacity --replace before anything... I am not really happy with that, I would like to understand, why my instalation bugged.

For my case, i have done a sudo apt-get autoremove before having the problem, I am pretty sure, too manythings have been removed, I would like to know what and reinstall it.

Any ideas would be welcome...

---

### Post by Psumi on 2010-04-06
sudo dpkg-reconfigure metacity?

---

### Post by gwu777 on 2010-04-06
> **Psumi said:**
> sudo dpkg-reconfigure metacity?

nop...

---

### Post by Psumi on 2010-04-06
> **gwu777 said:**
> nop...

sudo apt-get purge metacity

sudo apt-get install metacity

See if there is a file for metacity in your /etc/X11/Xsession.d directory.

Also, DO NOT do any of the commands I have said to do FROM THE RUN DIALOG BOX. You MUST do them from the terminal.

---

