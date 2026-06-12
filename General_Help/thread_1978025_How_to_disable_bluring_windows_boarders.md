---
title: "How to disable bluring windows boarders?"
date: 2012-05-11
forum: General Help
---

### Post by faizlo on 2012-05-11
Hi,

I was trying to try compiz and its effects. Well, I did not like it, and I decided I should remove it (erased it completely.) but I was left with a little (but very annoying to me) effect - a bluring windows' boarders which is really making me sad and I cannot get rid of this effect.
I tried to install compizconfig_settings_manager to make sure that all effects are unchecked and they were, yet I still have these bluring boarders.
I am using an Ubuntu 11.10 Core i5 Acer laptop.

Can you please help me get rid of them. I really cannot stand them.

thanks in advance

---

### Post by faizlo on 2012-05-11
Hi again,

I have also tried to find apps/gwd in my gconf-editor menus, but I could not find gwd under apps!
What am I missing exactly?

ur help is appreciated guys

---

### Post by wilee-nilee on 2012-05-11
The unity desktop is a plugin in compiz. If you are using gnome 3 it does not use compiz.

So what release are you using and what desktop, as of now there are 4 releases and at least 4 different versions and multiple desktops that all can use, some details would help and a screen shot of what you see.

---

### Post by faizlo on 2012-05-11
As I said, I am using Ubuntu 11.10 updated to the latest (last update few min. ago) and I am using it on a laptop (Acer Core i5)

---

### Post by wilee-nilee on 2012-05-11
> **faizlo said:**
> As I said, I am using Ubuntu 11.10 updated to the latest (last update few min. ago) and I am using it on a laptop (Acer Core i5)

Okay granted I missed that but is it the unity desktop, the gnome-shell, or the fallback. My guess is the fallback as if you removed unity you would have very little of that desktop.

Hmm no answer to the desktop and no screenshot.

You have to understand that details are important, some key ones are missing at least for me to help.

---

### Post by faizlo on 2012-05-11
OKz

I will try again.
I am using the fallback version. But I have not removed unity from the list of installed packages. It is still installed but I used (no effects.)
When I took a screenshot the pic was not clear. I can say that windows boarders have a blurring shadow that is almost .5 cm in width (from the boarders of the window and out)

hope this helps

---

### Post by wilee-nilee on 2012-05-11
> **faizlo said:**
> OKz

I will try again.
I am using the fallback version. But I have not removed unity from the list of installed packages. It is still installed but I used (no effects.)
When I took a screenshot the pic was not clear. I can say that windows boarders have a blurring shadow that is almost .5 cm in width (from the boarders of the window and out)

hope this helps

Look for screenshot in the apps, or hit the prtsc key.

---

### Post by faizlo on 2012-05-11
One thing I have noticed also is that when I move an icon on my desktop it leaves a blurred trace along its path, and then it disappears.
I hope this may help identify the problem.

---

### Post by wilee-nilee on 2012-05-11
> **faizlo said:**
> One thing I have noticed also is that when I move an icon on my desktop it leaves a blurred trace along its path, and then it disappears.
I hope this may help identify the problem.

Go to users and make another account and see if this is the same there.

Run this command and post the results as well.

```
  [FONT=Verdana, sans-serif][SIZE=1]lspci | grep VGA[/SIZE][/FONT]
  
```

---

### Post by faizlo on 2012-05-11
I could add a screenshot to my previous response, hope this will make it easier to identify the problem.

---

### Post by wilee-nilee on 2012-05-11
> **faizlo said:**
> I could add a screenshot to my previous response, hope this will make it easier to identify the problem.


Hmm, looks good to me, I can't really tell what you're referring to. Is it the shadow around the authentication?

---

### Post by faizlo on 2012-05-11
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
```
And yes, it is that shadow.

---

