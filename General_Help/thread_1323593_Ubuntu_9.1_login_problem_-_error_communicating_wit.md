---
title: "Ubuntu 9.1 login problem - error communicating with authentication system"
date: 2009-11-11
forum: General Help
---

### Post by thinhhanh on 2009-11-11
I can no longer login into my Ubuntu system after adding a 2nd user. I had automatic login setup and I unchecked the setting to logon as the 2nd user. From there on, I always get this message at the login screen "error communicating with authentication system" no matter which user i choose.

Some thread I found suggest to undo the keypairing line in the /etc/pam.d file but I don't know how to get a terminal directly from boot. I installed Ubuntu as an [[COLOR=blue][COLOR=blue ! important][FONT=Verdana][COLOR=blue ! important][FONT=Verdana]application[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.linuxquestions.org/questions/#") from my Vista (dual boot).

Please help.
TIA,

---

### Post by bashphoenux on 2009-11-11
> **thinhhanh said:**
> .

Some thread I found suggest to undo the keypairing line in the /etc/pam.d file but I don't know how to get a terminal directly from boot.
TIA,

to go to terminal you need to change to virtual workspace by pressing ctrl+alt+F1/F2/F3/F4 
then login and make the changes you want to :)

---

### Post by glpunk on 2009-11-11
I'm having the same problem. Please post the solution if you found it. Thank you.

=(

---

### Post by thinhhanh on 2009-11-11
I fixed the problem, thanks guys!

1. Hitting <CTRL><ALT><F1> at the login screen got me out of the Xwindows to a text terminal.

2. edit the file /etc/pam.d/gdm to remove/uncomment the line
@include common-pamkeyring

---

### Post by glpunk on 2009-11-12
Thank you thinh, I resolved it in the same way.

To edit the file:

[B]sudo vi /etc/pam.d/gdm
[/B]
Press letter "i" to edit, erase the line "@include common-pamkeyring", to save: "shift+ZZ"

Done.

:popcorn:

---

