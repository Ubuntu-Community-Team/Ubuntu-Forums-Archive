---
title: "terminal server client &gt; host key ???"
date: 2011-04-08
forum: General Help
---

### Post by dgoosens on 2011-04-08
hi ubunteros,

I wonder... Is there some kind of Host key like there is one in Vbox for the "Terminal Server Client" ?
I hate to have to grab my mouse every time I need to switch to another app. outside of the terminal...

It seems so obvious to me that I can not imagine this functionality does not exist...
If it does not exist, could you point me to some other rdesktop front-end that would have this ???

Thanks a lot in advance !
dGo

---

### Post by Quintilian on 2011-04-08
what are you trying to do? and are you talking about when you are remote desktoping in fullscreen mode?

if so a simple Ctrl+Alt+Enter will bring the fullscreen remote desktop into a window. 
reviewing your question again i thing what you want is to check the box that says "Enable window manager's key bindings" on the Performance tab of Terminal Server Client, or add a -K if you're starting it from the terminal. this will send your Alt+Tab to your desktop instead of your remote terminal. Although this is kind of an either-or situation. What you could do is change either your local computer or your remote computer to switch programs on something other than Alt-Tab so that you could use it in both locations.
is that what you mean?

---

### Post by dgoosens on 2011-04-08
hi Quintilian,

Thanks for your reply.

No... What I am looking for is not exactly that.

In Virtual box, when in a virtual machine (VM), you have full control over it... This means, all the keystrokes go to the VM.

This, unless you hit the right CTRL key. Then your keystrokes are for the host machine (hence, the "host-key").

Thus, what I am trying to find is a way to leave the remote desktop terminal without having to click outside of it and without logging out.

(Full-screen mode has nothing to do here... Except that it proves it is possible to interact with the host machine while working within the terminal.)

Any ideas ?

---

### Post by Quintilian on 2011-04-08
No problem
sorry, that's as much as i know

---

