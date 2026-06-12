---
title: "Different DE login problem?"
date: 2011-11-03
forum: General Help
---

### Post by lianazaman on 2011-11-03
Hey,

I'm using Lubuntu 11.10. I noticed there's a dropdown choices of DE. Funnily, when I picked one besides default, then try to login, it comes back to the login screen. 

So far I can login to LXDE, Lubuntu, and Gnome classic (no effects). But in that options I have also Ubuntu, Ubuntu 2D, Gnome, Gnome classic. How did I have those without even installing? O.o

Since it's there, should I:
a) install the DEs
b) Find a way to remove them from the dropdown menu ( l long list is useless if we can't login into it right?)

---

### Post by amjjawad on 2011-11-04
> **lianazaman said:**
> Since it's there, should I:
a) install the DEs
b) Find a way to remove them from the dropdown menu ( l long list is useless if we can't login into it right?)

Hi again,

You don't have to install anything, it's there by default and if the user decides to install a particular DE then it's on the list.

Also, no need to remove them, just keep everything as it's and don't use it :)
It won't make any difference if you keep it or remove it but IMHO, better to keep it as long as it's not harmful :)

Someone had a problem with starting other DE's: [http://ubuntuforums.org/showthread.php?t=1871456](http://ubuntuforums.org/showthread.php?t=1871456)

Not sure if my steps will work for him/her or not? still waiting for a reply but just in case you'll be in the same situation :P

---

### Post by lianazaman on 2011-11-04
Hm...check the /usr folder. since I'm using lubuntu, I don't think I'm searching for xsession. So, hm...until I further understand it, I'll leave it as it is.

Well,  I thought it would conflicts between DEs, or hogs space, but if it's not, I'll leave them.  

Okay, I'll look more into the posts then. Just to make sure it isn't a big problem :)


p/s: I know this is unrelated, but...

I want to set my keyboard switcher with us and arabic. Found some methods, but it's not permanent. Everytime I reboot, I need to re-adjust. Any way or settings should I do to make it permanent?

---

### Post by amjjawad on 2011-11-04
> **lianazaman said:**
> Hm...check the /usr folder. since I'm using lubuntu, I don't think I'm searching for xsession. So, hm...until I further understand it, I'll leave it as it is.

Well,  I thought it would conflicts between DEs, or hogs space, but if it's not, I'll leave them.  

Okay, I'll look more into the posts then. Just to make sure it isn't a big problem :)

Nothing to worry about, just keep everything as it's. If you face any problems in the future, the forum is here and hope I'll be here too ;)


> I want to set my keyboard switcher with us and arabic. Found some methods, but it's not permanent. Everytime I reboot, I need to re-adjust. Any way or settings should I do to make it permanent?

I have received this through our mailing list by one of the developers:

> as I got a lot of requests to implement an autostart feature for
lxkeymap I did it.
LXKeymap 0.5 is now capable to store its keymap configuration into a
file that it reads out during autostart.
Therefore I wrote a little *.desktop file that I put in the global
/etc/xdg/autostart which contains the new command "lxkeymap -a" to
trigger the autostart function of lxkeymap. The Keymap configuration
will be stored locally in your home directory ( ~/.config/lxkeymap.cfg)
and is easily editable either by using lxkeymap and set a new keymap or
by editing it by hand.
You can get this version from here:
[http://content.wuala.com/contents/leszek/Dokumente/Share/lxkeymap_0.5-0ubuntu1_all.deb?dl=1](http://content.wuala.com/contents/leszek/Dokumente/Share/lxkeymap_0.5-0ubuntu1_all.deb?dl=1)

If you notice any bugs then report them here: [http://launchpad.net/lxkeymap](http://launchpad.net/lxkeymap)

Also I guess there is a bug in lxdm, because changing the keyboard
layout in the session and logging out to lxdm does not restore the
global keymap but uses the one choosen in the session.
This could be also fixed by simply calling "lxkeymap -a" from within
lxdm but as lxkeymap uses only a local configuration it would then
create and use the root accounts .config/lxkeymap.cfg file. So you need
to create this first by executing lxkeymap as root if you want to have a
different keymap globally+lxdm and your user accounts.


Hope that will help!

---

