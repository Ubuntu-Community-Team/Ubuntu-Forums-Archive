---
title: "Trying to change default folder pcmanfm opens to"
date: 2011-11-12
forum: General Help
---

### Post by Bucky Ball on 2011-11-12
Hi all,

Quick one. As the title explains, I am trying the alter the default folder pcmanfm file manager opens to. I am using version 0.9.7 and Ubuntu 10.10 and have tried inserting the following under the section [general]:

```
home_folder=FOLDER
```... where 'FOLDER' is the folder I want pcmanfm to open by default, into the following two config files, while there are no pcmanfm windows open and appears there is no pcmanfm process running:

```
/.config/pcmanfm/pcmanfm.conf
/.config/pcmanfm/LXDE.conf
```... in the former the added line has disappeared when I save/close and open the file again (so I figure this is being overwritten and is the wrong config file) the latter a pointless exercise no doubt as I'm not using LXDE (actually using xfce). Anyhoo, no dice. Still keeps opening to my /home/user folder and there doesn't seem to be any other config files I can try adding that to. The how-to I read suggested:

```
~/.config/pcmanfm-mod/main
```... but I don't seem to have that, although I do have it in another install which is either 10.04 LTS or 11.04, neither of which I use at the moment because I haven't had time to fix their numerous glitches on my machine (a project for the xmas break). Anyone got any ideas? Perhaps I am attempting to add it to the wrong section - [general] - of the config file. 

I would really like to get this happening. Reason? I am frantically attempting to finish uni stuff for end of year and need to be able to open directly to the specific folder I'm working in rather than click through five to get there. Time saver, believe me. I use a hotkey to open pcmanfm so not just a matter of clicking on the folder (which for me is more cumbersome). 

Cheers and here's hoping someone knows the trick!

---

### Post by Bucky Ball on 2011-11-14
No clues? This is annoying ... ;(

---

