---
title: "Problem with the notification box."
date: 2012-06-27
forum: General Help
---

### Post by UAdnan on 2012-06-27
Hello,

Basically, I had installed Ubuntu 12.04 on my Netbook, but after some testing, I found that Unity - which I really like - is taking much resources from my low-end computer, so I decided to install a lighter desktop environment, and after testing many of them, I found that Xubuntu is the ideal one for now.
But I have a problem with the notification box (Which by default appears on the top-right area of the screen)... I don't really know how to explain the problem, so I provided a screen-shot:

[http://sournoishack.com/uploads/699722099Xubuntu_Error.png](http://sournoishack.com/uploads/699722099Xubuntu_Error.png)

I tried every theme, and tried to change the opacity but it keeps looking like that, 100% opaque and with a black rectangle, which is quite ugly.

How can I fix this ?
Thanks in advance,
UAdnan.

---

### Post by zombifier25 on 2012-06-27
Notify OSD need a compositing-able windows manager to work (like Compiz) Xfwm does not support compositing, so it'll look ugly.

When you install Xfce, you should already have xfce4-notifyd installed (which looks better on non-composited environment) If not, install it.

---

### Post by UAdnan on 2012-06-27
I just typed < sudo apt-get install  xfce4-notifyd > in the Terminal but it's telling that it's already the newest version. . . ?

---

### Post by wheeze on 2012-06-27
> **zombifier25 said:**
> Xfwm does not support compositing,

I'll have to disagree with that statement.

You can enable compositing in the Window Manager Tweaks applet. (I think that's what it's called. Not currently running an Xfce setup to verify)

---

### Post by holycow131415 on 2012-06-27
> **wheeze said:**
> I'll have to disagree with that statement.

You can enable compositing in the Window Manager Tweaks applet. (I think that's what it's called. Not currently running an Xfce setup to verify)
 
Yep, you can turn it on through that. Its in the settings, and the control panel like area.

---

### Post by wkrekik on 2012-06-27
> **wheeze said:**
> I'll have to disagree with that statement.

You can enable compositing in the Window Manager Tweaks applet. (I think that's what it's called. Not currently running an Xfce setup to verify)
And unlike compiz, xfce compositing is very light on resources.

---

### Post by wkrekik on 2012-06-27
After seeing the screenshot I think that your problem is not a compositing one but arose from a mix of unity/xfce notification tools. You should uninstall unity/ubuntu notification to get the xfce/xubuntu one working.
Sorry for my bad english

---

### Post by UAdnan on 2012-06-27
This is my third edit to my post (hopefully no-one read anything before), so after going to Window Manager Tweaks, which I believe you were referring me to, I got rid of that ugly stuff, and now the notification looks better. But isn't it a little odd that all the themes are the same as well as the default position ? (Whatever is the position I choose, it always appear in the top right corner as by default)

---

### Post by wkrekik on 2012-06-27
> But isn't it a little odd that all the themes are the same as well as the default position 
That is why I said that it's not simply a compositing problem. Your system is using a non xfce notification tool. I have had the same problem when I installed unity in Xubuntu and solved it by uninstalling the unity/ubuntu notification system (I forgot what package it was)

---

### Post by UAdnan on 2012-06-27
> **wkrekik said:**
> That is why I said that it's not simply a compositing problem. Your system is using a non xfce notification tool. I have had the same problem when I installed unity in Xubuntu and solved it by uninstalling the unity/ubuntu notification system (I forgot what package it was)

And would you please tell me how to uninstall the Ubuntu notification system ?!

Thank you for your support.

Edit: Alright, alright ! I found out how to do that, thanks for helping me to solve my problem ! 

And I should also thank these two links that helped me getting through solving the last problem, but of course I wouldn't get to that without the help of wkrekik.

[http://askubuntu.com/questions/6302/how-can-you-remove-unity](http://askubuntu.com/questions/6302/how-can-you-remove-unity)
Well, I couldn't find the second link, which provides how to remove the notifyOSD, I will provide it upon request.

Case closed. :)

---

