---
title: "Startup Problem"
date: 2010-08-04
forum: General Help
---

### Post by Noorani on 2010-08-04
I recently just updated my Uubuntu Lucid and started having problems.
As soon as I log on the desktop does not appear. I see my wallpaper(it is the same as the login screen background) but there are no panels and nothing works. I cannot right click also. All I can do is Ctrl+Alt+Del and then click on Shutdown, Restart, Suspend or Hibernate. I went to the Grub menu and booted using an older kernel as well as booting in recovery mode. None of them worked.
Could anyone please help.
Thanks!

---

### Post by sydbat on 2010-08-04
> **Noorani said:**
> I recently just updated my Uubuntu Lucid and started having problems.
As soon as I log on the desktop does not appear. I see my wallpaper(it is the same as the login screen background) but there are no panels and nothing works. I cannot right click also. All I can do is Ctrl+Alt+Del and then click on Shutdown, Restart, Suspend or Hibernate. I went to the Grub menu and booted using an older kernel as well as booting in recovery mode. None of them worked.
Could anyone please help.
Thanks!Try this - when booting, go into the recovery mode (should be one down from the regular kernel). If GRUB menu is hidden, press Esc to enter the GRUB menu.

Once in the recovery area, there are options to fix various things. Try fixing the x server and then dpkg. Might resolve your issues.

---

### Post by utilitytrack on 2010-08-04
to **Noorani**

go to into console (Ctrl-Alt-F1) and login. After type it:


```
gnome-session --display=:0.0
```

---

### Post by Noorani on 2010-08-04
I tried the FailsafeX option after using recovery mode but it didn't help. the same thing happened
When I used dpkg I got so many lines of something like:
Failed to fetch...URL...

I also went to the console and typed the code :
gnome-session --display=:0.0   but got an error messagesaying 'No protocol specified. WARNING **: Cannot open display: :0.0

---

### Post by utilitytrack on 2010-08-04
Hmm, "Cannot open display" message mean that Xserver don't run or it's run on other VT than VT7. Or do you sure that it's run properly? This can be easy check:
```
$ ps -AHF | grep X
```

Ok, I think that reinstall your GNOME DE is more simple, though:
```
# aptitude reinstall gnome-desktop-environment
```


good luck!

---

