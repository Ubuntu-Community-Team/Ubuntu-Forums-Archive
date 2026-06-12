---
title: "Ubuntu citrix time out"
date: 2011-04-28
forum: General Help
---

### Post by cotcot on 2011-04-28
Using ubuntu for a connection to my works server through citrix gives this message 

> Your session with the Web server has expired. You have been logged out. 

as soon as I open the web page and thus before I enter my credentials.
I get the message in the field of the webpage where I usually (on other computers) see that I have 2 minutes time to log in.

On another computer (also ubuntu) I can connect normally.

I do not know where to change this time.

Has anybody an idea about this ?

SOLVED : the URL from the destination was wrong (some kind of an automatic extention was not OK); 

A second problem occured with an error of not finding the application to open "launch.ica". This was solved by changing actions of citrix to "wfica" instead of "always ask" in firefox under Edit -> Preferences --> Applications.

---

