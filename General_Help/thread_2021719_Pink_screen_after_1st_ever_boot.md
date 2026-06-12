---
title: "Pink screen after 1st ever boot"
date: 2012-07-09
forum: General Help
---

### Post by taffy222 on 2012-07-09
Hi All. I am completely new to Ubuntu. I installed it onto my son's desktop - Acer Aspire T180-197Z AMD Sempron 3200+ processor with 80GB hard drive. I installed 12.04 and used the whole hard drive. I did not want Windows any more. The installation seemed to go well. Chose language, user name etc. Then removed the CD and rebooted for the first time. It only got as far as the pink screen. I can draw rectangles with the mouse and can create a 'New Folder' but that's all I can do. Have rebooted a couple more times and only the same. It does work via the Live CD though. Please go easy on me. I only know the basics of computing and this is the first time I have ever installed an OS. Really worried I have messed up his PC now. Please help.[SIZE=1][B]
[/B]

[/SIZE]

---

### Post by MG&amp;TL on 2012-07-09
If you can make a new folder, that's good. You haven't messed up, and it looks to be easily fixable. :) I suspect your graphics card might be causing problems with hardware acceleration for Ubuntu 3D.

Can you get to the login screen, or have you enabled automatic login?

[B]If you can:
[/B] 
1. Click the Ubuntu logo at the side of the username.

2. Select Ubuntu 2d.

3. Login. 

4. Report results back.

**If you can't:**

1. Press Ctrl-Alt-F1

2.Login at the text prompt (you can't see the password, just keep typing).

3. Type:

```
sudo service lightdm restart
```to restart the login screen. You'll need to enter your pass, again, you can't see it.

4. Use instructions for if you could use the login screen, ('if you can',  above).

---

### Post by taffy222 on 2012-07-13
Thanks MG&TL. I had onboard graphics and my daughter had a spare graphics card and inserted this, booted again and it works fine now. Thanks for your help.

---

### Post by dontyellpl0x on 2012-09-20
Hey guys, new to Ubuntu. I too have this problem. Although I can't do anything with my mouse or keyboard. 

i3 3220
ASUS P8B75-M
gtx 550ti

Any help would be greatly appreciated

---

### Post by dontyellpl0x on 2012-09-20
> **digithal said:**
> At install screen (when you boot from disk)  press F6 and select "nomodeset". This will disable KMS and resolve your  issue.

Ok, dont worry sorry guys. After searching more I found this and it fixed it

---

