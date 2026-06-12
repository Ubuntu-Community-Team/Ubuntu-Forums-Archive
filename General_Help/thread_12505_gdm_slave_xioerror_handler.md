---
title: "gdm_slave_xioerror_handler"
date: 2005-01-25
forum: General Help
---

### Post by biggyfries on 2005-01-25
hi all.  i have had this problem for a while, and was hoping someone could help me.

X randomly and frequently crashes and reboots.  it does not matter what i am doing at the time.  i can have many different programs running, and i can have nothing running but gdm, and it crashes.

here is a snippet of my syslog:

```
Jan 24 22:47:44 localhost udev[22846]: removing device node '/dev/vcs7'
Jan 24 22:47:45 localhost udev[22856]: removing device node '/dev/vcsa7'
Jan 24 22:47:45 localhost gconfd (xxx-4460): Received signal 15, shutting down cleanly
Jan 24 22:47:45 localhost gconfd (xxx-4460): Exiting
Jan 24 22:47:45 localhost gdm[4338]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Jan 24 22:47:47 localhost kernel: agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Jan 24 22:47:47 localhost kernel: agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Jan 24 22:47:47 localhost kernel: agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Jan 24 22:47:47 localhost kernel: agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
Jan 24 22:47:47 localhost kernel: agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
Jan 24 22:47:47 localhost kernel: agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
Jan 24 22:47:48 localhost udev[22897]: creating device node '/dev/vcsa8'
Jan 24 22:47:48 localhost udev[22873]: creating device node '/dev/vcs7'
Jan 24 22:47:48 localhost udev[22881]: creating device node '/dev/vcsa7'
Jan 24 22:47:48 localhost udev[22889]: creating device node '/dev/vcs8'
Jan 24 22:47:48 localhost udev[22936]: removing device node '/dev/vcs8'
Jan 24 22:47:48 localhost udev[22940]: removing device node '/dev/vcsa8'
Jan 24 22:47:48 localhost udev[22939]: creating device node '/dev/vcs8'
Jan 24 22:47:48 localhost udev[22943]: creating device node '/dev/vcsa8'
Jan 24 22:48:01 localhost gconfd (xxx-23007): starting (version 2.8.1), pid 23007 user 'dan'
Jan 24 22:48:01 localhost gconfd (xxx-23007): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Jan 24 22:48:01 localhost gconfd (xxx-23007): Resolved address "xml:readwrite:/home/dan/.gconf" to a writable configuration source at position 1
Jan 24 22:48:01 localhost gconfd (xxx-23007): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Jan 24 22:48:06 localhost gconfd (xxx-23007): Resolved address "xml:readwrite:/home/dan/.gconf" to a writable configuration source at position 0
``` 

I have changed the username to "xxx", fyi.  

any help would be greatly appreciated.

thanks.

dan

---

### Post by biggyfries on 2005-01-30
so, i guess no one has an answer for me...?

Yes, i am still having this problem.

any help would be greatly appreciated.

---

### Post by crane on 2005-01-30
Does it do this randomly?

 I noticed the "Received signal 15" also it my help to search and see what that signal is referring to.

Also what vid card are you running and what version Warty or hoary?
Have you checked your X11 log to see if there was an error listed there?


I;m not a guru, these are just a couple things I thought of that may help someone find the problem.

---

### Post by biggyfries on 2005-01-30
I am using a Nvidia Ti4400 card. Running Warty.  It does happen randomly--i can have anything open, and then it will crash (has not yet crashed with Terminal open yet, tho).

I will post my X11 log when i am home.

Also, i am receiving some fixed font errors, for unix/:7100, or something like that.  I read on a [different forum](www.linuxquestions.org)  to comment that line out of the XFree config, do i did.  I have not used the pc since, so i will post my results here.

is anyone seeing this issue with gdm?

---

### Post by Blayde on 2007-06-11
I too am having this problem, but it a little more annoying.

```
Jun 11 10:13:55 ubuntuDesktop gdm[4555]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Jun 11 10:13:57 ubuntuDesktop gdm[5372]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Jun 11 10:14:01 ubuntuDesktop gdm[5384]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Jun 11 10:14:06 ubuntuDesktop gdm[5398]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
Jun 11 10:14:06 ubuntuDesktop gdm[4552]: deal_with_x_crashes: Running the XKeepsCrashing script
Jun 11 10:14:20 ubuntuDesktop gdm[4552]: Failed to start X server several times in a short time period; disabling display :0
```

Then I just press the power button and let the kernel gracefully shutdown (yay for acpi) because the video output is shot. This only happens when using Firefox, but that is really all that is ever used on this computer. I thought it had something to do w/ a buggy extension so I disabled a bunch of them and it doesn't happen as much. The computer is an old HP Brio w/ an Intel Celeron @ ~534MHz, 320 MB RAM, 431 MB swap, and an Intel Corporation 82810 CGC [Chipset Graphics Controller] for the video card. Right now all I'm thinking I can change is to add more swap or disable some modules in the xorg.conf like dri and/or glx. Any other suggestions are welcome!

---

### Post by jesushero on 2007-12-14
I'm having some similar problems. Different log entries, but I do have the X problem.

Have a look there [http://ubuntuforums.org/showthread.php?t=640105]("http://ubuntuforums.org/showthread.php?t=640105")

If you do find a solution that works for you, let me know.

---

### Post by sstalpers on 2008-02-02
I had a similar problem; updating my NVidia driver solved it for me. See [http://ubuntuforums.org/showthread.php?t=96068]("http://ubuntuforums.org/showthread.php?t=96068").

Good luck.

---

