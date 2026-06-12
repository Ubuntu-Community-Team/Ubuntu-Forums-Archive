---
title: "Problem in Compiz Desktop Effects"
date: 2009-10-22
forum: General Help
---

### Post by chrislionheart on 2009-10-22
[SIZE=3]I recently installed 'Compiz Desktop Effect' from the Add/Remove option in the taskbar. 
Everything downloaded without any problem and also got installed without any problem.

It got perfectly installed on my machine. 
But when I went in the System>Preferences, the option of Compiz Effect was missing.
I uninstalled it and again reinstalled it but still the same problem..... it doesn't show up in the preference. 

And because of this I cannot use it......[/SIZE]


[SIZE=6][COLOR=Red]PLEASE HELP!!!!![/COLOR][/SIZE]

---

### Post by P4man on 2009-10-22
Please tone down the caps and colors and giant fonts.

Do you have an "extra" setting on the visual effects tab in appearance?
IF so, its working. If you want to configure all the other compiz bells and whistels, you need to install compizconfig-settings-manager

---

### Post by chrislionheart on 2009-10-22
Yeah the the EXTRA setting on the appearance tab works very well......

So you say that if I install **compizconfig-settings-manager **from the Add/remove option then I will get that option in the preferences menu.... right!!!!

I try it out........... and thank you very much for the help

---

### Post by chrislionheart on 2009-10-22
I searched it in the ADD/Remove, but didn't get it...........

Where can I download this 'compizconfig-settings-manager'

Please help!!!

---

### Post by P4man on 2009-10-22
in a terminal run:
```
sudo apt-get install compizconfig-settings-manager
```

or look it up in synaptic package manager.

---

### Post by mr.suchy on 2009-10-22
I find this in two minutes on google, here you're :[http://www.tech-recipes.com/rx/2756/ubuntu_install_compiz_config_settings_manager_configure_desktop_effects/](http://www.tech-recipes.com/rx/2756/ubuntu_install_compiz_config_settings_manager_configure_desktop_effects/)

---

### Post by chrislionheart on 2009-10-22
I typed that in the terminal everything went okay but still nothing appeared in the preferences menu

this is all that happened in the terminal


[B]chris@chris-desktop:~$ sudo aptitude install compizconfig-setting-manager
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "compizconfig-setting-manager"
Couldn't find any package whose name or description matched "compizconfig-setting-manager"
The following packages will be REMOVED:
  libphysfs-1.0-0{u} libsdl-image1.2{u} 
0 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 233kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 137137 files and directories currently installed.)
Removing libphysfs-1.0-0 ...
Removing libsdl-image1.2 ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done[/B]

---

### Post by chrislionheart on 2009-10-22
I typed that in the terminal is what happened.........

sudo apt-get install compizconfig-settings-manager

[B]chris@chris-desktop:~$ sudo apt-get install compizconfig-setting-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compizconfig-setting-manager
chris@chris-desktop:~$ [/B]

but still nothing came up in the preferences menu    :(

please help

---

### Post by P4man on 2009-10-22
click the link already given above.. use your imagination, use google,..
If you really get stuck, feel free to ask but please dont 
[SIZE="7"]HELP URGENT PLEASE [SIZE="3"]
MY SHOES ARE UNTIED[/SIZE]
[/SIZE]

---

### Post by chrislionheart on 2009-10-22
[IMG]http://cosmicmarshall.com/Screenshot.png[/IMG]

---

### Post by chrislionheart on 2009-10-22
But I still don't get that option

---

### Post by P4man on 2009-10-22
I take it that screeenshot was supposed to show the preferences menu?
If there is no compiz config settings menu try logging out and in again.

---

### Post by chrislionheart on 2009-10-22
you mean I restart my computer and then I may get that compizconfig thing in my preferences menu.........
right?

I am very sorry, if I am asking dumb questions..... I am very new to linux and therefore finding some hard time in doing many stuff..........

---

### Post by chrislionheart on 2009-10-22
[IMG]http://cosmicmarshall.com/Screenshot-1.png[/IMG]

---

### Post by P4man on 2009-10-22
I should have looked closer at your command output. You mistyped. You have to install compizconfig-setting**s**-manager 

Dont type it entirely, use the tab key to complete. Or copy paste the command, or search the package in synaptic (system > adninstation > synaptic)

Anyway

```
sudo apt-get install compizconfig-settings-manager 
```

should do the trick

---

### Post by chrislionheart on 2009-10-22
[IMG]http://cosmicmarshall.com/Screenshot-2.png[/IMG]

---

### Post by chrislionheart on 2009-10-22
Just cannot understand.......... what seems to be the problem.....

Everything works fine........ I didn't get any errors till now........ but still why this problem...

---

### Post by P4man on 2009-10-22
No thats the wrong app. thats for KDE (Kubuntu)

Also, enable ALL available applications in the drop down and you will see compiz config settings manager

---

### Post by P4man on 2009-10-22
[IMG]http://img24.imageshack.us/img24/4038/screenshot001lt.png[/IMG]

---

### Post by chrislionheart on 2009-10-22
okay okay
..........................

I will just check that....

---

### Post by chrislionheart on 2009-10-22
[B]THANK YOU SOOOOOOOOOOOOOO VERY VERY MUCH........

PROBLEM SOLVED....   THANK YOU P4man   very very much.....

I owe you [/B]

---

### Post by chrislionheart on 2009-10-22
[SIZE=7]THANKS TO [COLOR=DarkOrange]P4MAN[/COLOR][/SIZE]
[SIZE=6][SIZE=7]:)[/SIZE]

Problem solved!!!!!! Hurray [/SIZE]

---

