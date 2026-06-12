---
title: "open terminal command in 10.04?"
date: 2010-11-27
forum: General Help
---

### Post by pstrbrc on 2010-11-27
In Xubuntu 9.04 I could right click in any directory folder and have the option of opening a terminal window "there". So the terminal command line would open preloaded to that directory. I know, I'm lazy, but it sure made life (and command line work) easier. But it's not available in my new install of Ubuntu 10.04. Now, I know that my gui environment has changed from xfce to gnome, but I would have expected MORE features, not less. Can anybody help?

---

### Post by WorMzy on 2010-11-27
I dunno about XFCE's default file browser, but that functionality is not available with the standard nautilus package. Install nautilus-open-terminal.

```
sudo apt-get install nautilus-open-terminal
```

---

### Post by dcstar on 2010-11-28
> **WorMzy said:**
> I dunno about XFCE's default file browser, but that functionality is not available with the standard nautilus package. Install nautilus-open-terminal.

```
sudo apt-get install nautilus-open-terminal
```

Or simply use Synaptic to install it instead of insisting people use terminal commands when their issue is that they are having trouble getting into the terminal.....

---

### Post by jocko on 2010-11-28
> **dcstar said:**
> Or simply use Synaptic to install it instead of insisting people use terminal commands when their issue is that they are having trouble getting into the terminal.....
He did not say that he has problems getting into the terminal, just that the "open terminal here" function is missing. So he can very easily open a terminal from the gnome menu (Applications-->Accessories--Terminal) and run that command to install the nautilus extension.

---

### Post by Spyderkid on 2010-11-28
Can't you just right click and do open with and then choose terminal?

---

### Post by WorMzy on 2010-11-28
> **dcstar said:**
> Or simply use Synaptic to install it instead of insisting people use terminal commands when their issue is that they are having trouble getting into the terminal.....

Click here, now click there, then click this box, then type this, then scroll down, then right-click this, then left-click that...

No. You can insist that people use that unintuitive method if you want. I'll stick with what's easy to say, easy to understand, and easy to perform. I'm not sure what your problem is with the command line is, but I'd appreciate it if you didn't go around chastising people for using it.

---

### Post by Dave_L on 2010-11-28
Personally, I would simply say "Install the package nautilus-open-terminal.", and only provide more detailed instructions if asked. :wink:

---

### Post by Swagman on 2010-11-28
or press ctrl + alt + T

---

### Post by pstrbrc on 2010-11-28
LOL Golly, guys. No, in 10.04 control-alt-t does not open a terminal in the directory you have open, it opens the terminal in the ~ directory, which is home. And, yes, I'm completely comfortable working command line, or I wouldn't be trying to open a terminal *anywhere.* And I'm just as comfortable with command line apt-get as Synaptic or the Ubuntu Software Center under the Applications dropdown menu. But even if I weren't, I could just simply ask a poster that told me to install xyz, "How do I do that?" Quit ragging each other, OK? Grow up, show some grace. Watching total strangers squabble about what's wrong with the way the other offered me help makes me sorry I asked. Sheesh!

---

### Post by pstrbrc on 2010-11-28
btw, the list of nautilus stuff was quite confusing in Software Center, but it was there. I found it because I used the command line command, so the particular file showed up as "installed" in the list offered by Software Center. But it required a reboot. Works fine now. 
I mostly use this function when I'm wrapping a series of mp3 clips into one seamless file. Put them all in one folder, right click and open terminal, run mp3wrap. Best of both worlds. gui and terminal, working hand-in-hand. 
That and a good quad espresso, makes for a good day.

---

