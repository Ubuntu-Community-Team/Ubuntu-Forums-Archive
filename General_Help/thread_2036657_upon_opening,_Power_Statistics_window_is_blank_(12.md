---
title: "upon opening, Power Statistics window is blank (12.04)"
date: 2012-08-02
forum: General Help
---

### Post by haplorrhine on 2012-08-02
Upon opening, the window titled "power statistics - device history" is blank.
In the terminal, *gnome-power-statistics* doesn't result in any output.

I've realized that this problem does not occur after a fresh login, so logging out and logging back in fixes it.

Various programs seem to trigger this problem (GIMP, Firefox, Dillo).
Scratch that.  It's only loading upon the first attempt, but it never loads on the second attempt.

---

### Post by ramsharan065 on 2012-08-15
If you don't want to have blank window,
[LIST=1]
[*]Do not close gnome power statistics using cross(X) at the top.
[*]Use close button at the bottom to close the application.
[/LIST]

If you have already blank window and want to have the application running appropriately then
[LIST=1]
[*]Open terminal (in ubuntu Ctl +Alt + T).
[*]Type command: ps -A | grep gnome-power.
[*]You will get process with gnome-power-sta.
[*]Note its PID at the left side. In my case its pid is 5051.
[*]Then type command:kill pidValue . In my case : kill 5051.
[/LIST]

Now you can re-open gnome-power-statistics and look the statistics without logout and login.

---

### Post by ramsharan065 on 2012-09-06
You can also look at this link for the solution    
[https://www.youtube.com/watch?v=KyhZVDwuRTA&feature=plcp](https://www.youtube.com/watch?v=KyhZVDwuRTA&feature=plcp)

---

