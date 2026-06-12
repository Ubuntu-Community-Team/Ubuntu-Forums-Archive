---
title: "GRUB2 editor in Ubuntu 12.04"
date: 2012-05-23
forum: General Help
---

### Post by Nityanandi on 2012-05-23
Pkg. has various names: kcm-grub2; kde-config-grub2; 0.5.0-0ubuntu3: 

Ubuntu Software Center puts icon for newly installed ap on the Launcher. I instead used Synaptic, installed kde-config-GRUB2, highly promising by all accounts. Now i can't get into it, Dash doesn't do anything, no matter how i name it, and i don't want to kill myself with Terminal, where Command not recognized. Happy and grateful to do so if advised. Not proficient on my own. 

I am very grateful to Linux and Ubuntu, already, and also in advance for your kind-hearted help.

---

### Post by wilee-nilee on 2012-05-23
> **Nityanandi said:**
> Ubuntu Software Center puts icon for newly installed ap on the Launcher. I instead used Synaptic, installed kde-config-GRUB2, highly promising by all accounts. Now i can't get into it, Dash doesn't do anything, no matter how i name it, and i don't want to kill myself with Terminal, where Command not recognized. Happy and grateful to do so if advised. Not proficient on my own. 

I am very grateful to Linux and Ubuntu, already, and also in advance for your kind-hearted help.

What is your final goal here?

---

### Post by Nityanandi on 2012-05-25
> **wilee-nilee said:**
> What is your final goal here?
Wilee-Nilee, *thanks*. Trying to USE it. Don't have a command for the terminal, don't have an icon, Dash (HUD) is void. 

And to you, thanks for consideration. Searched it up throughout /usr/share; and removed it with Ubuntu Software Center as a last resort, so Ubuntu Software Center and not Synaptic could then reinstall. And then USC would presumably put the icon on the launcher. It reinstalled, but still no command, no icon. The proper file name was kde-config-grub2, and the installed Ubuntu version of same is 0.5.0-0ubuntu3. 

Really thank you, not only saying again, but i'll be feeling it more often than you'd guess.

---

### Post by Nityanandi on 2012-05-25
It is a perennial problem...installing something that doesn't provide a working icon, doesn't store itself in the right place, because different distros use different dirctories for the operation, or somehow simply doesn't have a command that we can discover. And then those applications are never used, because we just can't get into them. Seldom find out how. So the main "final goal" here, as you say, is to know how, once and for all, to find out how to launch applications in this situation. And that [SIZE="4"]is[/SIZE] a big one. For that reason, your help is valuable, more than just for the grub2 configuration application that i *have* to have.

---

### Post by wilee-nilee on 2012-05-25
If you are trying to customize the grub menu most often people use the grub-customizer.

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by haresear on 2012-05-25
I would suggest using the terminal to discover and launch the app for the first time. Then you can pin it to the launcher. It is safe to use 'man <command>' to test for the name of a command without doing anything. Also, use the tab key to auto-complete the name if you have the first part of the name. Hit the tab key twice and it will give you all the possibilities for completion. For example, in your case I would try:

```
man kde-config<tab><tab>
```

Based on the synaptic name, I would expect the name to be
 'kde-config-grub'

---

### Post by Nityanandi on 2012-05-25
To Haresear, thanks very much, but those two things had already been tried. One thing please DO tell us. If the terminal *had* brought up the application, how could it be pinned to the Launcher? That is important, because many people, even proficient ones, have been stuck on this problem with new installations, and i'm chasing the fix for all time. 


And to Wilee-Nilee, our dear Ubuntu junkie, i heard last night about GRUB Customizer, and thought that Daniel Richter was the same coder who brought it out as kde-config-grub2. Now by your advice i plan to install; and do again genuinely feel gratitude. ):P

---

### Post by Nityanandi on 2012-05-25
Wilee-Nilee, Daniel Richter *is* the same programmer who wrote both grub2 editors. Maybe grub-customizer is an older version. Maybe it will do exactly what is needed. I ought to re-post this thread in a larger context: how to open a recalcitrant newly installed application. This is the vital information that would have fixed the dilemma, because all the power is sitting here in this box and cannot do its thing. 

And you couldn't be more welcome to have a go! Answer *that* one. Glory!! Haresear's methods were too elementary, though kindly supplied. They had been used. Not enough penetration.

---

### Post by critin on 2012-05-26
> doesn't store itself in the right place,
Have you checked in System Settings?

[https://launchpad.net/ubuntu/precise/i386/kde-config-grub2](https://launchpad.net/ubuntu/precise/i386/kde-config-grub2)

I don't know about putting it in a launcher, but it's not something you would normally need too often, is it?

---

### Post by Nityanandi on 2012-05-27
Critin, 

Thanks for Reply. No. Of course boot menu config application would seldom be needed, maybe, at most once, per installation. As it is, can't reach it at all. If Ubuntu knew where to find it with an icon, it would also know using the terminal or Dash. My son chased up the doc files and a few others on my computer; the installation was done. But we can't find the executable. 

Looking for it in System Settings sounds as likely as finding turtle feathers. But i tried. You may well know how you would go about it, which it would be most kind of you to explain. Once again, Critin, you are good to help me out, and Linuxy; thank you. Thanks for reading the Posts!...serving universal good. :)

---

### Post by practic on 2012-05-27
First of all, are you using Ubuntu or Kubuntu?

The kde-config-grub2 program is meant to run as a module inside the KDE System Settings program. So you won't see it if you're running the Gnome version of Ubuntu.

Like the others suggested, I would recommend Grub Customizer, as it works nicely.

By the way, since you used Synaptic, it's possible to turn on an option that shows all the files that were installed with any given package. It's under Settings->Preferences in Synaptic. The option is at the top and is called "Show package properties in the main window". If you check this on, you will see another panel open up near the bottom of the window. Then you can select any package that you already installed, and one of the tabs in this new panel shows all the files that were installed (and their paths).

For example, for kde-config-grub2, it lists the following:

/etc
/etc/dbus-1
/etc/dbus-1/system.d
/etc/dbus-1/system.d/org.kde.kcontrol.kcmgrub2.conf
/usr
/usr/lib
/usr/lib/kde4
/usr/lib/kde4/kcm_grub2.so
/usr/lib/kde4/libexec
/usr/lib/kde4/libexec/kcmgrub2helper
/usr/share
/usr/share/dbus-1
/usr/share/dbus-1/system-services
/usr/share/dbus-1/system-services/org.kde.kcontrol.kcmgrub2.service
/usr/share/doc
/usr/share/doc/kde-config-grub2
/usr/share/doc/kde-config-grub2/changelog.Debian.gz
/usr/share/doc/kde-config-grub2/copyright
/usr/share/kde4
/usr/share/kde4/config.kcfg
/usr/share/kde4/config.kcfg/kcm_grub2.kcfg
/usr/share/kde4/services
/usr/share/kde4/services/kcm_grub2.desktop
/usr/share/locale
/usr/share/locale/da
/usr/share/locale/da/LC_MESSAGES
/usr/share/locale/da/LC_MESSAGES/kcm-grub2.mo
/usr/share/locale/de
/usr/share/locale/de/LC_MESSAGES
/usr/share/locale/de/LC_MESSAGES/kcm-grub2.mo
/usr/share/locale/et
/usr/share/locale/et/LC_MESSAGES
/usr/share/locale/et/LC_MESSAGES/kcm-grub2.mo
/usr/share/locale/hu
/usr/share/locale/hu/LC_MESSAGES
/usr/share/locale/hu/LC_MESSAGES/kcm-grub2.mo
/usr/share/locale/nl
/usr/share/locale/nl/LC_MESSAGES
/usr/share/locale/nl/LC_MESSAGES/kcm-grub2.mo
/usr/share/locale/pt
/usr/share/locale/pt/LC_MESSAGES
/usr/share/locale/pt/LC_MESSAGES/kcm-grub2.mo
/usr/share/locale/pt_BR
/usr/share/locale/pt_BR/LC_MESSAGES
/usr/share/locale/pt_BR/LC_MESSAGES/kcm-grub2.mo
/usr/share/locale/sv
/usr/share/locale/sv/LC_MESSAGES
/usr/share/locale/sv/LC_MESSAGES/kcm-grub2.mo
/usr/share/locale/uk
/usr/share/locale/uk/LC_MESSAGES
/usr/share/locale/uk/LC_MESSAGES/kcm-grub2.mo
/usr/share/polkit-1
/usr/share/polkit-1/actions
/usr/share/polkit-1/actions/org.kde.kcontrol.kcmgrub2.policy

The line that has the ".desktop" entry would probably be executable: /usr/share/kde4/services/kcm_grub2.desktop

---

### Post by Nityanandi on 2012-05-27
Critin, now understood: 

[COLOR="RoyalBlue"]Binary packages built by this source
kde-config-grub2: Configuration module for the GRUB2 bootloader
 This is a configuration module for System Settings for configuring the
 GRUB2 bootloader.[/COLOR] 

It wasn't placed there. Thanks very much.

---

### Post by critin on 2012-05-27
You're welcome.   Grub Customizer does the same job and is easier to work with--imo.

---

### Post by Nityanandi on 2012-05-28
Dear Practic, 
this sounds fabulous and easy. Years ago it was disastrous to install too many KDE components to Ubuntu, and Kubuntu pkg mgs were impossible. So i use Ubuntu, though KDE is awesome and an ***old*** friend. 

Anyhow, after those non-trivial difficulties with KDE pieces on Ubuntu, i now run ... :lolflag:   two identical Ubuntu OSs, and even have a Fedora 16, strictly KDE, where again, pkg mgr none too happy. Story is, my Ubuntus are not really equal; one is preferred. And though that one is stepped up to 12.04, the other has yet to be updated. When that is done, the boot menu will have made ***it*** the default. The [COLOR="RoyalBlue"]menu customizer[/COLOR] has to be sorted out before upgrade for peace. Somehow i care a lot, and can't stand 5012 extra lines in the boot menu. Installation of grub-customizer was ... Lord ... the [COLOR="RoyalBlue"]same story again.[/COLOR] Can't find it. Didn't even fight, assuming the one under discussion here is the latest. 

Every one of your exquisite suggestions will be tried until one works. On the less-preferred Ubuntu, still 11.10, the kde-config-grub2 and KDE have successfully been installed, as an experiment, and it looks fine so far. Now it can be logged in for a KDE session and System Settings checked there. So it can be tested before the upgrade. 

People have said kde-config-grub2 allows the choice of which OS to store the boot menu in, as well as the default, so that either of the other two OSs here could be removed harmlessly at any time. This should be verified first, to not brick the computer. 

Sorry i have been prolix here, sharing the real considerations. My brother lives in Vernon, BC forest, incidentally, whence i left for Australia, but it gave me pang to see your piercingly intelligent face, and place. Indeed thanks. 

[CENTER][/CENTER]):P 

Initial bumbling... 
[COLOR="RoyalBlue"]Terminal:[/COLOR] 
sudo: /usr/share/kde4/services/kcm_grub2.desktop: command not found
nityanandi@Transcendental:~$ sudo kcm_grub2.desktop
[sudo] password for nityanandi: 
sudo: kcm_grub2.desktop: command not found
nityanandi@Transcendental:~$ sudo kcm_grub2
sudo: kcm_grub2: command not found

[COLOR="RoyalBlue"]Icon[/COLOR] copied nicely to the desktop, owing to your Synaptic Preferences advice; and : 
"There was an error launching the application."



Practic...my mind comes and goes. What's next?

---

### Post by critin on 2012-05-29
>  Installation of grub-customizer was ... Lord ... the [COLOR=RoyalBlue]same story again.[/COLOR] Can't find it. 

Didn't Software Center add a line on its page (underneath the description) telling you where you can find it?   It may not in 12.04, but it was sure handy.

---

### Post by Nityanandi on 2012-05-30
Thank you once again, Critin. That wizard named Practic said (see above) that Synaptic, if told in Preferences, would show pkg properties, including paths. And, true. Story is now, it can be found, but cannot launched. I have another Ubuntu partition, to which i installed KDE and of course the two grub2 configuration tools also mentioned above. As soon as i have time i'll use System Settings (Gnome) to change the default session to KDE. And then, also according to said gentleman Practic, the boot configuration tool SHOULD... even as you told me ... appear in System Settings. 

You're good to follow this thread.

---

### Post by bartora on 2013-01-21
Well, I solve the problem here in my computer using some suggestions people gave, and the final solution was: I created a script with a name like, for example, grub_config.sh and saved it in a folder (for example you can create a folder, put the name Program on the folder and save your script there).

The content of the script is:

```
cd /usr/share/kde4/services/ 
gksu kcmshell4 kcm_grub2
```

Make your script executable with the comand:

```
chmod +x grub_config.sh
```

Than I lounched the main menu (if you don't find it just type the command: ```
alacarte
``` in a terminal).

After that, choose in the main menu the place you want your louncher to go, click in new item, than give a name to your aplication in the name field. Than, on the command field you give the command to execute your script, like:

```
./Programs/grub_config.sh
```

And that's it. It should work. If something goes wrong try to execute your application like a terminal application (you can choose it in the main menu), and maybe change the command gksu for the command sudo on your script.

Here things are working right now. Thank's everybody for your help.

---

