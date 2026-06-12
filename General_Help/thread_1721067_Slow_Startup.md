---
title: "Slow Startup"
date: 2011-04-04
forum: General Help
---

### Post by ndstate on 2011-04-04
Hello,

Ubuntu is booting up much slower than it use to be.  My bootchart can be seen at [http://dl.dropbox.com/u/1243306/bootchart.png](http://dl.dropbox.com/u/1243306/bootchart.png).  Does anyone have any idea why its taking so long to boot?

Thanks!

---

### Post by lithopsian on 2011-04-05
I don't know what it was like before but you seem to be having problems with your hard drives.  Or one of them anyway.  You might want to try booting with quiet off or look in the logs to see what it says about that.

The bootchart you posted shows a full-on fsck of one of your drives which might just be an unfortunate coincidence or it might be an ongoing problem.

Other than that it doesn't look too bad until Gnome starts.  Then it seems slow, perhaps just because your readahead doesn't cover that part of the boot.  The Samba Netbios daemon looks like it is holding things up a lot, but I'm not familiar with how it should behave.

For advanced tweaking, you should be able to improve your boot time by utilising both CPU cores with the concurrency options that are available.  Fix the other problems first though.

---

### Post by ndstate on 2011-04-06
Hello,

Thank you for your response.  Below are different bootcharts to help establish what is "normal" for this system

[Normal boot chart with expected speed]("http://dl.dropbox.com/u/1243306/bootchart-good.png")
[Bootchart after running e2fsck]("http://dl.dropbox.com/u/1243306/bootchart-new.png")
[Another bootchart after running e2fsck (one difference is the length of ureadahead)]("http://dl.dropbox.com/u/1243306/bootchart-new2.png")


The only thing I saw that jumped out at me was that my second hard drive had not been fsck-ed after 250 boots, so I fsck-ed it and changed it in fstab to 0 3 .. which I believe makes it 3rd in line to be fsck-ed when needed.  I looked at the logs and with with quiet boot off and didn't see anything else that jumped out, but I am no expert on any of this.

It seems like "upstart-dev-br" "portmap" and "smbd" among others run for a lot longer now then in the original bootchart.  I dont know what any of that means.

I appreciate anyone's continued help.

Thank you so much! :)


--

Edit: I am not sure its related or not, but sometimes when the desktop loads I get the following errors:
```
The panel encountered a problem while loading "OAFIID:GNOME_ClockApplet".
The panel encountered a problem while loading "OAFIID:GNOME_FastUserSwitchApplet".
The panel encountered a problem while loading "OAFIID:GNOME_NotificationAreaApplet".
```
Related to the ureadahead?

---

### Post by lithopsian on 2011-04-08
The readahead in the second two bootcharts does not seem to be effective.  Assuming you are starting more or less the same set of services.

It might be failing because the readahead profile needs to be updated.  This ought to happen automatically but might not for some reason.  The readahead might be reading a lot of unnecessary files and not reading necessary ones.

Or maybe readahead is actually trying to do a profile instead of reading ahead.  The second bootchart shows ureadahead running in parallel with the rest of the boot rather than performing lots of IO before the rest of the boot.  That suggests it is doing a profile.  The third one looks like it has done the readahead but it hasn't produced a useful cache of the necessary files for the rest of the boot.

The readahead cache might also be getting trashed by something like a large fsck job or some other huge disk read.

---

### Post by ndstate on 2011-04-09
Hello,

Thank you for your input.

I purged ureadahead, rebooted to let it profile, and rebooted again.  [This is the 2nd reboot's bootchart]("http://dl.dropbox.com/u/1243306/newur.png").

Boot is still pretty slow.  Any ideas what else could be the issue or whats going on?

Thank you!

---

### Post by tweaktolive on 2011-04-09
you can download ubuntu tweak it will help.

what is your PC config ? maybe thats why its slow

---

### Post by lithopsian on 2011-04-09
That doesn't really look slow.  Your Ubuntu is basically booted in 20 seconds.  From then on it is just starting a pretty complex looking desktop, with Metacity and compiz and dropbox and all sorts of stuff starting up.  I imagine you're also starting a whole lot of services that I don't see but are making the readahead do a of of work.  Probably you don't need half of them.  Like do you need avahi?  Firestarter?

---

### Post by ndstate on 2011-04-10
Hello,

Thanks for the responses.  Ubuntu may be booting pretty quickly to the desktop, but the entire process use to take less than 30 seconds, take a look at [this bootchart]("http://dl.dropbox.com/u/1243306/bootchart-good.png").

I don't believe there are many if any services that were added after that bootchart.  Something else has to be making it slow down?  But I will take a look at services nevertheless.

Thanks again

---

### Post by lithopsian on 2011-04-10
The main difference (the only difference?) I can see between [this (good)]("http://dl.dropbox.com/u/1243306/bootchart-good.png") and [this (bad)]("http://dl.dropbox.com/u/1243306/newur.png") is that bootchart stops earlier on the "good" so it appears quicker.  Actually everything is taking about the same time.

Bootchart (depending on version) is normally stopped by upstart when the rc scripts are finished, although Gnome and Metacity scripts may still continue to run for an indefinite period after that.  This appears to have happened in your good example, but not in the bad example.  Check your bootchart.conf to see that it is still configured to be stopped at rc finish.  Also check if there is a late rc script that is sleeping for 30-40 seconds.  I don't see it on the bootchart though.

Another possibility is that bootchart is running more or less the same in each case but that the chart is being chopped at 30 seconds in one case and not the other.  I believe it includes logic to end the chart when Gnome appears to be idle which might happen briefly even though there are more startup tasks yet to run.

---

### Post by ndstate on 2011-04-12
I saw the following in bootchart.conf

```
start on virtual-filesystems
stop on stopped rc

```

Is that what I was looking for?

The startup difference even after login is very noticeable.  Everything use to pop up instantly, now I literally have to wait about a minute before the desktop is ready to go.

Is there any other way to figure this out? I really don't understand exactly what bootchart is saying, other than some of the processes look way longer than they use to.  But you know more about this than me so I appreciate any continued help.

Thanks!

---

### Post by lithopsian on 2011-04-12
Yes, that is the correct controls.  So for some reason, your rc (= /etc/init.d/rc) is no longer finishing at 30s which is just when your desktop is coming up, but is lasting over a minute which is until all your desktop and startup processes have completed.  I think you should track this down before trying to do anything else.  That is the only big difference I can see (although I can't see how your desktop environment start in the first bootchart) and it may well lead to your problem.

I can't see anything on the bootchart that looks like an rc script sitting there for 30s.  Which S99 services do you have in /etc/rc2.d?

---

### Post by ndstate on 2011-04-13
Hello,

In /etc/rc2.d I have the S99 following files:

S99acpi-support
S99grub-common
S99ondemand
S99rc.local

Is that what you were looking for?  I also have tons of other files with other names.

> So for some reason, your rc (= /etc/init.d/rc) is no longer finishing at 30s which is just when your desktop is coming up, but is lasting over a minute which is until all your desktop and startup processes have completed. I think you should track this down before trying to do anything else.

Sorry to be a bug, but how would I track that down?  Ill look into what that file does.

---

### Post by lithopsian on 2011-04-14
Well that's a good question.  How do you track anything down?  Just keep poking and see what you turn up.  In this case something is making your bootchart run way longer than it should and the first place to look is the stopped rc event that should be closing it.

Of your S99 scripts, only rc.local seems like a candidate for running way too long.  Or rc itself.  I would expect either case to show in bootchart but I don't see it.  Of course rc is running for the whole length of the boot and it doesn't show, but it is still there.  You might be able to spot it from a terminal as soon as your desktop comes up.  Or put a little script in your autostart file that dumps off all the processes.  rc should be long gone by the time you get to that point, and so should bootchart (=collector).

Or the stopped rc event might be happening normally after about 20s and still bootchart isn't stopping.  Don't know why that would be, I'm not an upstart expert.

---

### Post by lithopsian on 2011-04-15
I might have sent you off on a wild goose chase.  upstart versions of bootchart continue to run after they have been told to stop by upstart.  They mark this point with the third red dotted line on the chart.  The time that they continue to run is configured in bootchart.conf and set to 45s by default.  The bootchart collector also stops itself during this time if it detects the PC is idle and assumes that desktop has booted.

Your "bad" bootchart is showing that it has been requested to stop at about the right time.  It then continues to run for about 45s.  Quite possibly there are still processes starting up after that, or perhaps you are already using the desktop for something else because the chart doesn't show any signs of going idle.

The "good" bootchart stops about 2s after being told.   The IO has gone idle and the CPU more or less idle.  Obviously I can't tell if a whole bunch of desktop stuff then started up a few seconds later.  The greeter had started but no way to tell whether it was auto-logging in or sitting at a prompt.

The difference may be a very subtle thing that prevents bootchart seeing idle on the second bootchart, or it might be a very real change you've made to the desktop programs being started or to the login dialog.  Desktop processes I see include, dropbox, nm-applet, nautilus, awn-applet, and more but they don't really kick in for about 5s after the desktop is ready.  In between is mostly the GDM greeter (login) but also I notice a dbus/hald task has slipped slightly in the "bad" login.  The IO is idle and the CPU nearly idle, but obviously not quite enough to shut bootchart down.

---

### Post by ndstate on 2011-04-16
Hello,

Thanks for the info and help.  Perhaps the problem could be that it is reporting the desktop is ready, but the background/icons and top panel have not appeared yet?

Is there maybe a way to set boot order for the desktop stuff?  It seems like the panel and such are taking quite a while to appear.

Thanks! :)

---

