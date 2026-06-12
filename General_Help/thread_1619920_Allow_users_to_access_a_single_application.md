---
title: "Allow users to access a single application"
date: 2010-11-12
forum: General Help
---

### Post by awp2513_ on 2010-11-12
Hi,

I have a windowed java application that requires the use of IMEs to allow users to enter Asian characters. From what I've seen so far, SCIM and IBUS require Gnome to run, which means I need to start gnome and then start my java application in order to get the functionality that I want.

However, I also have the requirement that users cannot root around the system. I would like to make it so that only my java application is available to the user. More specifically, when they turn the computer on, I want the user to be automatically logged into an account and have my application appear full screen. From here, I would like to prevent the user from accessing the desktop and any applications on the system (terminal).

Is what I would like to do possible without starting the system in text mode ("headless server?") and starting the java application (xinit....)? Is there a way to use IBUS, SCIM, or some other IME without starting Gnome?

Thanks, in advance,

---

