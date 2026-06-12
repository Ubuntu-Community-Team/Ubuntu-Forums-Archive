---
title: "Connecting laptop to external screen"
date: 2011-02-04
forum: General Help
---

### Post by YigalB on 2011-02-04
I installed Ubuntu on MSI laptop. Works great.
I am trying to connect the laptop to external screen through the VGA output.
When the laptop's lid is open - it works just fine
When the laptop's lid is closed - the VGA output content is gone.

i didn't find t\in the monitors' menu nor in the power menu, an entry where I can ask or set the VGA output to be active all the time.

Any idea?

---

### Post by Habitual on 2011-02-04
Preferences > Power Management

---

### Post by drewsus on 2011-02-04
> **Habitual said:**
> Preferences > Power Management

There is nothing there for that. 

I set this sort of thing up for my mom, and the way I dealt with this issue is to have a mouse (preferably wireless) attached to the netbook and when you close the lid, just move the mouse and the screen will come back on.

---

### Post by NFblaze on 2011-02-04
Are you sure?

The power management should have an option in the "AC Tab" and "On Battery Tab" to set an option for what happens when you close lid. 
You'd change that to "Do Nothing".

(Also, if that works you can also add to the panel Inhibit Sleep or Inhibit Power to the gnome panel. That way it's easier and more manageable.)

---

### Post by YigalB on 2011-02-04
> **drewsus said:**
> There is nothing there for that. 

I set this sort of thing up for my mom, and the way I dealt with this issue is to have a mouse (preferably wireless) attached to the netbook and when you close the lid, just move the mouse and the screen will come back on.
You are right - there is nothing there. Strange - for such a common simple issue.
Finally it worked for me. here is what I did:
I closed the lid 7 times. Each time, before closing, I did "make default" - finally it worked. 
It seems that 7 is the magic number.

But now I am afraid to open the lid.

---

### Post by drewsus on 2011-02-04
> **NFblaze said:**
> Are you sure?

The power management should have an option in the "AC Tab" and "On Battery Tab" to set an option for what happens when you close lid. 
You'd change that to "Do Nothing".

(Also, if that works you can also add to the panel Inhibit Sleep or Inhibit Power to the gnome panel. That way it's easier and more manageable.)

[IMG]http://i.imgur.com/BVp6t.png[/IMG]

---

### Post by NFblaze on 2011-02-04
Im not on Linux box right now though your panel seems to be definitely lacking. I have that plus more such as "Dim Display" and ability to control "screen brightness".   Is the battery tab the same?

What version are you using by the way. Perhaps I'm using a superior power manager also.

---

### Post by YigalB on 2011-02-04
> **NFblaze said:**
> Im not on Linux box right now though your panel seems to be definitely lacking. I have that plus more such as "Dim Display" and ability to control "screen brightness".   Is the battery tab the same?

What version are you using by the way. Perhaps I'm using a superior power manager also.
I am using 10.10.
I am not sure what "your panel seems to be definitely lacking".

---

### Post by drewsus on 2011-02-04
> **YigalB said:**
> I am using 10.10.
I am not sure what "your panel seems to be definitely lacking".

He is talking to me (and my first screenshot).


Whoops... that was taken from my Desktop. Doh.

Still, from my netbook, there is no "Do Nothing" option. 

[IMG]http://i.imgur.com/BGnQL.png[/IMG]

gnome-power-manager v2.32.0

---

### Post by NFblaze on 2011-02-04
"Blank Screen" would be the "Do Nothing". 
I thought that was understood in terms of power management. My fault.

---

### Post by drewsus on 2011-02-04
> **NFblaze said:**
> "Blank Screen" would be the "Do Nothing". 
I thought that was understood in terms of power management. My fault.

Ah, I see. To me, "Do Nothing" means do nothing. As in, don't *change* to a blank screen. 
Well I think you need to re-read OP's problem. 
He has a netbook. He has an external screen. He has a cable that connects the two. He sends the visual output to the external screen and does not need his internal, so he closes it. This causes power manager to go "Blank Screen" which applies to the external monitor as well. With the lid closed, he cannot press any keys or move the mouse via the track pad, so has no way to reactivate the display.

Another solution would be to leave the lid up and press the Fn + F# that turns your internal screen black.

---

### Post by YigalB on 2011-02-05
> **NFblaze said:**
> "Blank Screen" would be the "Do Nothing". 
I thought that was understood in terms of power management. My fault.
I also have the "do nothing". And now I lost the screen when I closed the lid.

And worst: I started playing with the "same image on all monitors" and I found out that if I don't select this, I can utilize better resolutions both in the laptop's screen and the external screen. However, I have two problems:
1- In the external screen, i don't have the bar on top and bottom.
2- Again, when I close the lid, the external monitor gets no signal.

How can I solve these 2 issues?

---

### Post by techunit on 2011-02-05
Significantly simpler solution. plug in your monitor and hit ctrl>alt>backspace this will log you out and depending on your settings log you back in. when it does your monitor should switch over and you should be able to close the laptop display. You can also do this manually via the monitor settings configuration under the preferences menu.

---

### Post by YigalB on 2011-02-05
> **techunit said:**
> Significantly simpler solution. plug in your monitor and hit ctrl>alt>backspace this will log you out and depending on your settings log you back in. when it does your monitor should switch over and you should be able to close the laptop display. You can also do this manually via the monitor settings configuration under the preferences menu.
Now I have signal while lid is closed. I am not sure if the "ctrl>alt>backspace" had any affect - i see no change.


But I still don't have the to and bottom bars.

---

### Post by techunit on 2011-02-05
Try it a couple different ways this worked for me. Try going in to the display settings and manually turn off your laptop monitor. or try the function switch key (If it was working)

---

### Post by YigalB on 2011-02-05
> **techunit said:**
> Try it a couple different ways this worked for me. Try going in to the display settings and manually turn off your laptop monitor. or try the function switch key (If it was working)
What would happen if I disable the laptop's monitor, and then opening the lid? will it resume automatically? What if I disconnect the monitor? will it be smart enough not to leave me monitor-less?

---

### Post by techunit on 2011-02-05
I have no idea. A won't have a change to test this until next weekend unfortunately. You could try it and if it didn't come back you could hit 

ctrl alt backspace

to bring it back I think. However since ctrl alt backspace isn't working for you I don't know.

---

### Post by soltero on 2011-03-08
*- post deleted, pending possible solution -*

---

