---
title: "Skim doesn't work"
date: 2010-10-12
forum: General Help
---

### Post by oromay on 2010-10-12
As I know skim is only program to write in amharic. It worked well on Kubuntu 10.4, but now I have some problem:(. 
I was following this instruction  [https://help.ubuntu.com/community/SCIM/Kubuntu](https://help.ubuntu.com/community/SCIM/Kubuntu)
When I am trying to start the SKIM it shows me the next message:

nikolay@Kolya:~$ sudo im-switch -s skim
No system wide default defined just for locale ru_RU .
Use "all_ALL" quasi-locale and set IM.
nikolay@Kolya:~$ skim
kbuildsycoca running...
Reusing existing ksycoca
DCOP Cleaning up dead connections.
KCrash: Application 'skim' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.

I am a freshman in Linux so be friendly please;-)[COLOR=#000000][FONT=Arial][FONT=Tahoma][/FONT][/FONT][/COLOR]

---

### Post by Zorael on 2010-10-12
I think you can input in Amharic via the **m17n** libraries, using any input method engine that support those. I'd advise against using SCIM because it's old and no longer under active development, and likewise Skim because it's based on Qt3.

You could try either IBus or UIM.

To try **UIM**;
```
$ sudo aptitude install uim uim-qt uim-m17nlib
$ sudo sed -ie 's/toolbar-qt)/toolbar-qt4)/g' /etc/X11/xinit/xinput.d/uim-toolbar-qt   # makes it start the correct toolbar
$ im-switch -s uim-toolbar-qt
```
Log out and back in, and you should get the UIM toolbar to automatically start. Enter its preferences and set up m17n for Amharic input.

-----------

To try **IBus**;
```
$ sudo aptitude install ibus ibus-gtk ibus-qt4 ibus-m17n
$ im-switch -s ibus
```
Likewise, log out and back in.

---

### Post by oromay on 2010-10-13
Thank you a lot for advices!
But it still doesn't work...

trying ibus
[I]nikolay@Kolya:~$ sudo im-switch -s ibus                           
No system wide default defined just for locale ru_RU .                                                                                                                              
Use "all_ALL" quasi-locale and set IM.     [/I]            

trying uim
[I]nikolay@Kolya:~$ im-switch -s uim-toolbar-qt4
Error: no configuration file "uim-toolbar-qt4" exists.
Error: No action taken.[/I]

what should I do?

---

### Post by Zorael on 2010-10-13
Don't use sudo with im-switch, it doesn't seem to work with all locales. So just '**im-switch -s ibus**'.

And the UIM command has a typo, my bad. I edited the post and corrected it. It should spell **uim-toolbar-qt**.
```
$ im-switch -s uim-toolbar-qt
```

---

### Post by oromay on 2010-10-13
Thank you, it is not so difficult as I thought:-)

---

