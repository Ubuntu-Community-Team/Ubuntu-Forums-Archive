---
title: "Middle mouse button on Citrix application"
date: 2010-02-18
forum: General Help
---

### Post by Lars on 2010-02-18
Hi.

I'm having trouble getting my middle mousebutton (mousewheel) to work in a Citrix application.
It seems to do the usual Linux feature, which is to paste whatever text is currently marked.
But the application uses the middle mousebutton for something else, namely to pan maps/graphics.

I'm running Ubuntu 9.10 and have installed the latest Citrix Receiver software from the Citrix website.

I have to point out that the servers are running Windows and I have no control or access to them whatsoever, and that the login is web-based (which means that I don't setup a connection in the receiver config window)

I hope someone can help me on this one.. :)

/LarsG

---

### Post by Lars on 2010-02-25
The problem has been solved.

The solution is to open $HOME/.ICAClient/wfclient.ini
and find a line which says "MouseSendsControlV=True" -
change this to "False", and it should work. :)

/LarsG

---

