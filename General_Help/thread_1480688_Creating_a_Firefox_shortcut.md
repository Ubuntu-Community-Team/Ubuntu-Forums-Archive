---
title: "Creating a Firefox shortcut"
date: 2010-05-11
forum: General Help
---

### Post by rmcellig on 2010-05-11
I am using Xubuntu 10.04.

I access my mail through [www.gmail.com](www.gmail.com). I would like to add a shortcut to this site to my Panel so that I can quickly access the site. Is this possible?

---

### Post by kerry_s on 2010-05-11
yes, you can go several ways for that.

command = **exo-open [https://mail.google.com/mail/](https://mail.google.com/mail/)**
you can also use "gnome-open" or "xdg-open" instead of "exo-open", what it does is use your default browser, so if you set another prefered browser you don't have to worry about changing it.
or
you can install desktop-webmail & set that as the command, which is what i use in xfce4-mailwatch-plugin & it can be run on email links from your browser.

---

### Post by rmcellig on 2010-05-11
Let me try out the options you mention and I will post back. Thanks!!

---

### Post by rmcellig on 2010-05-12
[QUOTE=kerry_s;9283698]yes, you can go several ways for that.

command = **exo-open [https://mail.google.com/mail/](https://mail.google.com/mail/)**
you can also use "gnome-open" or "xdg-open" instead of "exo-open", what it does is use your default browser, so if you set another prefered browser you don't have to worry about changing it.

Because I am so new to Linux (I'm basically a Mac user), can you explain to me how exactly I can implement what you mentioned above?

I would really appreciate this!! :)

---

### Post by kerry_s on 2010-05-12
> **rmcellig said:**
> [QUOTE=kerry_s;9283698]yes, you can go several ways for that.

command = **exo-open [https://mail.google.com/mail/](https://mail.google.com/mail/)**
you can also use "gnome-open" or "xdg-open" instead of "exo-open", what it does is use your default browser, so if you set another prefered browser you don't have to worry about changing it.

Because I am so new to Linux (I'm basically a Mac user), can you explain to me how exactly I can implement what you mentioned above?

I would really appreciate this!! :)

so you want to create a icon launcher. :)
right click the panel-> add new items
left click hold on "Launcher" & drag drop where you want it on the panel
right click the launcher you just put & select "properties"

going down the line,

name: what ever you want, for example: Open Gmail

description: again what ever you want or just leave empty

you can click on the icon to select 1, click on the bar at the top & select "appliction icons" theres a gmail icon in there.

command: exo-open [https://mail.google.com/mail/](https://mail.google.com/mail/)

then just give it a try.

---

### Post by rmcellig on 2010-05-12
This is really fun learning this new OS. Not as slick as Mac OS X but I think it is way more flexible than Windows?

I am going to try that out!! Thanks again!!

I just installed Compiz but don't know how to bring up the Compiz manager so I can try out some of the cool things in Compiz. In Ubuntu, I knew where to go but in Xubuntu, I'm not sure. I installed the Compiz Fusion Icon as well as Compiz.

---

### Post by azertyh on 2010-05-12
hi,
simply create a launcher and make google as your default site for firefox.

---

