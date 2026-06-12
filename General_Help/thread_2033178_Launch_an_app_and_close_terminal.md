---
title: "Launch an app and close terminal"
date: 2012-07-25
forum: General Help
---

### Post by allg33k on 2012-07-25
I haven't used Ubuntu since 10.something.  None-the-less I use a program called gnome-rdp for terminal sessions to my windows servers.  I used to have the program start up in the top panel next to the clock.  Then I could just right click on it and see all of my saved sessions.  I can't figure out how to do that now that there is this new unity feature.  

I can still launch the app by opening terminal and typing gnome-rdp.  However then I have a terminal session left open.  I don't remember how to launch the program and not have the terminal session on the screen.  

So basically I guess I am asking two questions.  How do I make a launcher for the gnome-rdp program and how do I start it without the terminal session staying open.  

I'm thinking I may have used some sort of script to do this in the past, but honestly I totally don't remember.

---

### Post by ajgreeny on 2012-07-25
```
*command* & exit
```will do that.

---

### Post by allg33k on 2012-07-25
That definitely worked.  Thanks!  However any idea how to pin it up by the clock?

---

### Post by BoogeyOfTheMan on 2012-07-25
If its a tray icon, go into the dconf editor, go to desktop > unity > panel and add it to the exceptions, or just add "all".

Better detailed instructions: [http://ubuntugenius.wordpress.com/2011/06/25/ubuntu-11-04-fix-show-all-iconsindicators-in-unity-panels-notification-area/](http://ubuntugenius.wordpress.com/2011/06/25/ubuntu-11-04-fix-show-all-iconsindicators-in-unity-panels-notification-area/)

---

