---
title: "Ubuntu 9.10, the honeymoon is over?, Logon boot loop"
date: 2010-01-07
forum: General Help
---

### Post by NunyaB on 2010-01-07
I apologize in advance if my post is long winded, just really frustrated :(

I thought I had found the perfect match.  I built a mini desktop based on a VIA mini ITX MB using laptop drives in a removable dock.  This way a simple turn of the key, plop in a new drive, instant new OS that can be switched back & forth.  I really, really enjoyed Ubuntu 9.10 from the start.  The problem is this machine connects to the single monitor through a KVM switch.  ( No monitor detected )  Ubuntu defaulted to a 640x480 resolution.  I researched the forums and manually set the res I needed with "xrandr --newmode "1024x768_60.00""  no problems and everything was great.  Two updates later and I have the logon loop issue.  ( Boots, prompts pw, enter it, reboots and re-prompts for pw, over and over )  Eventually it boots normal without a pw, I researched the forums again.  None of the solutions work for me.  My xorg.conf is blank and creating it with suggested methods on forums does not change that.  I am not sure that it is a conflict with the boot screen resolution anyway since mine is lower at 640x480 than my desktop of 1024x768.  ( One of the suggested issues causing the problem )  Even the other ( sorry for being such a newb, command prompt in Windows,) method says no such command when I go the "C"+"Alt"+"F1" route

In addition yesterdays set of update manager updates has given me the following error [I]"Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-xV8IiXCKol: Connection refused)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-xV8IiXCKol: Connection refused)"  and the system freezes for a few seconds every now and then (HD & mouse lights lit all desktop activity stopped until they go out)  

[/I]A simple restart will probably clear that but it might be another hour before I can get logged back on.  I do not think this is a hardware issue as Ubuntu 9.04, Windows XP SP1, or Windows XP SP2 HDs have any issues.  Please help so I can get back to enjoying my new machine and Ubuntu.  Otherwise I need to consider the honeymoon is over and move on.  ;)  

Thanks In Advance!

---

### Post by running_rabbit07 on 2010-01-07
I'd reinstall. First fire up the LiveCD and run the Check disk for defects function before reinstalling or even burn a new dosk running Windows and burn it at a slower setting. Karmic is running great for most people now, hopefully you can join the crowd.

What are your system specs? Primarily the GPU?

---

### Post by NunyaB on 2010-01-07
Thanks Rabbit, I will give the Live CD a try.  I hate the idea of a clean install if I can avoid it but as long as I don't run right into the same problem...

It's a VIA EPIA mini ITX 1.3 Ghz MB with 1 Gig of RAM ( max for MB ).  Onboard integrated video & sound with very, low power useage.  Not a gamer but sweet with clean OS.  XP & Ubuntu both did great on this up until this problem with 9.10

---

### Post by Strongman332 on 2010-01-07
did you ever try booting in recovery mode?

---

### Post by NunyaB on 2010-01-07
yes strongman I did try recover mode, no effect.  Said everything was ok then right back into boot loop.  But come to think of it I did not try to boot into the previous versions before the updates.  That's food for thought.  Thank You!

---

### Post by prshah on 2010-01-07
> **NunyaB said:**
> ( Boots, prompts pw, enter it, reboots and re-prompts for pw, over and over )
[I]"Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-xV8IiXCKol: Connection refused)

Maybe you've already checked this, but it's a suggestion worth throwing out all the same: Do you have enough free space on your Ubuntu HDD? Inodes? Please check with```
df -h
df -i
```

I don't know what the "optimum" free space should be, but if any of the results are over 90%, probably this is the first thing I would look at.

---

### Post by NunyaB on 2010-01-07
Thanks for responding prshah, I will run df -h/-I as soon as I can get back into Ubuntu.  I shut down over night and it is going to take me awhile but it should have plenty of space.  80 gig drive only with Ubuntu 9.10!  If there is a space problem it might indicate HD failing so go thought.  Thanks!

Let me get back into the machine and I'll let you all know what I find.  Thanks Again!

---

### Post by NunyaB on 2010-01-07
Update:

Still working on machine, setting up another new HD with full clean install.  While trying to access the orginal found a new error message that flashed before boot screen pw prompt:

*vga=768 is depreciated*   followed by something but flash was so quick on three attempts this is as much as I could see before it was gone.  Something is not right. ](*,)

---

### Post by NunyaB on 2010-01-07
Thanks for all the suggestions.  I have done a clean install with a new HD and all is great again.  I will continue to run tests to be sure and will post any status changes here.  Before I allow any updates to take place I am creating and ISO of the hard drive to make the restore process a lot smoother.  Kudos to Ubuntu though, I would SOOOO rather do a Ubuntu clean install than Wondoze any day.  

I tried using the Live CD to repair the original.  No luck and it says everything is fine.  I do not know yet what got so messed up but I have saved the hard drive as is and will find out!  ;)  Even the CD had a screen res much higher than I need so it is not an issue that the machine can't do it.  I think I will eye the "you've got to do these Tweaks" articles a little bit closer next time.  Thanks Again All!

---

### Post by running_rabbit07 on 2010-01-07
That's awesome. Glad you got it working.

---

### Post by NunyaB on 2010-01-11
OK, I think I have discovered what was causing the initial boot loop problem.  I am not sure If I should start a brand new post or if anyone will see this.

As I said in my first post, I set up this system CENTERED around removable laptop drives in a ICY-Dock.  This way I can swap out operating systems, versions , and configurations at will.  I now think this is what is creating the boot loop.  The new clean install worked great with no issues.  Tested several restarts before & after upgrades, software installs.  No problems.  I cloned the drive and that one had no problems on restart.  But I did notice on one try I was prompted for pw when I forgot to remove an external usb drive I was transfering files from.  I removed it and back to no problems.

Now here's the thing.  I was working with other OS drives all weekend.  Tonight I went back to the Ubuntu 9.10 drive.  BOOT LOOP pw prompt!  _Can some one tell me if this issue is being created by the drive being removed from the machine?_  If so I'm not sure I can rely on using Ubuntu until I can build a machine dedicated to just it.  And that would not be nice...  :(  My first try at 9.10 lasted 2 months before the boot loop cycle corrupted the OS to non-functionality.  2 days this time before it starts.  I can't be the only one who needs to remove the drive from the machine.

Thanks in advance for all the help!  NunyaB

---

### Post by NunyaB on 2010-01-11
I will start a new thread on this one since ( maybe ) it's a new issue

---

