---
title: "Custom Compiz commands"
date: 2009-11-24
forum: General Help
---

### Post by tylerannosaurus on 2009-11-24
I'm trying to make a custom command to minimize the window that has focus using screen edges. I want it to minimize when I move my mouse to the bottom left but I can't find any sort of tutorial anywhere on how to make custom commands.

---

### Post by cta16 on 2009-11-24
You might want to take a look into the "wmctrl" package in the repositories. If you take a look at this video [http://www.youtube.com/watch?v=MOAsNyRE7k4]("http://www.youtube.com/watch?v=MOAsNyRE7k4")
you can see that wmctrl can maximize windows. Just change maximize to minimize and change the edge that it works on.

---

### Post by tylerannosaurus on 2009-11-24
I tried using the command it gave and changing "maximized_vert" to "minimized_vert" but that didn't work, I'm not sure what I need to do...

Here is the code line:

```
wmctrl -r :ACTIVE: -b add,maximized_vert,maximized_horz
```

I found there is a similar thing in the general settings of compiz where you can make it so you click at an edge to do what I want, but not with JUST an edge bind.

---

### Post by cta16 on 2009-11-24
The correct command for minimizing would be 'hidden'. So it should be like this

```
wmctrl -r :ACTIVE: -b add,hidden
```

I looked around and it seems like there is a lot of bug reports saying that the 'hidden' option doesn't work. You can try using ```
wmctrl -r :ACTIVE: -b toggle,shade
```
instead which will shade the window(reduce the window to only the title bar). The above script will unshade it if you go to the same edge that shaded it.

---

### Post by tylerannosaurus on 2009-11-24
I tried both of those and neither worked. (???)

I also appreciate the help!

---

### Post by cta16 on 2009-11-24
Yeah, the command 
```
wmctrl -r :ACTIVE: -b add,hidden
```
doesn't work for me either but 
```
wmctrl -r :ACTIVE: -b toggle,shade
```
works as it should for me.

What version of Ubuntu are you using?

Did you follow the steps in the youtube video I linked to?

If so, which method did you use in the video(Compiz or Metacity)?

Have you tried the other two scripts from the video which resize the windows? Do they work?

---

### Post by tylerannosaurus on 2009-11-24
I originally had the Aero snap thing from this page here: [http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html]("http://www.omgubuntu.co.uk/2009/11/aero-snap-ubuntu-linux.html") which is the same as in the video. All of those commands worked for me, but for some reason the shade one wouldn't work. I'm using 9.10 and Compiz.

I'll try the scripts from the video to see if that will work for me.

Edit>

Ok, so I tried using a script this time (I think that's what you were asking me to try) and it would work for the maximize, but not for the shade or hidden.

---

### Post by cta16 on 2009-11-24
I really have no idea why it doesn't work then. The aero snap thing you used is exactly the same as the one in the video so there's no need to try it. There's not point trying hidden because it shouldn't work.

I'm using Kubuntu 9.04 for the script and the video is using Ubuntu 9.10 so it's not a distro problem.

The only explanation I can think of is if you typed in the command wrong. Notice there are no spaces between 'toggle' and 'shade'. If you typed it in correctly, then I have no idea.

EDIT: I just tried the shade script and it doesn't work anymore. Weird...

---

### Post by tylerannosaurus on 2009-11-24
I copied and pasted it from your code after it didn't work to be sure I didn't make an error...I'm not sure why it doesn't work. I wonder if that shade feature is just disabled for me on Compiz or something.

I sent a message to the guy from the video to see what he might suggest. I'll post his response here if I get a reply.

Thanks again!

---

### Post by cta16 on 2009-11-24
I found the problem. I pasted to wrong code. It should be 'shaded' instead of shade. My bad.

```
wmctrl -r :ACTIVE: -b toggle,shaded
```

---

### Post by tylerannosaurus on 2009-11-24
Ahhhh...haha! Yeah, that works!

Not quite what I'm looking for, but glad that it works! Do you know of any sort of command list or something so I can see what else I could try? I didn't know there were even "shaded" or "hidden" commands.

---

### Post by cta16 on 2009-11-24
Just open a terminal and type in

```
wmctrl -h
```
to see all the options( hopefully the right code this time). Just scroll down and look for the section starting with <STARG> to see the options. Right now, the options are:

modal (?)
sticky
maximized_vert
maximized_horz
shaded
skip_taskbar
skip_pager
hidden
fullscreen
above
below

---

