---
title: "Dual Boot Default OS issue"
date: 2011-05-09
forum: General Help
---

### Post by thalo on 2011-05-09
I recently updated to 11.04, with WinVista dual boot.  With previous updates I have set my default OS at the grub boot screen to Win.  I go through the Startup Manager to set the default OS.

I have done so recently, with the 11.04 update, but it still defaults to 11.04.  I have run grub update, through the 11.04 recovery (it gives a window with many options, one is to update grub) and through a terminal window (sudo update-grub).

any thing else I need to do to make things happen?

---

### Post by stber321 on 2011-05-09
> **thalo said:**
> I recently updated to 11.04, with WinVista dual boot.  With previous updates I have set my default OS at the grub boot screen to Win.  I go through the Startup Manager to set the default OS.

I have done so recently, with the 11.04 update, but it still defaults to 11.04.  I have run grub update, through the 11.04 recovery (it gives a window with many options, one is to update grub) and through a terminal window (sudo update grub (I know this is not 100% correct, but I used the correct command)).

any thing else I need to do to make things happen?

what  do you mean, what is your probilem, if the startup manager is not working then open /etc/grub.conf as root and change ```
default=0
```to the number of the OS you want in order of appearance in the grub menu (obviously like most options the list starts at zero), save it, then run sudo update grub... one question do you rely want to give away your freedom [COLOR=RoyalBlue][http://en.windows7sins.org/](http://en.windows7sins.org/) [http://www.fsf.org/about/what-is-free-software](http://www.fsf.org/about/what-is-free-software)[/COLOR]

---

### Post by oldfred on 2011-05-09
With Natty & grub 1.99, grub has  a lot of changes. I thing some of the gui tools that made it easy to change things are not up to speed just yet.

I would try to old school manual way.

You can use a number for grub default or this:

But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find your windows entry in grub.cfg and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default line here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new line:
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

### Post by thalo on 2011-05-11
> **oldfred said:**
> With Natty & grub 1.99, grub has  a lot of changes. I thing some of the gui tools that made it easy to change things are not up to speed just yet.

I would try to old school manual way.

You can use a number for grub default or this:

But Grub 2 also lets you use the title. Suppose your Windows title is "Windows Vista (on /dev/sda1)". Then you can use in /etc/grub/default, and you won't have to edit Grub after kernel updates.

find your windows entry in grub.cfg and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default line here:
gksudo gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new line:
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

If I go into /etc/default/grub and edit DEFAULT=0, then I add ```
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)
```
to the same file or /boot/grub/grub.cfg?

right now it shows GRUB_DEFAULT=6

---

### Post by thalo on 2011-05-11
oldfred, thanks for your help.  i got it all figured out.  to reiterate:

1.  use gedit /boot/grub/grub.cfg to find out exactly how the string is shown for where you want your default to be.  I just copied what you had written, but mine shows "Windows Vista (loader) (on /dev/sda1)".  initially it didnt work, then i understood, added the extra bit and it is fine.

2.  use sudo gedit /etc/default/grub to edit the GRUB_DEFAULT=X with the code you showed.  make sure to # (comment out) or remove the previously existing default line.

3.  run sudo update-grub to update.

cheers

---

### Post by drs305 on 2011-05-11
Glad you have it working the way you want. I'll just add this caveat for others that may want to use a title in the GRUB_DEFAULT= setting.

The normal (pre-Natty) methods of using the number or title as the GRUB_DEFAULT still works in Natty, but there are two restrictions:
[LIST]
[*]The entry must be on the main menu (i.e. not in a submenu).
[*]When counting entries to come up with a number, include any 'submenu' title entry such as 'Previous linux versions'  on the main page (but not menuentries within the submenu that do not appear on the main Grub 2 menu).
[/LIST]

If you want to use a title for a kernel within a submenu, the way to designate it is different. Refer to this thread for more information on submenus:
[Grub 1.99 Submenus]("http://ubuntuforums.org/showthread.php?p=10720316")

---

