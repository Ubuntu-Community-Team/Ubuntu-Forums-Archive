---
title: "Full / and Gparted issues"
date: 2010-06-03
forum: General Help
---

### Post by LostSpoon on 2010-06-03
I'm running Kubuntu x86-64 10.04, but it doesn't recognize when my laptop is plugged in which means my videocard is running at half-speed and possibly my CPU isn't running as fast as it could either.

To remedy this I was going to recompile my kernel using KernelCheck. I was having a bunch of problems but I finally got the program running when it would quit after about 10 minutes. After reading through the error messages it seems I was running out of room to work with. So I emptied /tmp and tried again and ran a bit longer until running into the same problem. Turns out my entire / partition (all 7.9 GB) was full.

So I burned myself a SystemRescueCD and tried using Gparted to shrink my /home partition(sda4), move it to the right and grow / (sda3). Gparted successfully shrunk the partion and read it, but when copying it over to the right (a 16 hour operation) it seems to quit about halfway through every time. And since it didn't move it to the right I can't grow /. I can't log on normally, trying to log in through tty7 with the graphical login just tells me xserver work because there is no room on /tmp, but I can switch to another terminal and still run some commands.

I've tried apt-get clean/autoremove/autoclean but there doesn't seem to be anything to remove, and emptying /tmp doesn't free up room anymore it seems.

Any ideas?

---

### Post by srs5694 on 2010-06-03
I have two suggestions. First, you could try running e2fsck on your /home partition, with the -f (--force) option, as in:

```

sudo e2fsck -f /dev/sda4

```

You'll need to do this from an emergency boot disc or as a direct root login (not supported by a standard Ubuntu configuration) so that you can unmount /home. This operation may fix whatever problem was preventing the move-to-right part of the GParted operation. I make no promises about that, though.

Second, if that doesn't work, or if you prefer to try a quick workaround, try this: Remove your kernel source tree (/usr/src/linux-{whatever}) and uncompress the kernel somewhere in /home (or move the existing tree to somewhere in /home). You can then create a symbolic link from /usr/src/linux to wherever the files actually reside. In theory, the kernel should compile fine like that. I *think* I've done this myself once or twice, but I'm not positive of that.

---

### Post by LostSpoon on 2010-06-03
Unfortunately that didn't work, I think Gparted does it on it's own anyways, but after trying it still restarted on it's own.

And I don't know how to compile the kernel to do what I need to. I'll try to figure out how to do that though.

Oh well, thanks for the help.

---

