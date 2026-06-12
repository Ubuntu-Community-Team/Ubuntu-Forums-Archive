---
title: "uninstall wine?"
date: 2011-07-26
forum: General Help
---

### Post by qwertyjjj on 2011-07-26
I am trying to uninstall wine but it keeps crashing (using the wine uninstall option).
I also tried to use the software centre but it doesn't say it is unstalled.
Anyway to do this? I believe wine has the .NET framework installed, which also needs to go.

This doesn't work:

n-Inspiron-9300:~$ sudo apt-get --purge remove wine
[sudo] password for j: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I also reinstalled and uninstalled and it still remains in the Applications list and still takes about about 300Mb

---

### Post by Wayne_V on 2011-07-26
if you didn't install wine with apt-get you can't uninstall it with apt-get.   (see 'dpkg --list | grep wine')

if you installed from a downloaded tar ball you'll need to see the documentation there for uninstall.

---

### Post by qwertyjjj on 2011-07-26
> **Wayne_V said:**
> if you didn't install wine with apt-get you can't uninstall it with apt-get.   (see 'dpkg --list | grep wine')

if you installed from a downloaded tar ball you'll need to see the documentation there for uninstall.

I'm pretty sure I used the software centre
So, how can I uninstall it?

:~$ dpkg --list | grep wine
ii  ttf-symbol-replacement-wine1.3                               1.3.24-0ubuntu1~ppa1~maverick1                    Free font with the same metrics as Symbol
ii  wine1.3                                                      1.3.24-0ubuntu1~ppa1~maverick1                    Microsoft Windows Compatibility Layer (Binary Emulator and Library)
ii  wine1.3-gecko                                                1.2.0-0ubuntu1~maverickppa1                       Microsoft Windows Compatibility Layer (Web Browser)
ii  winetricks                                                   0.0+20110629~ppa1                                 Microsoft Windows Compatibility Layer (winetricks)

---

### Post by deconstrained on 2011-07-26
When you install applications in Wine, they go into your home folder (in ~/.wine/) and this is not removed when you uninstall wine. If you wish to remove them, delete ~/.wine/ and edit your menus manually. Better yet, use wine itself to manage the removal of the software you don't want (I'm pretty sure there's a way to do this) and then uninstall wine. When you're done, if the menu items still remain, you'll just have to remove/disable them manually (this is a problem I've encountered myself--menu items that just won't die).

---

### Post by qwertyjjj on 2011-07-26
> **deconstrained said:**
> When you install applications in Wine, they go into your home folder (in ~/.wine/) and this is not removed when you uninstall wine. If you wish to remove them, delete ~/.wine/ and edit your menus manually. Better yet, use wine itself to manage the removal of the software you don't want (I'm pretty sure there's a way to do this) and then uninstall wine. When you're done, if the menu items still remain, you'll just have to remove/disable them manually (this is a problem I've encountered myself--menu items that just won't die).

I deleted .wine
How can I remove the menu item?

---

### Post by Arbayong on 2011-07-26
> **qwertyjjj said:**
> I deleted .wine
How can I remove the menu item?

open menu editor under ur applications/programs menu. once in menu editor select applications and scroll down to wine. click on wine and all wine programs will pop to the right side of ur screen. uncheck all the checkboxes beside these applications. apply ur changes and close the window.

am not sure but i hope it works

---

### Post by lkjoel on 2011-07-26
If you installed Wine Beta, try this:
```
sudo apt-get remove --purge wine1.3
```

---

### Post by qwertyjjj on 2011-07-26
> **Arbayong said:**
> open menu editor under ur applications/programs menu. once in menu editor select applications and scroll down to wine. click on wine and all wine programs will pop to the right side of ur screen. uncheck all the checkboxes beside these applications. apply ur changes and close the window.

am not sure but i hope it works

can't see menu editor.
anyway to run it from the terminal?

---

### Post by WorMzy on 2011-07-26
I should have this bound to a hotkey.

[http://wiki.winehq.org/FAQ#head-ddc6f242056eb1a4fe566c9434d15fd8b64606aa]("http://wiki.winehq.org/FAQ#head-ddc6f242056eb1a4fe566c9434d15fd8b64606aa")

---

### Post by qwertyjjj on 2011-07-26
> **lkjoel said:**
> If you installed Wine Beta, try this:
```
sudo apt-get remove --purge wine1.3
```

that worked, thanks?
any folders left to  remove?

---

### Post by lkjoel on 2011-07-26
> **qwertyjjj said:**
> that worked, thanks?
any folders left to  remove?
I don't think so, but just to be on the safe side:
```
sudo apt-get purge wine1.3-gecko ttf-symbol-replacement-wine1.3 winetricks
rm -rf ~/.wine
sudo rm -rf ~/.wine
```

---

### Post by turtle153 on 2011-07-26
Just to explain lkjoels answer, you need to type the exact package name into the terminal to remove it. It can be confusing when using the Software Centre as the package name is hidden, so as a general rule, if you install with the Software Centre, remove with the Software Centre.

Edit: purge "Remove[s] packages and config files", so it should delete ~/.wine too

---

### Post by lkjoel on 2011-07-26
> **turtle153 said:**
> Just to explain lkjoels answer, you need to type the exact package name into the terminal to remove it. It can be confusing when using the Software Centre as the package name is hidden, so as a general rule, if you install with the Software Centre, remove with the Software Centre.

Edit: purge "Remove[s] packages and config files", so it should delete ~/.wine too
I know, but just in case something had gone wrong, it never hurts to remove .wine again ;-)

---

### Post by WorMzy on 2011-07-26
> **turtle153 said:**
> Edit: purge "Remove[s] packages and config files", so it should delete ~/.wine too

This is actually a misconception. apt-get will /never/ touch files in any home directories. "Config files", as far as apt-get (and any other dpkg front-end, e.g. aptitude) is concerned, refers to system-wide config files, which are stored in /etc.

---

### Post by lkjoel on 2011-07-26
> **WorMzy said:**
> This is actually a misconception. apt-get will /never/ touch files in any home directories. "Config files", as far as apt-get (and any other dpkg front-end, e.g. aptitude) is concerned, refers to system-wide config files, which are stored in /etc.
Thanks for the clarification!

---

