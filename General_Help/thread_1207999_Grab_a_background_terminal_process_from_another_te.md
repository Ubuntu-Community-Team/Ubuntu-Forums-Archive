---
title: "Grab a background terminal process from another terminal"
date: 2009-07-08
forum: General Help
---

### Post by littlespy on 2009-07-08
I run fuppes as a upnp media server and often I start it in the background via Alt+F2 so I don't have the terminal window cloging up the desktop (it's my main computer).

There are people around the house constantly watching movies off it and often times I want to run commands in the fuppes terminal program to update the filedb etc.

Is it possbile to grab a process already running in the background from a new terminal window, with the pid or something similar?  So that it will not close the program effectively disconnecting people using the server.

---

### Post by hibliss on 2009-07-13
Seems like Screen is the answer to your problem -- [http://ubuntu-tutorials.com/2007/05/04/command-line-multitasking-with-screen/]("http://ubuntu-tutorials.com/2007/05/04/command-line-multitasking-with-screen/")

Screen lets you run several virtual terminal windows within one, like tabbed browsing. It is very powerful once you get used to it, and I use it to run FUPPES and rtorrent in the same terminal window (though a better solution for you would just be to put it in another workspace in Gnome).
[B]
[Here]("http://www.cyberciti.biz/tips/how-to-use-screen-command-under-linux.html")[/B] is a decent quick explanation of screen.

Gnome allows up to 64 virtual workspaces, and I generally use either 4 or 8 (8 one my Eee PC due to lack of screen real estate, 4 on my desktop with a larger monitor). You may already use this, but setting up a separate workspace for FUPPES is another decent option, just move it over there, and if you need to update the database quickly, just hit ctrl+alt right and jump to that window. **[Here]("http://library.gnome.org/users/user-guide/stable/overview-workspaces.html.en")** is a guide on how to manage workspaces in Gnome.

To be honest, if you don't feel like learning how to use Screen (which is very useful for server management on headless boxes, along with this application), then just setup a seperate workspace for the terminal window and always keep it maximized in that workspace. If you choose this option, I also recommend getting one of the following on your panel so you don't forget about things you open in other workspaces and accidentally try to open another instance of FUPPES, or rtorrent, or any other app that runs in a terminal window:

**Window List** will give you a series of buttons with the icon and name of the window (very much like GatesOS's bottom panel). Each one takes a good bit of screen real estate, though, so you'll probably want to devote a whole panel to it.

**Window Selector** will give you a single icon which, when clicked, will bring up a pop-up list of all your open windows, from which you can choose. Much less screen real-estate, but you can't simply survey your open windows without diving into what is essentially a sub-menu.
[B]
Window Picker[/B] requires installation through Synaptic ("window-picker-applet"), but gives you an icon-only listing of your open windows, along with an additional entry (with close button) for whatever window currently has focus. This is the one I use, and I highly recommend it.

---

### Post by hibliss on 2009-07-14
I guess without learning screen at all you could just use tty3.

Press ctrl+alt+F3, strat FUPPES, press ctrl+alt+F7 to hide the screen. It will continue to run in the background and you can bring it up at any time by using ctrl+alt+F3 again.

---

