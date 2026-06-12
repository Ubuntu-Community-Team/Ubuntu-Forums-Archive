---
title: "Help with terminal window - ubuntu 10"
date: 2011-03-16
forum: General Help
---

### Post by janor on 2011-03-16
Hi
I'm new to ubuntu, I found this article about how to disable the password prompt in ubuntu, the method involves editing some commands in the terminal window, the problem is I don't know how to save the window after editing it, there's no save buttons or anything.
so I'll be grateful if someone told me how to save it...

---

### Post by kn0w-b1nary on 2011-03-16
if you mean remove password prompt for sudo, the commands are:
```
sudo visudo
```then change the line ```
%admin ALL=(ALL) ALL
``` to:
```
%admin ALL=(ALL) NOPASSWD:ALL
```
then hit "Control + x"
then hit "y"
there you go!

---

### Post by janor on 2011-03-16
> **kn0w-b1nary said:**
> if you mean remove password prompt for sudo, the commands are:
```
sudo visudo
```then change the line ```
%admin ALL=(ALL) ALL
``` to:
```
%admin ALL=(ALL) NOPASSWD:ALL
```there you go!

yes I know that code
but I can't save the file after writing this code!

---

### Post by kn0w-b1nary on 2011-03-16
I just edited my first post,

hit "Control + x"
then "y"

---

### Post by antaios256 on 2011-03-16
> **janor said:**
> yes I know that code
but I can't save the file after writing this code!


i understand wanting to remove the sudo password prompt as it is really annoying some days, but for the security aspect it would be recommended to leave it as is and regularly change the sudo password. 

so Im just curious on why you want to remove the password.  im not trying to make offense here just curious.

---

### Post by janor on 2011-03-16
> **kn0w-b1nary said:**
> I just edited my first post,

hit "Control + x"
then "y"

thanks a lot mate

---

### Post by r-senior on 2011-03-16
Do you have a bar at the bottom of the window that has entries like "^X Exit"?

If so, the '^' means the control key, so Control-X to exit. If you made changes it will prompt you whether you want to save. Press Y to save. Obviously.

---

### Post by janor on 2011-03-16
> **antaios256 said:**
> i understand wanting to remove the sudo password prompt as it is really annoying some days, but for the security aspect it would be recommended to leave it as is and regularly change the sudo password. 

so Im just curious on why you want to remove the password.  im not trying to make offense here just curious.

its just annoying to enter the pass every time I login, besides no one else uses the pc

---

### Post by kn0w-b1nary on 2011-03-16
> **janor said:**
> thanks a lot mate

You're welcome!

---

### Post by mcduck on 2011-03-16
> **janor said:**
> its just annoying to enter the pass every time I login, besides no one else uses the pc

You don't need to (and shouldn't!) remove the sudo password to log into desktop without a password. :D And actually doing that wouldn't even help you, you'd still need a password to log in to desktop. Editing that guide would allow you (or anybody who gets access to your computer, locally or through network) to do admin tasks without entering a password.

Automatic login can be enabled in System/Administration/Login Screen. :)

---

### Post by janor on 2011-03-16
> **mcduck said:**
> 
Automatic login can be enabled in System/Administration/Login Screen. :)

yes just found this...well thanks

---

### Post by kn0w-b1nary on 2011-03-16
I'd rather buy a fingerprint reader then disable sudo prompt, IMO. Just better security.

---

