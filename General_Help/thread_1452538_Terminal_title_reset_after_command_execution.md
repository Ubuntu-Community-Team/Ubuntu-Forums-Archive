---
title: "Terminal title reset after command execution"
date: 2010-04-12
forum: General Help
---

### Post by ipsi on 2010-04-12
I'm not quite sure what's up with this, but when I change the title of a terminal away from the default (e.g. to represent which project that terminal is to be used for), it changes back to the default (user@host:path), but only on the task bar at the bottom of the screen, listing the open windows.

If I change tabs in the terminal and then change back, it displays again at the bottom of the screen, but as soon as I execute another command (e.g. ls), then it resets again. That's quite annoying, as I like to have a few terminals open, each with a set of tabs pertaining to a particular project. The fact that I can't see from the title on the taskbar which is which means I have to guess/remember/check them all...

Anyone have any thoughts?

---

### Post by nothingspecial on 2010-04-12
I`m not sure what your problem is or why it exists so all I can do is let you know what works for me.

I use GNU screen and byobu for terminal management.
```

sudo apt-get install byobu
byobu
```

Once byobu is running, press F2 to create a new "tab". You can have several. You navigate between them using F3 and F4.

To name them press Ctrl+A then Shift+A

The naming process defaults to "shell" which you have to delete first (You`ll see what I mean if you try it)

I find GNU screen (byobu) incredibly useful.

---

### Post by gmargo on 2010-04-12
This behavior is caused by your PS1 prompt.

The default .bashrc sets PS1 to the following for xterm compatible terminals like the gnome Terminal.
```

PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"

```The embedded code "\e]0;" says "write the following text to both the title and icon-name properties of this window" up to the "\a".

So every time you hit return, just as the command prompt appears, those other values (title and icon-name properties) are overwritten.  Comment out that line in your .bashrc and see how the behavior changes.  Of course it will no longer write user@machine to the titlebar at all.

Now try replacing the "0" with a "1" - then the prompt will only set the icon-name property, not the title property.
Now try replacing the "0" with a "2" - then the prompt will only set the title property, not the icon-name property.

---

