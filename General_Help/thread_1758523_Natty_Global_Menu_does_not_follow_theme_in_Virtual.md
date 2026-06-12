---
title: "Natty Global Menu does not follow theme in Virtualbox"
date: 2011-05-14
forum: General Help
---

### Post by Kri5 on 2011-05-14
I am running Ubuntu 11.04 Natty Narwhal on Virtualbox 4.0.6 (host OS is Ubuntu 10.10 Maverick) and for some reason the Global Menu does not follow the theme selected in appearances. 
By this I mean that no matter what theme I select the Global Menu resembles something like a Windows 95 theme, I presume a default basic theme.
This also applies to the 'Home Folder' icon in the launcher and the corresponding icons in the home folder itself.

Has anyone else come across this and does anyone know how to correct it?

I have also posted on the Virtualbox forums, but judging by the number of people logged on at the time I fancy my chances here better.

So any help would be greatly appreciated as I'm new to Virtualbox.

---

### Post by Kri5 on 2011-05-19
Typing the command below into the Terminal of the OS running in Virtualbox appears to resolve the issue, however you need to repeat every time to run Virtualbox.

killall -9 gnome-settings-daemon && gnome-settings-daemon

---

