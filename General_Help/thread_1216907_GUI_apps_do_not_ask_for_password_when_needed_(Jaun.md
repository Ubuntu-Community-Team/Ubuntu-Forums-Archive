---
title: "GUI apps do not ask for password when needed (Jaunty)"
date: 2009-07-18
forum: General Help
---

### Post by CaptainEvilStomper on 2009-07-18
For some reason, whenever any application needs root privileges, instead of asking for my password it freezes or nothing happens. For example, if I go to System > Administration > Users and Groups, then click unlock, the application freezes and I have to kill it. If I create a new network connection in the connection editor, then try to make it available for all users and click apply, nothing happens. Applications that ask for a password before running still work (for example, Startup Manager), but if at any time after that they need to ask for a password, I get nothing. What can I do to determine what's causing this and (hopefully) fix it?

---

### Post by CaptainEvilStomper on 2009-07-19
Update: I figured I could get around my problem in the short term by just running everything with gksudo - apparently not. Running "gksudo users-admin" doesn't work because everything is grayed out, including the unlock button, and "gksudo nm-connection-editor" works until I try to save any changes I make to a connection, at which point I get this error message:
```
PolicyKit authorization could not be created; invalid action ID.
```
How do I not have authorization to do something if I'm running it with root privileges? :confused:

---

### Post by CaptainEvilStomper on 2009-07-19
Update #2: I figured out what was causing the problem. Apparently these apps rely on PolicyKit to elevate my privileges and PolicyKit just hangs whenever it's called. I did some Googling and found out that the PolicyKit settings are stored in /etc/PolicyKit/PolicyKit.conf, so I added my user name to it and gave myself full access to everything, which made it so that whenever I tried to do anything that previously would require me to enter my password it would just do it without prompting me. Obviously that's a huge security issue, so I removed my user name and put all the settings back the way they were. Now my problem has apparently been solved somehow - the apps that were locking up before now work fine and ask me for my password again.

---

