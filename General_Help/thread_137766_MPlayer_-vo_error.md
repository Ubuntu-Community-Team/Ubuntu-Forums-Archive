---
title: "MPlayer -vo error"
date: 2006-02-28
forum: General Help
---

### Post by rohan! on 2006-02-28
I get "Error opening/initializing the selected video_out (-vo) device" messages when i try and play things in mplayer.

I have had it playing dvd's just last week, and am sure that I haven't changed anything.

Any suggestions??

on a positive note... am really having a great time on linux since i moved earlier this month!

---

### Post by rattking on 2006-02-28
Hi
I am not sure what caused that to change..
this may help
mplayer -vo help
will list all video outputs
find one that works well.. I use xv
then to make it default in mplayers config
gedit ~/.mplayer/config
add the line
vo=xv
or whatever -vo you choose
save that file then your good to go

---

### Post by rohan! on 2006-02-28
am i not supposed to be editing /etc/mplayer/mplayer.conf ??

will tried your way first... it didn't work, so i tried editing etc/mplayer/mplayer.conf. that didn't work either.

am going to try completely uninstalling (erasing config files and everything) and starting again from scratch...

mnugh!! it's still not working!! wot have i done??

Ok will keep on going...

---

### Post by rohan! on 2006-02-28
don't know what i did but it's working again!! and visually better than it did before which is nice (was really sketchy image before) -- audio is abit jumpy.
something is really bizarre with this.

i deleted /etc/mplayer/mplayer.conf_backup and reopened mplayer, pressed play dvd and it worked! i don't understand, but am happy.

thanks for support. only wish that i understood why things weren;t working and why they are now. strange.

---

