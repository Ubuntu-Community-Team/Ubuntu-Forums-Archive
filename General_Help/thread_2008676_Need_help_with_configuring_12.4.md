---
title: "Need help with configuring 12.4"
date: 2012-06-23
forum: General Help
---

### Post by aviedw on 2012-06-23
I have been adjusting quite well to the new GUI in 12.4. But i must be remise due mainly to the loss in configuing that is granted with this new ubuntu distribution. 

Problem 1. How do i determine if i have properly applied my third party Nvidia drivers? And is there anything that allows you to adjust the graphical effects that the graphics afford you.

Problem 2. I grew very fond of a screen saver called Electric Sheep. My last distribution was 10.4 and i never had a problem applying that specfic screensaves or any other screensaves for that matter. The functon to simply apply new screen savers has copmletely excaped me. 

Problem 3. Getting videos to play on youtube and other such services seems to be a lot harder than i anticipated. I ran the script that installs all the extras and restricted programs wtih no avail.

Other than that i must admit that this new distribution is quite stable. Once i have worked out these few quirks, i can quite honestly see my self staying with this distro and release for quite some time.

Any assistance offered is appreciated. Thanks in advance.

---

### Post by HiImTye on 2012-06-23
>  Problem 1. How do i determine if i have properly applied my third party  Nvidia drivers? And is there anything that allows you to adjust the  graphical effects that the graphics afford you.use 'nVidia X Server Settings'
should be in System Tools>Administration
alternately, you can just run
```
nvidia-settings
```
in a terminal or 'run' prompt

> Problem 2. I grew very fond of a screen saver called Electric Sheep. My  last distribution was 10.4 and i never had a problem applying that  specfic screensaves or any other screensaves for that matter. The  functon to simply apply new screen savers has copmletely excaped me. ```
sudo apt-get install electricsheep xscreensaver
```you will need to run xscreensaver and then configure it to use electricsheep. if there's no entry for it in the menu then post back here and Ill find the instructions for you

>  Problem 3. Getting videos to play on youtube and other such services  seems to be a lot harder than i anticipated. I ran the script that  installs all the extras and restricted programs wtih no avail.check if you have adobe flash installed
```
sudo apt-get install aptitude; aptitude search flashplugin-installer
```if there is no entry for it, you may want to consider adding the [medibuntu]("https://help.ubuntu.com/community/Medibuntu") repo

---

