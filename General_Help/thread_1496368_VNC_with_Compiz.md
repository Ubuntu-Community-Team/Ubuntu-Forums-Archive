---
title: "VNC with Compiz"
date: 2010-05-29
forum: General Help
---

### Post by Daminator on 2010-05-29
Hello all,

I love Compiz, but I log into my machine remotely often using VNC from my other machines and over the internet. If I have compiz on my main machine, then VNC doesn't work.

I know that I can turn it on and off using the Compiz icon, but is there a way to just leav it on and have VNC work with it?

I believe FreeNX can work with Compiz, but I don't want to be logging into new sessions, I want to log into the currently active session.

Any ideas?

D

---

### Post by jpmorelli on 2010-06-01
I have this error and the solution is really simple, hope it works for you too. For me works perfect and is really simple.

1) Open a terminal o press ALT+F2, then run/type: gconf-editor

2) Go to /desktop/gnome/remote_access and enable "disable_xdamage"

I can believe the solution is so simple and why Ubuntu people left this unsolved.

Hope you make it work too like I do, regards from Argentina !!!

---

### Post by Niels Olson on 2010-06-06
Works for me! Awesome!

---

### Post by Daminator on 2010-06-06
That's unbelievable! Why on earth has this problem gone on for so long unfixed and why has no one else posted that answer anywhere. Seems to work perfectly! Thanks jpmorelli!!!

D

---

### Post by ktneely on 2010-06-07
That's amazing.  If it's not in an FAQ somewhere, it really should be.  Great job, and thanks for the help!

---

### Post by hoptimusPrime on 2010-06-16
thank you jpmorelli!
i can now use compiz and AWN with my VNC remote desktop viewer.  
connects perfectly using windows 7 and ubuntu
somebody tag this baby as SOLVED!

---

### Post by Boondoklife on 2010-06-17
> **hoptimusPrime said:**
> thank you jpmorelli!
i can now use compiz and AWN with my VNC remote desktop viewer.  
connects perfectly using windows 7 and ubuntu
somebody tag this baby as SOLVED!

Actually the issue is not solved, the key you changed just takes a full screen shot each time instead of just what needs to be updated. This results in a much higher network utilization than is needed for such a simple function.

---

### Post by hoptimusPrime on 2010-06-17
> **Boondoklife said:**
> Actually the issue is not solved, the key you changed just takes a full screen shot each time instead of just what needs to be updated. This results in a much higher network utilization than is needed for such a simple function.

oh really.  darn..  well it is still much better than static screen

maybe maverick will finally have a fix.

is it worth it for me to switch to metacity then?

---

### Post by Boondoklife on 2010-06-17
I personally don't bother with compiz myself, I think metacity works just fine and the vnc works fine with it.

---

### Post by hoptimusPrime on 2010-06-17
thanks Boondoklife__[]("http://ubuntuforums.org/member.php?u=826988")

---

### Post by tiosus on 2010-09-10
> **jpmorelli said:**
> I have this error and the solution is really simple, hope it works for you too. For me works perfect and is really simple.

1) Open a terminal o press ALT+F2, then run/type: gconf-editor

2) Go to /desktop/gnome/remote_access and enable "disable_xdamage"

I can believe the solution is so simple and why Ubuntu people left this unsolved.

Hope you make it work too like I do, regards from Argentina !!!
Works for me! Tanx

---

### Post by Marc van der Wijst on 2010-10-29
> **jpmorelli said:**
> I have this error and the solution is really simple, hope it works for you too. For me works perfect and is really simple.

1) Open a terminal o press ALT+F2, then run/type: gconf-editor

2) Go to /desktop/gnome/remote_access and enable "disable_xdamage"

I can believe the solution is so simple and why Ubuntu people left this unsolved.

Hope you make it work too like I do, regards from Argentina !!!

Works like a charm! Perfect! Many thanks.

:popcorn:

---

