---
title: "two fold problem, grub and shell problems"
date: 2010-07-03
forum: General Help
---

### Post by radiomog on 2010-07-03
I just installed 10.04 (x64) on a new machine yesterday

I have dual monitors, I need to install the Nvidia files but need to kill x windows.  what ever I try, I can't get to a terminal after killing x windows..instead, my system just hangs there with the desktop background image showing.  There is no response except when I use a ctrl+alt+del, which gets the computer to reboot.  ctrl+alt+backspace does the same thing.   ctrl+alt+f1 nets no response.

When I boot, I don't see the grub boot menu (this is not dual boot, but my first boot showed grub and the typical grub boot options).

I tried changing things in 'startupmanager' to no avail.
after bios displays it's processes, it's a blank screen till the ubuntu login prompt.  holding down the shift key doesn't net any response.

---

### Post by yetiman64 on 2010-07-03
Sounds like you're trying to kill the x server with a desktop active and causing gdm to seize. Try dropping to a tty terminal first (CTRL + ALT +F1). Login, then issue the command
```
sudo service gdm stop
```Try the nvidia installer from there; if it complains about x being active, then try killing x from there next.

If this still doesn't work consider booting into a recovery (single user) mode, drop to a root prompt and try the installer again. Hope this is of some help.

---

### Post by radiomog on 2010-07-03
> **yetiman64 said:**
> Sounds like you're trying to kill the x server with a desktop active and causing gdm to seize. Try dropping to a tty terminal first (CTRL + ALT +F1). Login, then issue the command
```
sudo service gdm stop
```Try the nvidia installer from there; if it complains about x being active, then try killing x from there next.

If this still doesn't work consider booting into a recovery (single user) mode, drop to a root prompt and try the installer again. Hope this is of some help.


I've tried that, note in my OP that I mentioned that the ctrl+alt+f1 doesn't get me a terminal... which is part of my dilemma.

I cant find a way to get there from x-windows or at boot

---

### Post by matey3 on 2010-07-03
you can also do a control alt F1 thru F6 to get into the different (tty1~tty6) terminal screens.
I usually do a ps -A |more to see the process number of the gui i want to kill.

if you can run the terminal within your gui then may be run this and reboot:

update-rc.d -f gdm remove

(takes the gdm out of the startup), I dont know if it works with 10.x? but to put it back do this;
update-rc.d -f gdm defaults

but usually if the F1 (tty1) doesnt work the others will , do you get any black screens at all?

sometimes control c or hitting enter will show you the login prompt.

---

### Post by gamblor01 on 2010-07-03
First of all, is there a reason that you are not using the binary versions of the driver?  Just go to System -> Administration -> Hardware Drivers and then install the driver from there.


If you absolutely must install from the script then try another CTRL+ALT+F2 or F3, and so on.  CTRL+ALT+F1 shouldn't be the only terminal.  If this still fails then you can put a live CD in and reboot.  You should be able to select the "rescue mode" (or whatever it's called).  I haven't used it in a long time but I remember in the past it used to drop me into a shell (without starting an X server).

Great instructions here by the way:

[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by radiomog on 2010-07-03
> **matey3 said:**
> you can also do a control alt F1 thru F6 to get into the different (tty1~tty6) terminal screens.
I usually do a ps -A |more to see the process number of the gui i want to kill.

that just locks up my computer

acer E2220

fml

---

### Post by yetiman64 on 2010-07-03
In your first post you said
> ...I can't get to a terminal **after** killing x windows...My point was to get you to drop to a tty terminal **before** killing the x server, sorry if I didn't make that clear enough. 
Also I was under the impression that your desktop seizing etc came about as a result of killing the x server thus seizing gdm (the graphical display manager).

Here's a link you may consider checking out as it is a howto for nvidia driver installation in Lucid. May be of some help to you as general info (**not** specfic to your situation though re the seizing and terminal). [--LINK--]("http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+lynx")

Can you currently boot to a workable desktop. If so reconsider my first post again with these added comments.

---

### Post by radiomog on 2010-07-03
> **gamblor01 said:**
> First of all, is there a reason that you are not using the binary versions of the driver?  Just go to System -> Administration -> Hardware Drivers and then install the driver from there.


If you absolutely must install from the script then try another CTRL+ALT+F2 or F3, and so on.  CTRL+ALT+F1 shouldn't be the only terminal.  If this still fails then you can put a live CD in and reboot.  You should be able to select the "rescue mode" (or whatever it's called).  I haven't used it in a long time but I remember in the past it used to drop me into a shell (without starting an X server).

Great instructions here by the way:

[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)




I open "hardware drivers" and get a message saying that no proprietary drivers are in use and there are no options available in that window.  There are also no drivers listed.


the above link lists the key step in getting to a terminal, which, again, is my main issue here.. wth is going on here?  I've got ubuntu on 6 different machines and this is pushing the bleading edge of frustration.

---

### Post by radiomog on 2010-07-03
> **yetiman64 said:**
> In your first post you said
My point was to get you to drop to a tty terminal **before** killing the x server, sorry if I didn't make that clear enough. 
Also I was under the impression that your desktop seizing etc came about as a result of killing the x server thus seizing gdm (the graphical display manager).

Here's a link you may consider checking out as it is a howto for nvidia driver installation in Lucid. May be of some help to you as general info (**not** specfic to your situation though re the seizing and terminal). [--LINK--]("http://ubuntuforums.org/showthread.php?t=1467074&highlight=install+nvidia+lynx")

Can you currently boot to a workable desktop. If so reconsider my first post again with these added comments.


I previously tried the process in the link you provided, same results.

I'm in ubuntu now, I can get to a regular terminal within x-windows, but the ALT+F(1-6) results in a frozen computer, I can't even get to other boot options on startup to come in that way.

---

### Post by yetiman64 on 2010-07-03
Ok, if tty terminals are not going to work for you, what about trying

> If this still doesn't work consider booting into a recovery (single  user) mode, drop to a root prompt and try the installer again....In a Ubuntu only install hold down the SHIFT key during the grub boot stage to get the menu up to access the recovery modes and thus the root prompt access.

Edit: just reviewed your first post. This may not work sorry. I'm at a loss here now and will hold back.

---

### Post by radiomog on 2010-07-03
> **yetiman64 said:**
> Ok, if tty terminals are not going to work for you, what about trying



In a Ubuntu only install hold down the SHIFT key during the grub boot stage to get the menu up to access the recovery modes and thus the root prompt access.



I know you all are trying to help, and I really appreciate it, but in my OP, I mentioned that holding down the shift key during boot does not do anything.  I tried many variations of holding down that key for my attempt, each one to no avail..



marked it solved as it's now irrelevant

too many things wrong with this computer, well within the window for a return, so I did.

thanks again for your efforts :)

---

