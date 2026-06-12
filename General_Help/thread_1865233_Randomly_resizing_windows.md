---
title: "Randomly resizing windows"
date: 2011-10-19
forum: General Help
---

### Post by hellfeuer on 2011-10-19
I've run into an extremely annoying bug in 11.10

Windows sometimes resize by themselves. Unmaximized windows become maximized or vice versa, and they can oscillate between the two states very rapidly.

On other occasions the window magically resizes, the resize handles show up and refuse to go away unless I maximize the window. They will sometimes but not always come back when the window is unmaximised). A window in this state will sometimes steal focus from the currently focused window.

All of this can happen to any window, whether or not its in focus.

Anyone know how to fix this or what's causing it?

Edit: I was wrong about one of the symptoms.

---

### Post by Thucydides411 on 2011-11-02
I have the same problem. I have no idea what causes it. All that's clear is that it's a regression introduced in Ubuntu 11.10.

---

### Post by hellfeuer on 2011-11-09
I may have found a workaround. 

Weirdly enough, the problem seems to go away when I disable my Synaptics touchpad with xinput. Does this work for you too?

I've also disabled the Move Window and Resize Window Compiz plugins, however I know for sure that that by itself did not solve the problem. I'm going to try re-enabling them to see if things still work fine.

---

### Post by War Tribe on 2012-01-28
this is exactly the same problem i've been having for a while, too. i'm happy to see a thread dedicated to this but i'm also sorry that it's happening to others. at least we are addressing it.

hellfeuer: how do you implement xinput? i'd like to do that since i don't use the touchpad on my laptop at all. and also, how do disable those plugins you mentioned?

---

### Post by hellfeuer on 2012-01-28
You don't need to disable any of the plugins. If you don't use the touchpad, here's what you can do:

In a terminal, type: ```
xinput list
```

This will give you a list of devices. For example, here's a part of the output on my system:
```
Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Razer  Razer Abyssus                    	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=13	[slave  pointer  (2)]

```

Find the id for your touchpad. In my case, it's 13

Then type: ```
xinput set-prop 13 "Device Enabled" 0
```

Where you replace the 13 by whatever id your touchpad has.

This disables the touchpad and gets rid of all the problems.

By the way are you also using an Asus G53J? I know me and Thucydides411 are

---

### Post by War Tribe on 2012-01-28
First, thank you for the instructions. To answer your question, no, I have a Gateway NV53a24u laptop. I think that's the model number for mine. It's been a great laptop so far. Once again, thank for the help!!!

---

### Post by War Tribe on 2012-01-28
i think that has solved my problem but i noticed that when i close the screen down and my laptop goes into suspend and unlock it to use it again, my touchpad can be used again. is there a permanent way of turning off the touchpad or do i have to keep putting that code into the terminal? i can use the code each time i use my laptop but a permanent solution would be nice.

---

### Post by Mr Ping on 2012-04-15
thanks hellfeuer for your instructions, as they worked flawlessly.
I have a G73JW and i was going completely nuts with this problem.
i knew it had to do with the touchpad but I couldn't find a way to turn it off until i found this thread.

again, thanks for the help :)

---

