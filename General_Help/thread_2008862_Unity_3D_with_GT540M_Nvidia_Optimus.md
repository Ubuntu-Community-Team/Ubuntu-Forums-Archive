---
title: "Unity 3D with GT540M Nvidia Optimus"
date: 2012-06-23
forum: General Help
---

### Post by Zen_Jackal on 2012-06-23
Hi all,

I'm using an Acer Aspire Ethos 5951G with an Nvidia GT540M graphics chip. I've run 
```
sudo /usr/lib/unity_support_test -p
```

And it says "yes" for every entry on the list (including 3D support).

What can I do to get Unity 3D to actually appear on my login menu and work?

---

### Post by bogan on 2012-06-23
Hi!, **Zen-Jackal**,

In the 'greeter' login window, alongside your username, there should be a small Icon, a gear, an Ubuntu logo, or a Gnome logo. Clicking the Mouse on that should give you a drop-dowm menu.

Is that what you referred to as "my login menu" ?

If so, 'Unity 3d' is listed as: "Ubuntu", and Unity 2d is listed as "Ubuntu 2d".

Click on "Ubuntu" and enter your Password and unity3d should show your Desktop.

If you are in doubt, in a Terminal enter:```
echo $DESKTOP_SESSION
```It will tell you which type is running.

If it does not do so, please Post the actual output of the unity_support_test, and/or ```
sudo lspci -nnk | grep -iA2 VGA
```Chao!, **bogan**.

---

