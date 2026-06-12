---
title: "Automatic HTML/Javascript Login"
date: 2010-10-11
forum: General Help
---

### Post by embolalia1187 on 2010-10-11
Basically, after a certain amount of time (which I haven't been able to narrow down), the network in my dorm locks you out. You have to open a web browser and enter your login information. It's a mild inconvenience, since it's usually just when you first open a browser in the morning, but it can get to be really obnoxious. (This is especially true for app tabs in FF4 and Chrome, which try to load automatically, but just get the login page, so you have to go through them all and reload them. MythTV also has a script to fill its listings database, which fails when it can't reach the server, but doesn't give any notice on the screen.)

As best I can tell, when you request a page (and aren't logged in), it redirects you to the login page. It's a simple login with JavaScript and HTML (just looking at what's visible of the source code.). When you login, it sends you to a confirmation page, and opens the page you had requested.

Is there a way to write a script, which could run before Firefox, which would "sense" if it got redirected, log in, and then launch Firefox?

---

