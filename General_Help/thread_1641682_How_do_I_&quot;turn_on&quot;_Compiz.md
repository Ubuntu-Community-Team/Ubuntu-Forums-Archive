---
title: "How do I &quot;turn on&quot; Compiz?"
date: 2010-12-09
forum: General Help
---

### Post by Phrawm48 on 2010-12-09
How do I tell my Ubuntu 10.04 and/or 10.10 installations (I have both) to *use* Compiz now that it has *evidently* been installed?


BACKGROUND -

I installed Docky and some other gadgets (Cairo Clock, desktop calendar) that informed me they couldn't be properly displayed unless I "enabled compositing".  What I did in response was install xcompmgr, then used Start Up Applications to start it upon boot.  Doing that enabled Docky and those other gadgets to display properly: my hardware thus seems capable of supporting compositing to some degree.

Later I was informed that xcompmgr was old and inelegant compared to Compiz.  So I used Synaptic to install several Compiz packages.  I now have a bunch of Compiz configuration panels and tools, *scads* of options(!), and a panel button.


PROBLEM -

What I haven't been able to find in all of those wonderful Compiz GUI controls is a way to tell Compiz or my Ubuntu 10 installations to run Compiz.  So I can't seem to "turn Compiz on", either in real-time or at boot.

The result is that if I disable xcompmgr, then run the Compiz configurator tool, compositing remains disabled such that Docky and those other desktop gadgets don't display properly.


QUESTION -

Maybe I've made the wrong assumption, but given the width and depth of the Compiz GUI tools, I would suppose somewhere in there would be a way to tell Compiz or my Ubuntu 10 installs to start and use Compiz on boot, etc.

But I can't find those controls.  Do I instead need to run a command line?  (Seems counter-intuitive given the huge number of Compiz choices I now seem to have, but Linux can sometimes be that way.)

For that matter, is my first problem perhaps the I need some way to simply verify that I have all the Compiz stuff I need?

Cheers & thanks for your help,
Riley

---

### Post by sefs on 2010-12-09
> **Phrawm48 said:**
> How do I tell my Ubuntu 10.04 and/or 10.10 installations (I have both) to *use* Compiz now that it has *evidently* been installed?


I could be wrong but if you try right clicking on the background there is an item in there, I think its the last one "Change Bacground" that you can click on. When the dialog opens go to the last tab I believe and select on of the three options.  the first turns off desktop effects, the second turns on some desktop effects (compiz) and the third turns them all on (full compiz)?

Not near my machine right now but that is what I remember.

---

### Post by coffeecat on 2010-12-09
System > Preferences > Appearance > Visual Effects Tab > tick any box except none. Compiz is now switched on. You can then fine-tune your effects with the compizconfig-settings-manager which you can install from the package manager.

Of course, this will only work if you have a graphics card/driver combination that supports 3d acceleration.

---

### Post by oldos2er on 2010-12-09
Install fusion-icon. It creates an icon on your panel from which you can control you window managers and decorators.

---

### Post by Phrawm48 on 2010-12-09
Thanks for all the replies.  However, I have tried those recommendations and they haven't helped.

1. In VirtualBox, I have enabled 3D Acceleration.

   I do at this point wonder if VirtualBox is able to support xcompmgr but not Compiz, or vice versa?

2. In Ubuntu 10, in System, Preferences, Appearance, in the Visual Effects tab, I choose Normal.

 Ubuntu tells me it's "Searching for appropriate drivers", displays a progress bar, flashes my screen three-times, then tells me "Desktop effects could not be enabled".

3. In terminal, if I run compiz from the command prompt, I get the same three flashed screens, then:

------ Begin terminal trace of compiz command ------

xxx-Ubuntu-10:~$ compiz
compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager

------ End terminal trace of compiz command ------

(Is that "software rendering detected" perhaps the key?)

4. I did and do have Compiz Icon installed.

   Clicking it displays the aforementioned set of panels, etc.  But I remain unable to find out how to use those panels to turn on Compiz's compositing.

As I said, xcompmgr enables me to display and use Docky and other compositing-required gadgets.  That seems to indicate to me that *some* level of compositing is supported in my Ubuntu 10 VMs.

That in turn makes it all the more puzzling that the putatively more advanced Compiz seems unable to do at least as much as its less sophisticated predecessor...?

Cheers & thanks 'gain,
Riley

---

### Post by coffeecat on 2010-12-09
You didn't mention Virtualbox in your first post. I've never managed to get compiz working in a Virtualbox guest OS.

---

### Post by sefs on 2010-12-10
> **Phrawm48 said:**
> Thanks for all the replies.  However, I have tried those recommendations and they haven't helped.

1. In VirtualBox, I have enabled 3D Acceleration.

   I do at this point wonder if VirtualBox is able to support xcompmgr but not Compiz, or vice versa?

2. In Ubuntu 10, in System, Preferences, Appearance, in the Visual Effects tab, I choose Normal.

 Ubuntu tells me it's "Searching for appropriate drivers", displays a progress bar, flashes my screen three-times, then tells me "Desktop effects could not be enabled".

3. In terminal, if I run compiz from the command prompt, I get the same three flashed screens, then:

------ Begin terminal trace of compiz command ------

xxx-Ubuntu-10:~$ compiz
compiz (core) - Fatal: Software rendering detected.
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager

------ End terminal trace of compiz command ------

(Is that "software rendering detected" perhaps the key?)

4. I did and do have Compiz Icon installed.

   Clicking it displays the aforementioned set of panels, etc.  But I remain unable to find out how to use those panels to turn on Compiz's compositing.

As I said, xcompmgr enables me to display and use Docky and other compositing-required gadgets.  That seems to indicate to me that *some* level of compositing is supported in my Ubuntu 10 VMs.

That in turn makes it all the more puzzling that the putatively more advanced Compiz seems unable to do at least as much as its less sophisticated predecessor...?

Cheers & thanks 'gain,
Riley

What you can do while you are waiting for an answer/solution for virtualbox, is to:

1) Download the vmware player ([http://www.vmware.com/products/player/](http://www.vmware.com/products/player/))

2) Convert the vbox vm to a vmware vm ([http://communities.vmware.com/thread/197423](http://communities.vmware.com/thread/197423))

3) Try to accomplish what you are trying to do in virtualbox in vmware player and see if it works there.

---

