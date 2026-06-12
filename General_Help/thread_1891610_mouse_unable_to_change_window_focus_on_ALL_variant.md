---
title: "mouse unable to change window focus on ALL variant"
date: 2011-12-06
forum: General Help
---

### Post by a8jr on 2011-12-06
Hi guys!

I have a problem that has been remain unsolved for 2-3 years. That is for every of my first login, my mouse pointer cannot change focus.

All I want to know is what these two lines means:

Gdk-CRITICAL **: gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed

GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

And why the failure occurs. These 2 lines are taken from .xsession-errors

Thanks in advance.

-------
You can read my long story below, but you may just skip it.

What I mean is, the first time I log in, when my mouse has not clicked on anything, the focus of the mouse is on the desktop.

However when you run an apps, lets say your file manager, the mouse should "change focus", means it should click on the things on your file manager.

My problem is that the mouse "stays" on the desktop. Means that when you click on a folder _inside_ your file manager, it clicks the things _on_ the desktop, e.g. shortcut, and not the folder in your file manager.

This of course not only happened just in the file manager. Whatever the app is, the problem remains the same.

This things also happened across many different distros. I've used Ubuntu, Xubuntu, and lately Crunchbang; all with different file manager, desktop environment etc but the problem remains.

All I can remember is the first time this thing happened is when I upgraded from Ubuntu 8.10 to 9.04. So perhaps either xorg or kernel.

I've been looking around this problem for a long, long time. Until recently, after learning a little bit about how xorg works, I took some times to see the .xsession-errors and found what might be the "symptoms" of the real problem.

So I experimented a couple of times, restarting my computer a few times, and that two lines indeed appeared every time a new window is opened. I tried to randomly click on the window, and these lines are repeated, more and more.

The "temporary" remedy is to either right-click on the 'focused' window  (means the wrong window) and then left-click on the window 'you want to  focus' on (means the right window). This way the focus will change to the window you left-clicked, but you cannot left-click again on the window you left.

Another way is to login - logout. This will remedy the problem for the current session *but* if the error occurs (the aforementioned 2 lines) the problem comes back again.

---

