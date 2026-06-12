---
title: "Help!  I can't Remove an app"
date: 2011-06-05
forum: General Help
---

### Post by Max-Tyson on 2011-06-05
Help Me! I am trying to remove the application sandboxgamemaker and have been using the command: sudo apt-get remove sandboxgamemaker
But I keep getting an error message

[IMG]https://1059339755729925169-a-1802744773732722657-s-sites.googlegroups.com/site/maxthelinuxuser/updates/errormessages/help2.png?attachauth=ANoY7co1KB8_eKFg968upFvxhMNkeUNbRBNlucC6-6FmBRzRmAYCM6SLp33MkgQgJ_LNpnthJYTB6uF9c2hlYXVt2JqdBGhnOtGgkiWAcHoTqBV_Ls9lzcT4tllPEftfxos0rGu4zpn1o7lyvyOVjt_N4e77y9bMzj77ZwUt69hkNS1P6OB-kIWd341ZFGwEvb1H1pPSWC4RBEsa8bqD_43qaOYoUj1U3nqFAgd9XpBrUVTgh-8haW0%3D&attredirects=0[/IMG]

Does anyone have an idea as to what I should do?

---

### Post by IWantFroyo on 2011-06-05
Your picture is not up.

Try:
```
sudo apt-get remove --purge sandboxgamemaker
```

---

### Post by Max-Tyson on 2011-06-05
I got ther error message :

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

What's this mean?

---

### Post by IWantFroyo on 2011-06-05
I think it means you killed a process while it was installing a program.
Copy and paste this into your terminal:
```
sudo dpkg --configure -a
```

---

