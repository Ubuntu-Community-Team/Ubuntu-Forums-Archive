---
title: "Openbox, Gnome &amp; KDE"
date: 2006-05-18
forum: General Help
---

### Post by larry on 2006-05-18
Hi,
As you can see I am running Ubuntu Dapper on my laptop.
I recently, just for fun, installed Openbox and Pypanel, just to find out how it feels to work with a minimalistic set-up.
I now seldom log into Gnome.
I wonder: is there a way to start Ubuntu with such a light environment and then add your own applications? I notice that most of my recent updated packages deal with some Gnome utilities I am no longer using (though I am sure that I do not know enough to simply start disinstalling stuff without making a mess...).
I also would like to know, without starting a flamewar, if there is a reason to choose KDE rather than Gnome applications having the goal of using them under Openbox.
I ask so since I keep hearing about how fast and stable Kubuntu is, though personally I prefer to keep things as simple as possible.
Cheers

Larry

---

### Post by barbarian on 2006-05-18
hi,
Xubuntu is a light version of ubuntu distro, besides you could use gtk and qt apps together under xfce without probs..

check this:

[http://www.xubuntu.org/](http://www.xubuntu.org/)

---

### Post by larry on 2006-05-19
[QUOTE=barbarian]hi,
Xubuntu is a light version of ubuntu distro, besides you could use gtk and qt apps together under xfce without probs..

check this:

[http://www.xubuntu.org/](http://www.xubuntu.org/)[/QUOTE]

This may do and I'll give it a try...but I still look for solutions based on using Openbox, which I think should be evan lighter.
Thanks for your help

Larry

---

### Post by barbarian on 2006-05-19
also ubuntulite would be interesting..

[https://wiki.ubuntu.com/InstallingUbuntuLite](https://wiki.ubuntu.com/InstallingUbuntuLite)

---

### Post by 3rdalbum on 2006-05-19
You could also try WindowMaker, which is more configurable than OpenBox but probably as lightweight. It's also more of a desktop environment than OpenBox.

/me is big OB fan.

---

### Post by larry on 2006-05-20
[QUOTE=barbarian]also ubuntulite would be interesting..

[https://wiki.ubuntu.com/InstallingUbuntuLite](https://wiki.ubuntu.com/InstallingUbuntuLite)[/QUOTE]

This sounds interesting again, but I wonder: can I simply start with a server installation, install directly some very light e.g. Openbox+Pypanel combination to use as a desktop/window manager and only then select the Gnome/KDE apps I really want?
Do you think this is feasible?
Cheers

Larry

---

### Post by Ramses de Norre on 2006-05-20
That's certainly possible. You'll need to install at least X and your window manager of choice.
I'm planning to do the same when I've got the time for it with fluxbox instead of openbox.

---

### Post by larry on 2006-05-21
[QUOTE=Ramses de Norre]That's certainly possible. You'll need to install at least X and your window manager of choice.
I'm planning to do the same when I've got the time for it with fluxbox instead of openbox.[/QUOTE]

Alright. I will probably pop up with more questions when I try this; I am not an expert but I like to play with my pc to learn a few things. 
Cheers

Larry

---

### Post by fuscia on 2006-05-24
if you go into synaptic, when you select something to be uninstalled, it will mention those programs that depend on the one you're uninstalling. you can strip away a lot of stuff. when you add a program, either through apt or synaptic, the dependencies will also be installed and you'll know what they are. you can use all sorts of things in openbox.

you might want to check out obmenu - [http://obmenu.sourceforge.net/index.html](http://obmenu.sourceforge.net/index.html) 
it's a menu editor for openbox that is very easy to use. the installation was a little tricky though, but doable for perma-noobs like me.

---

### Post by larry on 2006-05-25
[QUOTE=fuscia]if you go into synaptic, when you select something to be uninstalled, it will mention those programs that depend on the one you're uninstalling. you can strip away a lot of stuff. when you add a program, either through apt or synaptic, the dependencies will also be installed and you'll know what they are. you can use all sorts of things in openbox.

you might want to check out obmenu - [http://obmenu.sourceforge.net/index.html](http://obmenu.sourceforge.net/index.html) 
it's a menu editor for openbox that is very easy to use. the installation was a little tricky though, but doable for perma-noobs like me.[/QUOTE]

Thanks for the Openbox suggestion, which allows to edit quickly the menu. I find it very handy.
As to Synaptic, what you say is true, but sometimes I really fear to break my system by disinstalling something important without realizing at once.
Now a trivial question: what is the command to lock the computer? and can I introduce in the Openbox menu commands requiring sudo? I tried creating an entry like "sudo synaptic", but then Synaptic would not start!
Cheers

Larry

---

### Post by Ramses de Norre on 2006-05-25
{gksudo synaptic} works for me :)

---

### Post by Caligula on 2006-05-25
> I tried creating an entry like "sudo synaptic", but then Synaptic would not start!

you need "gksu synaptics" or "gksudo", I can't remmember, but one of them...

edit: oops... too slow typing...

---

### Post by larry on 2006-05-27
[QUOTE=Ramses de Norre]That's certainly possible. You'll need to install at least X and your window manager of choice.
I'm planning to do the same when I've got the time for it with fluxbox instead of openbox.[/QUOTE]


Hi,
I tried doing what we discussed.
 I went for a server installation having then the idea of setting up a simple desktop with openbox and a few selected apps.
Well, the server installation is fine, but now I am finding out that I have no idea of how to set up some graphical environment and what I should install to see something resembling a desktop (let alone installing Gnome/KDE) and so on.
Before now, I was running Ubuntu Dapper and Openbox as an alternative to Gnome.
Any suggestions about what to do? Is there a tutorial with some quick rules to follow?
I would like to get to the bottom of this and I cannot leave my laptop as it is (with little more than the command line) for a long time.
Cheers

Larry

---

### Post by fuscia on 2006-05-27
*sudo apt-get install x-window-system-core openbox obconf*

edit your .xinitrc file by doing...

 *sudo nano .xinitrc* 

then enter 'exec openbox' (no quotes) in the body of the text. save it by doing ctrl+x, yes (y) to the changes, hit enter to save in .xinitrc. 

then enter *startx* and you'll be in openbox.

---

### Post by larry on 2006-05-28
[QUOTE=fuscia]*sudo apt-get install x-window-system-core openbox obconf*

edit your .xinitrc file by doing...

 *sudo nano .xinitrc* 

then enter 'exec openbox' (no quotes) in the body of the text. save it by doing ctrl+x, yes (y) to the changes, hit enter to save in .xinitrc. 

then enter *startx* and you'll be in openbox.[/QUOTE]

Thanks. Now I have openbox up and running. The only trouble is that it does not recognize my usb key.
I enabled
gnome-volume-manager

in my ~.xsession file, but it is not enough.
Any idea? I simply would like my usb key to be automounted as it used to be before.

Cheers

Larry

---

