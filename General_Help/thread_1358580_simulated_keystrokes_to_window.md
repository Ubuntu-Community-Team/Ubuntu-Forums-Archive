---
title: "simulated keystrokes to window"
date: 2009-12-18
forum: General Help
---

### Post by nesro on 2009-12-18
Hello,
i wrote simple shell script to sending simulated keystrokes to windows. I use vkbd witch -text and -window. And my problem is that is working only on focused window. I need to work on something else and have my small window in corner with keystrokes in time interval. Is there any posibility how to set xvkbd to work in "background" or I need else application to this work? any ideas? Thank you very much..

(sorry my english)

---

### Post by StuartN on 2009-12-18
> **nesro said:**
> Is there any posibility how to set xvkbd to work in "background" or I need else application to this work? any ideas?

xdotool [http://www.semicomplete.com/projects/xdotool/](http://www.semicomplete.com/projects/xdotool/) will select a titled window, gain focus and send keystrokes to it.

---

### Post by nesro on 2009-12-19
but this is that problem. It must work "without" focus on window. My script is working like i want, but it takes focus from window iam working in.

this script I use and it takes me focus:

window="xxx"
window_id=`wmctrl -l | grep -i $window | awk '{print $1}'`
key[10]="\[F9]"
while [ 1 ]
do
    xvkbd -text ${key[10]} -window $window_id
    sleep 3
done

---

### Post by StuartN on 2009-12-19
> **nesro said:**
> but this is that problem. It must work "without" focus on window.

I think that I understand the problem - you want an automated input into one application, whilst you continue to work in another program. As far as I know, this is not possible because the window manager only has one input stream and that input stream is directed to the dialog that currently has the focus. A virtual keyboard must gain focus in the target dialog in order to send keystrokes, interrupting any other application. Maybe you could push the current focus, switch focus, send keystrokes and then pop the focus, but there is a risk that your own physical keystrokes will also be sent to the target dialog.

Can you have this task running as a separate log-in? Then you have two x-windows and two input streams.

---

