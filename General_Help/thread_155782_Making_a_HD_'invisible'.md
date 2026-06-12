---
title: "Making a HD 'invisible'?"
date: 2006-04-05
forum: General Help
---

### Post by NeghVar on 2006-04-05
Ok, heres the situation:

I have a second HD here that is automounted, it contains various back ups of files and folders I can't loose as well as other data and such. I want to make it completely invisible to anyone else who signs on here except root and me ofcourse. Is there some description of permision or such that would make it so that if I logged in with another user that I won't even know the drive exists?

I don't want to have to remount it everytime that I need to use it as it holds all my mp3s as well as other files that I use throughout the day but I don't want anyone else to even know it exists. My main concern is no matter how protected it is if they can see it there is the slightest of chances they can nuke it, I'm a very paranoid person incase you havn't noticed.

Thanks for any potential ideas.

---

### Post by renzokuken on 2006-04-05
could always just put a dot infront of the filename and mount it in an obscure place, thats what i do

e.g. my hdb1 partition is mounted at  /media/.storage

files with a dot dont show up in nautilus unless you press ctrl+H

---

### Post by taurus on 2006-04-05
Or just change the permissions to something like

-rwxr-x---  root  backup  /media/mp3

Then, add yourself to group backup and nobody else...

---

### Post by NeghVar on 2006-04-05
thanks, ill try changing the permissions

---

