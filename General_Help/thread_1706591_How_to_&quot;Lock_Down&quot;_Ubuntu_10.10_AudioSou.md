---
title: "How to &quot;Lock Down&quot; Ubuntu 10.10 Audio/Sound Settings ?"
date: 2011-03-14
forum: General Help
---

### Post by Jags_FL on 2011-03-14
As the title says, how could I "Lock Down" audio / sound settings in Ubuntu 10.10 please...

This is for an elderly person's PC. Somehow every week or so, he manages to "totally mute all sound", so I would like to lock it down completely that he cannot change/mute it(even if that means he can't lower/raise the volume level).

Many thanks in advance, any help is greatly appreciated.

---

### Post by flipper T on 2011-03-14
no idea at all as how to achieve this.... :)

however, you might consider placing a [SIZE="4"]very big[/SIZE] link to the appropriate dialog box on the desktop.

see attached screeshot

i had o do a similar thing for an elderly relative, who despite their age, insisted on using bluetooth, whilst refusing to lean where to find bluetooth manager.

---

### Post by Jags_FL on 2011-03-14
@ flipper T

thanks for the reply, unfortunately my problem is not that he(this elderly person I'm helping here) cannot find the volume icon but whatever he does to mute sound, even raising/lowering volume won't do any good.

Few times I un-muted Master volume from terminal using "Alsamixer" and other times I did bunch of things that I even don't know what brought the sound back.

-- Another thing: Even after locking Gnome Panel(by gconf-editor > apps > panel > global > lockdown) somehow he managed to delete/remove volume icon, so now I've added Sound/Sound Preferences icon to the taskbar.

---

### Post by flipper T on 2011-03-14
hi

i think that unless you find out how the sound is being muted, either system wide or within an app, you are not going to resolve this.

ps just in case anyone thinks that there is an ageist undercurrent in my previous post, please note that my relative is in his 90's, likes nothing better than messing with his photos in gimp and thinks the proposed unity interface in 11.04 sucks. :)

---

### Post by mastablasta on 2011-03-14
what is the sound card? my sound card occasionally doesnt' turn on. updates messed up the sound again as it was working nicely before. 
 
Usually restarting computer works. Sometimes it's enough to do a 
sudo alsa reload
 
but not always.
 
usually i think it's after hibernating or suspend. plenty newer intel cards have this issue it seems.
 
it worked before the updates so yay for the updates - again. messed up the flash videos first and now sound.

---

