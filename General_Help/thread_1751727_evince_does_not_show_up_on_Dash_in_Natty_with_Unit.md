---
title: "evince does not show up on Dash in Natty with Unity"
date: 2011-05-07
forum: General Help
---

### Post by chandra on 2011-05-07
I have just done a fresh install of Natty with Unity on an AMD 64 desktop.

When I open the Dash by clicking on the Ubuntu icon at the top left and type in evince, I do not get any icon or response.

When I type in evince after Alt-F2 I get an evince window.

Is this behaviour correct? Is it the default behaviour? Is it possible to add the evince icon to the Launcher? If so, from where do I do it?

Thanks.

---

### Post by chandra on 2011-05-07
I will answer my own question here. From the discussion at:

[http://askubuntu.com/questions/38684/why-doesnt-document-viewer-appear-in-the-dash-as-an-installed-application](http://askubuntu.com/questions/38684/why-doesnt-document-viewer-appear-in-the-dash-as-an-installed-application)

it appears that whether or not an application shows up on Dash is a design choice. Just as the Main Menu could be edited in Ubuntu Classic to allow display of installed but hidden applications, the same can be done as this quote from Lorem at the above link explains:

> You need to enable "evince" (or any other applications) in menu to search for it in dash. To do so you have to execute "alacarte", search the program you want and enable it, then logout. When you came back the application is searchable in dash.

The upshot is that any installed invisible application may be rendered visible by invoking 

Alt-F2 alacarte

and checking its box, logging out, and logging in again.

[Edit: Alternatively, use Dash -> Main Menu and checking its box, logging out, and logging in again.]

This gives comfort to those who are used to opening evince with no file to act upon. However, it appears that if an application is invisible, one should review one's habit of invoking it.

Since gedit may be started meaningfully with an "untitled file" to edit, it shows up on Dash. Since evince with no file to open is not much use, it is rendered not visible in Dash. It seems to make sense :)

---

