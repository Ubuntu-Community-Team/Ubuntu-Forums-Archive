---
title: "errors with ICEauthority, Nautilus, and permissions"
date: 2009-11-01
forum: General Help
---

### Post by Exüberance on 2009-11-01
I just recently (2 days ago) upgraded from Windows Vista to Ubuntu (I'm duel-booting though so I can still run both) and, with the exception of the screen going crazy which I fixed by updating graphics drivers, was working perfectly fine. I could access the Windows partition of my hard drive, change settings, start up normally. All was working well for the first several startups. After changing some login settings (I don't remember exactly what I changed now, but I think I set it to log me in automatically) my normal startup epic fails.

Firstly, an error pops up saying that ICEauthority cannot be updated. (I searched around and found out that similar problems could be resolved with the chown command. I tried that, but that changed absolutely nothing).
*Could not update ICEauthority file /home/exuberance/.ICEauthority*

Secondly, I get another error about a problem with the configuration server and something about a sanity check
*there is a problem with the configuration server. (/usr/lib/libconf2-4/gconf-sanity-check2 exited with status 256)*

Thirdly, I get an error about Nautilus not working properly.
*Nautilus could not create the following required folders: /home/exuberance/Desktop, /home/exuberance/.nautilus. Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them.*

Then, it starts up, but the background is what the background is for the root user, not for my normal user, and there are no task bars or icons. I tried pressing a bunch of key combinations, but I can only get 2 things to work: the ctrl+alt+del/power button menu, and the full-screen terminal (Ctrl+Shift+Alt+F2).

Tying in startx doesn't work since it's techinally already running, just very very broken.

But all is not hopeless. If I reboot and choose to run Ubuntu (Recovery) instead of Ubuntu, then choose normal boot, it opens the full-screen terminal. I log in as exuberance (my main account) and enter the command startx. TA-DA! It works! But, wait, not quite. My permissions are screwed. I tried accessing stuff like my USB key or the C: drive (the windows partition) but, nope. Can't do that. If I use commands in  the terminal to mount the USB device (prefixed with sudo), I can get it to work, but only for the current session. Every time I restart I have to do it again.

Now, if I log out and log in as root instead, I can now access everything. This is fine for now, but I would rather use my normal user and start up normally instead of having to do this. Changing my permissions for exuberance using the root account saves the changes, but doesn't actually change anything. I still can't do the same things on my exuberance account.

</wall of text>

So... any helpful insight or suggestions? In case it matters, I'm running a 64-bit system on an HP laptop. Vista still works "fine" (as well as it normally does, but slightly confused about the hard drive having a partition with a file system it doesn't like, but it doesn't actually mess anything it) and it remembers all my settings and everything on my exuberance account (and I assume root does too, but I haven't customized it yet because I was hoping to be able to use my main account like I should be able to)

---

### Post by Exüberance on 2009-11-05
EDIT: Semi-sort-of-kindof-almost fixed.

I followed the instructions [here]("https://answers.launchpad.net/ubuntu/+question/85598") (replacing his username with my own, of course) and that "fixed" the problem. Kind of. Technically it did resolve this problem, but instead introduced a more interesting problem. This problem is technically solved now, though.

---

