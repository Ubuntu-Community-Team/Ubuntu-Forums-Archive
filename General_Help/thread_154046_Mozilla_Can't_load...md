---
title: "Mozilla Can't load.."
date: 2006-04-02
forum: General Help
---

### Post by wcks48 on 2006-04-02
After install the Macromedia plug-in, i can't run my Mozilla. With the click on the icon, the mozilla picture just jumping beside the mouse pointer for a long time then disappear itself. even i can't find the executable file of Mozilla in /usr/bin/ and usr/lib/. i had tried to reinstall mozilla browser, firefox through Adept, but still the same situation there. 

when i tried to sign in as root to reinstall the mozilla firefox, i can't load the x-window with command: Startx. anyway, i still managed to install with the command line.

May i know any way to solve this problem?

---

### Post by hollywoodb on 2006-04-02
there is a difference between the mozilla suite and firefox, the mozilla browser package is "mozilla-browser" and firefox is "firefox" when using apt-get or adept.

whichever it is, try running 'mozilla' , 'firefox' , or 'mozilla-firefox' from konsole. It should give you some kind of error or clue as to why it is failing to run, which in turn will help you or others solve the problem.

Also, you don't need to sign in (login) as root to install applications with apt-get, just run "sudo apt-get install <appname>" from konsole, less hassle there.

---

