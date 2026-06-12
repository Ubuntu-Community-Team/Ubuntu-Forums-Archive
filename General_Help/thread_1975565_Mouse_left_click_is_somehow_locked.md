---
title: "Mouse left click is somehow locked"
date: 2012-05-07
forum: General Help
---

### Post by harpert on 2012-05-07
Today I ran into a problem with my Ubuntu 10.04 LTS.
Suddenly I could not click anywhere else but the last activated window.

It seemed that all actions (mouse and Keyboard) were confined to the activated Window.
Actually could move the mouse pointer all over the screen but with no effect on a click except within the last activated window.


 First I thought that the batteries of the mouse were drained. Changed the batteries without success.
 

 Tried a RESTART which didn't help either.
 

 Updated/reinstalled X11 mouse and keyboard driver. Again no click outside the active window
 

 With try and error I found that after a right click on the active window and then a left click into an empty area on the last activated window the mouse would be released and suddenly I can click into an other window and go on with typing.. there. However now the mouse actions are confined only to the newly activated window.   
 

 ARGRGRGGR!!
 

 Is there anybody who could give advise what the problem here is or how to overcome this situation?
 

 My configuration:
 
[LIST]
[*]ATI Radeon HD 5400
[*]Logitech Cordless Keyboard (with     multimedia keys) and Cordless Mouse
[/LIST]

---

### Post by L3ct3rIII on 2012-05-07
Hello, harpert.

I had the same problem, on the same version of Ubuntu. In my case, this happened due to a malfunctioning of *Compiz*. In my case, reinstalling it helped. Maybe you can benefit from [this topic]("http://ubuntuforums.org/showthread.php?t=1714105"), in which someone presents the same problem. See if the problem itself and the answers to it suits yours.

If it doesn't help, post here again.

See ya.

---

### Post by harpert on 2012-05-08
Hi L3ct3rIII,

first  of all thanks for your reply.
I read the thread you mentiond in your reply. I found that in my installation there is no compiz involved.

But I looked into the .xsession_errors file and found that each click produces the follwing errors.

(gnome-panel:1887): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
(gnome-panel:1887): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
(gnome-panel:1887): Gdk-CRITICAL **: gdk_window_get_events: assertion `GDK_IS_WINDOW (window)' failed
(gnome-panel:1887): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
** (update-notifier:2480): DEBUG: Skipping reboot required
(gnome-panel:1887): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

Since I have no clue abut the Gdk I am not sure what to do with these errors?
Do you have an idea?

bye 
harpert

---

### Post by harpert on 2012-05-13
Hi There,
first o all thanks for your (you were the only one who dared) advice

However I just found  that the problem is somehow connected to my MultiMedia Keyboard.
I repaced the logitech cordless keyboard (with multimedia keys) with a simple one and o wonder there are no probs with clicking anywhere.

So now I have to find out how to use my cordless without the trouble i had before

Thanks again
Harpert


> **L3ct3rIII said:**
> Hello, harpert.

I had the same problem, on the same version of Ubuntu. In my case, this happened due to a malfunctioning of *Compiz*. In my case, reinstalling it helped. Maybe you can benefit from [this topic]("http://ubuntuforums.org/showthread.php?t=1714105"), in which someone presents the same problem. See if the problem itself and the answers to it suits yours.

If it doesn't help, post here again.

See ya.

---

