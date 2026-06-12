---
title: "XOpenDisplay(NULL) fails when program run in boot sequence via rc.local"
date: 2012-05-09
forum: General Help
---

### Post by DAFlippers on 2012-05-09
[LEFT][COLOR=#000000]I have written a program that runs with ROOT permission in Terminal following login but fails when XOpenDisplay(NULL) call is made following reboot. The program is started up via rc.local but doesn't appear to be able to see X11.[/COLOR]
 
[COLOR=#000000]I need ROOT because I make LibUSB calls and these fail if not ROOT. I can see the program is running with ROOT permission but inspection of environment variables shows DISPLAY not set. I have a delay loop running and checks are made after user login and user can see DISPLAY set in environment variables but program cannot. If program is terminated and run in Terminal it works perfectly so the problem is that the program cannot interact with X11 when it is started and this state persists.[/COLOR]
 
[COLOR=#000000]I want the program to be up and running without user login.[/COLOR]
[COLOR=#000000][/COLOR] 
[COLOR=#000000]Can anyone let me know what I need to do?[/COLOR]
[COLOR=#000000][/COLOR] 
[COLOR=#000000]David[/COLOR][/LEFT]

---

