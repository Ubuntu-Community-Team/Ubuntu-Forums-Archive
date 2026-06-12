---
title: "Simple Data Recovery with 10.04 LiveCD?"
date: 2011-09-06
forum: General Help
---

### Post by dedukes on 2011-09-06
Hi.

Last night, while upgrading from 10.04 to 10.10 via Update Manager, my system stalled and the upgrade was corrupted  (already have posted a thread on this).  I can't reboot at the moment, and I'm running 10.04 off the liveCD.

I've kept weekly backups of my user files, so I'm not terribly freaked out.  I'm happy to do a clean install of 11.04 (my ultimate goals).  However, there are a couple precious Open Office files that didn't make it into the last back up cycle.

As I run through the following, please keep in mind that I'm pretty dumb about terminal commands.  I've run Ubuntu happily for years, but I'm still pretty stupid about commands, file structure, etc.  Thanks for your patience.

The LiveCD doesn't seem to include any backup software.  If I try to drag and drop my home or Documents folder onto my USB-connected external hard drive I get this error: "The folder "[any folder]" cannot be handled because you do not have permissions to read it." When I run the terminal from LiveCD Ubuntu I'm liveCD directory, and don't know how to get to the hard drive's directory.  When I run genome terminal from my hard drive, the prompt looks like this:

ubuntu@ubuntu:/media/c61e6381-e10b-4046-87bd-0282a1910c3e/usr/bin$ 

If someone could give me a simple process for copying my Home or Documents folder (home would be better, but I could live with just the Documents folder) to my USB hard drive I'd appreciate it.

DD

---

### Post by nothingspecial on 2011-09-06
You are trying to copy /usr/bin

You need to copy

/media/c61e6381-e10b-4046-87bd-0282a1910c3e/home/*your_user_name*

---

### Post by dedukes on 2011-09-06
Thanks!

Sorry to be a pain, but would you please give me the exact command to use?  The USB hard drive is called "clove."  I've tried several and I'm doing something wrong.

---

### Post by nothingspecial on 2011-09-06
If it's mounted at /media/clove then 

```
cp -rv 
/media/c61e6381-e10b-4046-87bd-0282a1910c3e/home/your_user_name/* /media/clove
```

You'll have to change your_user_name to your actual username

---

### Post by dedukes on 2011-09-06
Okay.

Did that.  And this is what happened:

ubuntu@ubuntu:/media/c61e6381-e10b-4046-87bd-0282a1910c3e$ cp -rv /media/c61e6381-e10b-4046-87bd-0282a1910c3e/home/dare/* /media/clove
cp: cannot stat `/media/c61e6381-e10b-4046-87bd-0282a1910c3e/home/dare/*': No such file or directory
ubuntu@ubuntu:/media/c61e6381-e10b-4046-87bd-0282a1910c3e$ 

When I cd to the home directory and use "ls" command it goes right back to the prompt, showing no files.

I can see it in the file manager (see attached screen shot).

---

### Post by nothingspecial on 2011-09-06
Well, lets try another aproach.

Press Alt-F2 and type ```
gksudo nautilus
```

When the file browser pops up press F3 so you have two panes. Try dragging yiur home folder across.

---

### Post by dedukes on 2011-09-06
That worked!  It took a while, because the external harddrive kept unmounting for some reason (possible a faulty cable).

But now, after I've copied all user docs, suddenly my computer won't boot from the LiveCD anymore.  It hangs on the Ubuntu screen with the flashing dots.  I tried another LiveCD (11.04) as well, and that doesn't work either.

Is it possible that this malfunction is a delayed response to the currupted uprade?  Or is it necessarily the hardware dying?

Now that I've backed up, if I could just do a clean install then maybe all would be well.

---

### Post by dedukes on 2011-09-07
I finally made my way out of the woods.  The CD drive stopped working because I have an ext drive connected through a USB. 

Once that was figured out I did a fresh install of 11.04.

Thanks for all your help nothingspecial.

---

