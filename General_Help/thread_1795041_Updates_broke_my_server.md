---
title: "Updates broke my server"
date: 2011-07-01
forum: General Help
---

### Post by Snoman314 on 2011-07-01
My server was set to automatically install updates, and stopped working while I was away. When I got back to it, it now has a boot menu to choose between kernel versions, with no default or timer. So I pick one, and there are heaps of other problems.
 the /home partition isn't mounting, despite the fstab being unchanged. I can mount it manually using mount with no problems
 /var/syslog has nothing since April, and isn't updating when I reboot, so I'm not sure what I can cut and paste to here for you all to look at.
 The networking isn't running, in fact, most of the network interfaces aren't even showing up.

That's just what I've identified so far. I have no idea where to start. I can't find anything wrong other than the fact it's not working.

I can't copy and paste any output at this point, because I can't ssh, but I'll type out anything people thinks will help diagnose it. 

Please help!

---

### Post by tgalati4 on 2011-07-02
Turn off automatic updates.

What was the uptime on the server?

I would open it up, clean it out, and reseat everything.

I don't understand how the log files stopped in April.  Did a disk error force the system to go read only?

What is the hardware?

---

### Post by Snoman314 on 2011-07-02
Well I've spent a long time getting it all set up to do a bunch of stuff, and would rather fix it if I can. I wasn't even aware that the updates were on prior to going away for a while.
 Not sure about the uptime, would have been weeks to months.
 Hmm, now you mention it, I think that the filesystem has gone read only. I just tried to create a file and got the error:
```
touch: cannot touch 'file': Read-only file system
```

Looking further, I see in /etc/mtab:
```
/dev/sda5 / ext4 rw,errors=remount-ro 0 0
```

should I delete the errors option?

The hardware is a mini-itx box with an ethernet exansion card to give it 4 ethernet ports.

---

### Post by Snoman314 on 2011-07-02
Except of course that I won't be able to. Because the filesystem is read only...

---

