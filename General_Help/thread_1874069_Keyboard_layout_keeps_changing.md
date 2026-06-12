---
title: "Keyboard layout keeps changing"
date: 2011-11-02
forum: General Help
---

### Post by Adarzh on 2011-11-02
Hi,

I'm using Lubuntu 11.10. My Keyboard layout keeps changing after every reboot.Its always resetting to Senegal but i want is United States. Any idea on how to fix it.

Thanks
Adarsh

---

### Post by Adarzh on 2011-11-02
Any idea ?.

---

### Post by amjjawad on 2011-11-03
> **Adarzh said:**
> Hi,

I'm using Lubuntu 11.10. My Keyboard layout keeps changing after every reboot.Its always resetting to Senegal but i want is United States. Any idea on how to fix it.

Thanks
Adarsh

Hi,

I just got this email from one of the Lubuntu Team via Mailing List 19 hours ago:

> Hi,

as I got a lot of requests to implement an autostart feature for
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


Let me know if you need anything else :)

---

### Post by Adarzh on 2011-11-04
amjjawad,

I tried it but it isn't working even though all the new files and configuration is in place as in the document

---

### Post by amjjawad on 2011-11-04
> **Adarzh said:**
> amjjawad,

I tried it but it isn't working even though all the new files and configuration is in place as in the document

Ok, any error message?

---

### Post by Adarzh on 2011-11-05
amjjawad,

Actually it worked but only after you logged in to the system. In the login page, it is still using different keymap. But if you could somehow loin(like tying all keys to know for username and password), then it will use the kaymap which is saved in the last or any session.

Thanks for helping. 

Adarsh

---

### Post by amjjawad on 2011-11-05
> **Adarzh said:**
> amjjawad,

Actually it worked but only after you logged in to the system. In the login page, it is still using different keymap. But if you could somehow loin(like tying all keys to know for username and password), then it will use the kaymap which is saved in the last or any session.

Thanks for helping. 

Adarsh


I'm so sorry, could you please explain that again?

You most welcome but I did nothing yet :)

---

### Post by Adarzh on 2011-11-05
What i meant say is that, in the Login page(where you enter username and password), the keyboard layout is still the old one. But if i could somehow login, then layout will become US again.

For example in my case, what i want is US layout but my system  is always defaulted to Senegal upon reboot. So i took your advice and updated the Lxkeymap  and saved the layout  to US. Now after reboot i again reached the login page but here,  the layout is still Senagal and not US. My username is 'adarsh' . For Senagal keyboard it is 'qdqrsh'. so if i type these, i could login to the system. Upon logging in to the system, keyboard layout will be the one that you saved in your last session (here US).

Hopes that explains..

Adarsh

---

### Post by amjjawad on 2011-11-05
> **Adarzh said:**
> What i meant say is that, in the Login page(where you enter username and password), the keyboard layout is still the old one. But if i could somehow login, then layout will become US again.

For example in my case, what i want is US layout but my system  is always defaulted to Senegal upon reboot. So i took your advice and updated the Lxkeymap  and saved the layout  to US. Now after reboot i again reached the login page but here,  the layout is still Senagal and not US. My username is 'adarsh' . For Senagal keyboard it is 'qdqrsh'. so if i type these, i could login to the system. Upon logging in to the system, keyboard layout will be the one that you saved in your last session (here US).

Hopes that explains..

Adarsh

Ok, so you mean it does save it ONLY at the Login Screen but once you login to your Desktop, it changes to the default which is US Layout, right?

And the fix that I posted previously wasn't helpful, right?

If you are 100% sure that you followed this post: [http://ubuntuforums.org/showpost.php?p=11420771&postcount=3](http://ubuntuforums.org/showpost.php?p=11420771&postcount=3)

and the problem is still happening, please report that as explained in that post :)

> If you notice any bugs then report them here: [http://launchpad.net/lxkeymap](http://launchpad.net/lxkeymap)

---

### Post by Adarzh on 2011-11-05
Exactly..the fix not working at Login page...but it will work after you logged in to the Desktop.

What i think is the problem is that the keymap configuration file is saved at .config/lxkeymap.cfg at user level not at the global level. 

This is the content of my keymap.cfg file
> 
[Global]
layout = us
variant = 


Adarsh

---

### Post by amjjawad on 2011-11-05
> **Adarzh said:**
> Exactly..the fix not working at Login page...but it will work after you logged in to the Desktop.

What i think is the problem is that the keymap configuration file is saved at .config/lxkeymap.cfg at user level not at the global level. 

This is the content of my keymap.cfg file


Adarsh

Got it :)
This is very interested.

Could you please report that as a bug as previously advised? thank you :)

---

### Post by llelectronics on 2011-11-05
It is not intended that lxkeymap should change the global keymap (so this included lxdm login manager after a reboot).
To change your global keymap do the following in a lxterminal:

```

sudo dpkg-reconfigure keyboard-configuration

```
There you have to configure your keyboard & layout.
This will change the keymap on ttys and globally also on lxdm.

---

### Post by Adarzh on 2011-11-05
> **llelectronics said:**
> It is not intended that lxkeymap should change the global keymap (so this included lxdm login manager after a reboot).
To change your global keymap do the following in a lxterminal:

```

sudo dpkg-reconfigure keyboard-configuration

```
There you have to configure your keyboard & layout.
This will change the keymap on ttys and globally also on lxdm.

Thanks. It worked......

---

### Post by amjjawad on 2011-11-05
> **Adarzh said:**
> Thanks. It worked......

That's great to know :)

Please mark your thread as SOLVED if you don't have further Qs :)

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=7263[/IMG]
[IMG]http://ubuntuforums.org/album.php?albumid=2161&pictureid=7263[/IMG]

---

### Post by cmike on 2011-11-24
> **Adarzh said:**
> Exactly..the fix not working at Login page...but it will work after you logged in to the Desktop.

What i think is the problem is that the keymap configuration file is saved at .config/lxkeymap.cfg at user level not at the global level. 

This is the content of my keymap.cfg file


Adarsh

I've got the same situation:
```
[Global]
layout = pl
variant = 

```
and every boot I have to set my keyboard layout to polish programmer - so I think that's something wrong with this config file

---

