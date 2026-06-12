---
title: "Nautilus command prompt?"
date: 2010-11-03
forum: General Help
---

### Post by d5xtgr on 2010-11-03
I've become annoyed recently when I download a .deb file because when it shows up in the browser's downloads window, you can't do anything with it; anything you try to launch will have insufficient privileges to properly unpack it.

The best solution I can think of is to have a command line box appear in nautilus (like when you press ctrl+f and get a search box) that I can run sudo whatever from.  Does anyone know of an extension that allows this?  I've come up dry on Google (the ability to open a separate terminal window is offered by an extension, but that's not really what I'm going for).

This would have the additional benefit of allowing me to type in commands like 'cd' to get to hidden files and folders without having to adjust the view settings; if I know the file is there, I would be able to open it even though it doesn't need to show up and clutter the folder display.  I'm guessing something this useful has already been made, so I'd like to hear about it if you know of it.

I'm not locked to nautilus either, so if your favourite file explorer has this functionality, please let me know too!

Thanks for any pointers you can give.

---

### Post by yetiman64 on 2010-11-03
Have you checked out the package nautilus-gksu? Some info about it (from Synaptic)
> The gksu extension for nautilus allows you to open files with
administration privileges using the context menu when browsing your
files with nautilus. With this there is no need for terminal use, just right click a file and choose "Open as Administrator" (just make sure the file is set to open with the correct app).
I think this may be of some help.

---

### Post by oldos2er on 2010-11-03
> **d5xtgr said:**
> I've become annoyed recently when I download a .deb file because when it shows up in the browser's downloads window, you can't do anything with it; anything you try to launch will have insufficient privileges to properly unpack it.


Assuming your browser is Firefox, what folder are you downloading to? Hopefully somewhere in /home/user.

There's a Nautilus plugin called nautilus-open-terminal that does what you describe.

---

### Post by oldfred on 2010-11-03
I do not think I added anything, but I right click, open with other application, use custom command. I have used that for gksudo gedit and then the next time it is in the list of open with.

---

### Post by d5xtgr on 2010-11-03
Thanks
The gksu extension is going to be very handy; I'm glad that was pointed out to me.

As far as the terminal-opening extension goes, I can see where it would be useful, but it's not really filling the niche I was hoping to.  For example, I have a relatively high number of hidden subfolders in my Documents folder.  What would really help is to be able to hit ctrl-something and get a command prompt within nautilus, just as hitting ctrl-f in chromium, nautilus, or evince pulls up a search dialog.  I type in 'cd .chessmatchreplays', the hidden folder opens in the same window, I quickly browse to the file I want and drag-and-drop onto the flash drive icon on my desktop.
I hide the subfolders specifically because I don't want them to clutter the interface; then I'd end up having to scroll through pages of icons.  If I have to go into non-hidden subdirectories within hidden ones, it's generally going to be easier to get around in a browser than the terminal.  I suppose a solution would be to open the terminal onsite and nautilus the hidden folder, but it seems like this would cause window clutter rapidly- thoughts?

Thanks again!

---

