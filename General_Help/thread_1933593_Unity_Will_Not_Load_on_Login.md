---
title: "Unity Will Not Load on Login"
date: 2012-02-29
forum: General Help
---

### Post by sideffects on 2012-02-29
I have been just fine with my Ubuntu 11.10 install until today. I have it set to automatic login. It loads to a purple backdrop, and it asks for my keyring password. I can also see a network notification popup in the top right corner, but that's it. If I enter my keyring password, nothing happens, the screen just sits there. Is there a way I can manually change my settings to not login automatically so I can try to boot into gnome and see if this is the issue? Has anyone has this problem before?

---

### Post by Krytarik on 2012-02-29
Please see this troubleshooting guide:

[http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html](http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html)

Regards.

---

### Post by raja.genupula on 2012-02-29
> I can manually change my settings to not login automatically 
go user account settings from system settings & select your user name and OFF the automatic  login Switch .

All the best and please try that above trouble shoot guide also . 

Let us know what you got .

---

### Post by Krytarik on 2012-03-01
> **raja.genupula said:**
> go user account settings from system settings & select your user name and OFF the automatic  login Switch .
Yeah, that would work if the OP would actually have a panel to click on. ;-)

---

### Post by raja.genupula on 2012-03-01
> **Krytarik said:**
> Yeah, that would work if the OP would actually have a panel to click on. ;-)

Yeah .... oops i miss it . thanks for reporting .

---

### Post by Tiganjero on 2012-03-01
Press ***Alt+F2***, enter ***terminal*** and click run. Paste ***sudo gedit /etc/lightdm/lightdm.conf*** into the terminal and press enter. This will bring up the config file where you can ***manually*** turn off auto login. *_You don't have to use gedit_*, you can use nano, or which-ever text editor you prefer. Hope this helps!

Cheers,
George

---

