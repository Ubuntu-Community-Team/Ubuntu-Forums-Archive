---
title: "In need of urgent help {apt-get remove}"
date: 2011-02-10
forum: General Help
---

### Post by ~Middle on 2011-02-10
Hello, so i was installing a package on my PC (I am on my laptop now) from Ubuntu software center and i got a message saying 'cannot download files from untrusted sources' and a list of libraries and so forth, so i apt-get install <list of libraries> then install the program from the Ubuntu Software center and it works fine, however i decided to remove the program, and then i thought i should remove the other stuff i had installed as well, so i did:

apt-get remove <list of libraries> 

However half way through the command i noticed it was removing a lot of stuff, if not everything... any ways i let it finish what it was doing as i wasn't too sure what was going on, but now i restarted my PC and the worst is true. My PC is F***ed, i turn it on and get in massive letters an error logo, and 

Ubunt
is

That is all i can see, i am trying to SSH into it, but i am pretty sure that open ssh will be removed anyway. 

How can i boot into text mode? and is it possible to reverse what has happened? and if not what should i do? and WHY has this happened?

Thanks a lot, i am mega stressed right now, there was a lot of important stuff on there and i had just got it configured correctly, why do i have this stupidity!!!

EDIT: Via button bashing i am now in the command line, what do?

---

### Post by stoneage on 2011-02-10
It would be helpful to mention what you removed.....

---

### Post by ~Middle on 2011-02-10
I can't recreate the list of things i installed on my laptop for some reason, but my bash history will literally be:

sudo apt-get install [these things]
sudo apt-get remove [these things]

Unfortunately, my terminals were set up not to save bash history, so i can't just press up...

I am in the command, line is there any thing i can do to test stuff? 

During the process i noticed that it was saying like 

Removing mozilla mplayer..
Removing hamachi...

^ I really don't get why it would have done that... can anyone shed any light as to why this might have happened, or even better suggest a solution?

And the package that i was trying to install was: w3af  (I thought it was something else) via Ubuntu software center i clicked install and got a message saying unknown sources for <list of packages> so i installed them from the command line. Maybe i had some of them all ready installed and i have just removed them?

Thanks

Infact that may solve it, if someone can find out what the list of things i removed was maybe i can re-install them... How would one get wireless networking going from the command line?

---

### Post by stoneage on 2011-02-10
That really doesn't help much. Until you know what you removed you can't reinstall it. 

Suggest you back up your home, reinstall Ubuntu and be more careful in future.

---

### Post by 3Miro on 2011-02-10
You can try reinstalling the ubuntu-desktop meta package:

```
sudo apt-get install ubuntu-desktop
```

This should fix most of the missing stuff, at least Gnome related (and revert to some defaults).

For general graphical stuff, you can try:
```
sudo apt-get install xorg
```

Other than that, you can try to reinstall the things that you uninstalled, but if they uninstalled other important things this may not help.

For installing/removing libraries, if you are not sure what to do, try Synaptic Package Manager, it will give you more information on what you are trying to do.

---

### Post by ~Middle on 2011-02-10
Hmmmm, useful...

What would be great is if i can solve the issue with the graphics so that i can see what Ubuntu has to say about all this.

I pressed escape twice and noticed that it rebooted, but it jsut sticks on *Starting TiMidity++ ALSA midi emulation, does this have any significance?

Really really don't want to have to do a re install

EDIT: just saw your post, and that is definitely something that was uninstalled... OK it needs to connect to the net, is there a way to start wireless networking from the CL?

---

### Post by 3Miro on 2011-02-10
There is nmcli

[http://manpages.ubuntu.com/manpages/maverick/man1/nmcli.1.html](http://manpages.ubuntu.com/manpages/maverick/man1/nmcli.1.html)

but i don't know if it is installed by default. If not, you will need to get a wired connection (assuming NetworkManager is not one of the things that got uninstalled).

What happened was that you asked it to uninstall an important library with many other things depending on it. Then apt-get uninstalled all other things with it.

---

### Post by ~Middle on 2011-02-10
Ah okay, that does make sense, so would i be able to work out what package i removed in any way? then just re-install  it? I would still need a wired connection to download everything again... goddamit this sucks...

Thanks a lot guys, now i need ot move my PC downstairs to get interwebs...

Cheers, and darn it i will have lost loads of stuff...

---

### Post by oldos2er on 2011-02-10
> **~Middle said:**
> Hello, so i was installing a package on my PC (I am on my laptop now) from Ubuntu software center and i got a message saying 'cannot download files from untrusted sources' and a list of libraries and so forth, so i apt-get install <list of libraries> then install the program from the Ubuntu Software center and it works fine, however i decided to remove the program, and then i thought i should remove the other stuff i had installed as well, so i did:

apt-get remove <list of libraries> 


In the future, just run **#apt-get remove <program>** and don't worry about the library files because APT will handle that on its own.

To fix the untrusted sources warning, see [https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

---

### Post by ~Middle on 2011-02-10
Thanks a lot for your help, i have fixed it by re-installing ubuntu-desktop from a wired connection, but it did mean lugging my PC the other side of the house!

And to stoneage:

I highly recommend you don't advise users to re-install their OS because of a problem, if i had been more of a newb then this could have followed your advice and ended up to re-installing everything, just based on your words, when in fact it was a simple fix!

Thanks to everyone that helped me!

---

### Post by 3Miro on 2011-02-10
Glad you had it fixed.

As I mentioned earlier, depending on what was uninstalled, ubuntu-desktop may or may not have solved the issue. If it were something else, then it may have been virtually impossible for us to find out what was missing and hence reinstall could have been the only viable option.

If you have no more questions on this, please mark the thread as "solved".

---

### Post by stoneage on 2011-02-10
Thanks very much for the helpful advice.

Here is some for you:-

**Don't** install packages from untrusted sources.
**Check** what the package is before you install it.
**Don't** remove important libraries when you have no idea what you are doing.
**Always check** what is being removed before agreeing to it.
And don't insult people who are trying to help you. If you had been less of a 'newb' you would not have "F***ed" your PC in the first place. 

Reinstall is a simple fix, would take twenty minutes and you would lose no data. I also suggest in future you keep a full and up to date backup of your home directory. Better yet would be to install home to a separate partition and you can reinstall without it affecting all your important data.

I sincerely hope all you lost was the desktop, and don't be surprised if in two weeks you find things breaking again because you have not reinstalled everything you removed today.

---

