---
title: "Can't enter in password"
date: 2010-08-28
forum: General Help
---

### Post by Eller200 on 2010-08-28
Ok, I have a 64 bit version I have install the os from the CD that I had requested.
When I had finish I remove the disk like it told me too then restarted.  Then is requested a user name I had already made a user when installing  the os so I type in the user name then asked for a password I couldn't  type in a password all I could do is press enter [button]("http://ubuntuforums.org/showthread.php?p=9778303#"). Please Help, Thanks to who ever helps me

Ubuntu Server Edition 10.04 LTS
64 bit os

---

### Post by Eller200 on 2010-08-28
Can somebody reply

---

### Post by mr clark25 on 2010-08-28
a very good question...

can you hit the "leave note for user" option and type there?  have you tried a different keyboard? is it a usb keyboard or a ps/2 keyboard?

even if your answers dont help me, they may help someone else.



BTW, please wait a little longer before bumping your post.

---

### Post by Eller200 on 2010-08-28
> **mr clark25 said:**
> a very good question...

can you hit the "leave note for user" option and type there?  have you tried a different keyboard? is it a usb keyboard or a ps/2 keyboard?

even if your answers dont help me, they may help someone else.



BTW, please wait a little longer before bumping your post.

nope, I tried

---

### Post by MooPi on 2010-08-28
The user should already be  visible and you shouldn't have to type a name in. Use your mouse to highlight the user then type your password. If this doesn't work there is an alternate solution.
Okay I missed the server edition, your user will need to be typed. I suggest you reboot and after the bios splash but before your system prompt depress the shift key to access the recovery console. Choose root console/prompt. At the prompt type:
```
passwd your_user_name
```
You are going to be asked for the new UNIX password. Type in a new password then reboot to test and use the new password.

---

### Post by Eller200 on 2010-08-28
> **MooPi said:**
> The user should already be  visible and you shouldn't have to type a name in. Use your mouse to highlight the user then type your password. If this doesn't work there is an alternate solution.
Okay I missed the server edition, your user will need to be typed. I suggest you reboot and after the bios splash but before your system prompt depress the shift key to access the recovery console. Choose root console/prompt. At the prompt type:
```
passwd your_user_name
```You are going to be asked for the new UNIX password. Type in a new password then reboot to test and use the new password.

I can't it can't even type in the current password nor the new neither the sign in area

---

### Post by MooPi on 2010-08-28
Were you able to enter the recovery console ?

---

### Post by mobilediesel on 2010-08-28
> **Eller200 said:**
> Ok, I have a 64 bit version I have install the os from the CD that I had requested.
When I had finish I remove the disk like it told me too then restarted.  Then is requested a user name I had already made a user when installing  the os so I type in the user name then asked for a password I couldn't  type in a password all I could do is press enter [button]("http://ubuntuforums.org/showthread.php?p=9778303#"). Please Help, Thanks to who ever helps me

Ubuntu Server Edition 10.04 LTS
64 bit os

Do you mean that when you try to type the password that you don't see any text? If it's in the console/terminal, you won't see any characters while typing a password.

---

### Post by mr clark25 on 2010-08-28
> **mobilediesel said:**
> Do you mean that when you try to type the password that you don't see any text? If it's in the console/terminal, you won't see any characters while typing a password.

very good point. just type your password and hit enter.




@mobilediesel- your website still looks a lot better than [my website]("http://mrclark.ath.cx/linux")...

---

### Post by aysiu on 2010-08-29
The server edition has no graphical interface, so it's definitely not going to give you any visual feedback when you enter your password. Just enter the password and hit Enter. It'll work.

This is a usability bug that will probably never be fixed. More details here:
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

