---
title: "Kubuntu boot halts after login"
date: 2011-02-08
forum: General Help
---

### Post by Niels_D on 2011-02-08
Hi all!
 
I have a problem after editing my grub configuration.
 
After the login screen, the KDE icons appear.
When it gets to "HDD" icon, it halts and the only option remaining is to reboot.
I can't boot into the terminal environment. When I try that, I get an empty screen without text (maybe because of "quiet splash"?
 
Does anyone know how I might fix this? :confused:
Thanks!

---

### Post by Niels_D on 2011-02-08
[SIZE=1]Hmm, it seems to have a relation to the used boot splash resolution.[/SIZE]
[SIZE=1]I set this value to be [COLOR=black][FONT=Courier New][FONT=Verdana][SIZE=1]1920x1080, but this seems to make any kind of textual boot info and terminal dissapear.[/SIZE][/FONT][/FONT][/COLOR][/SIZE]
[SIZE=1][COLOR=black][FONT=Courier New][/FONT][/COLOR][/SIZE] 
[SIZE=1][COLOR=black][FONT=Courier New][FONT=Verdana][SIZE=1]Anybody got an idea of the supported resolutions for this?[/SIZE][/FONT] [/FONT][/COLOR][/SIZE]

---

### Post by Niels_D on 2011-03-01
I re-installed Kubuntu to be able to login again into the normal environment.
Also here, when I press CTRL+ALT+F2 the screen goes black instead of displaying terminal texts.

Can someone please explain this? :(

---

### Post by mastablasta on 2011-03-01
i am a bit fresh with KDE here. but...
 
someone in KDE forums had a similar issue: [http://forum.kde.org/viewtopic.php?f=63&t=86876](http://forum.kde.org/viewtopic.php?f=63&t=86876)
 
it seems to be graphics card related. i haven't tried accessing the virtual consoles yet. i guess it will be a thing to try today.

---

### Post by Niels_D on 2011-03-01
Thanks for the reply!

I indeed found some other posts that were (Nvidia) graphics card related.
I am using the fglrx ATI drivers, but I didn't find anything about this on the interwebs...

The main problem is that also when I boot in the terminal mode, I don't get anything to see, which sucks for problem solving.:(

---

