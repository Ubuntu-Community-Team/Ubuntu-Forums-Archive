---
title: "File Roller 2.26.1 in J.J.-64"
date: 2009-08-28
forum: General Help
---

### Post by DeMus on 2009-08-28
Hi all,
At the moment I am unarchiving a bunch of rar files and the computer doesn't let me do anything else. The computer is unresponsive.
I have a Q6600, running at 3GHz instead of the normal 2.4GHz, I have 4GB ram and they are hardly used. Look at the screenshot which makes it clear.
Nevertheless I simply have to wait until this process is over because all I get are dark-grey screens of my other running programs, like FF for example. It's not only FF, they all do it.
I can imagine File Roller takes the complete CPU and so the PC is busy with that one program. But it is not doing that. CPU load is very low, not more than 20% per core.
Memory is not full, only about 1/3 is used.

Still I can drink coffee and wait. Anybody an idea why this happens? Why isn't File Roller using for example one core to its maximum and leave the other 3 for other programs, or to make things faster, use all 4 cores to their maximum and get it over with?
Now it runs slow but it is blocking the complete PC.

Please help. This is annoying me very much, and for a long time already.

---

### Post by DeMus on 2009-08-28
Filed a bug report about this. Hope things will change.

---

### Post by Johnny B on 2009-08-29
i have jaunty 64 bit dual core 3 ghz with a nVidia 8500GT and i cant reproduce the problem.
try opening file-roller with:
> nice -n 20 file-roller

---

### Post by DeMus on 2009-08-29
> **Johnny B said:**
> i have jaunty 64 bit dual core 3 ghz with a nVidia 8500GT and i cant reproduce the problem.
try opening file-roller with:

You mean to tell me the program runs fine on your computer? When you look in system monitor, what do the graphs tell you about the cpu load?
This would mean something is wrong in my hardware, since I also had this with Hardy already. Now I use Jaunty.

---

### Post by Johnny B on 2009-08-29
> **DeMus said:**
> You mean to tell me the program runs fine on your computer? When you look in system monitor, what do the graphs tell you about the cpu load?
This would mean something is wrong in my hardware, since I also had this with Hardy already. Now I use Jaunty.

yes, cpu usage averaged 3% while adding 5gb worth of files, and peaked at 15%

---

### Post by DeMus on 2009-08-29
> **Johnny B said:**
> yes, cpu usage averaged 3% while adding 5gb worth of files, and peaked at 15%

It looks a bit better, but still I get messages from other running programs that they can't do what they supposed to do, including the dark grey FF screen while typing this.
Well, I filed the bug, let's see what comes out of that. Thanks for your help.

Extra:

I did get this in terminal when closing file-roller:

(file-roller:1607): Gtk-WARNING **: Attempting to read the recently used resources file at `/home/jan/.recently-used.xbel', but the parser failed: Error reading file '/home/jan/.recently-used.xbel': Is a directory.

(file-roller:1607): Gtk-WARNING **: Attempting to store changes into `/home/jan/.recently-used.xbel', but failed: Failed to rename file '/home/jan/.recently-used.xbel.LE1JZU' to '/home/jan/.recently-used.xbel': g_rename() failed: Is a directory

(file-roller:1607): Gtk-WARNING **: Attempting to store changes into `/home/jan/.recently-used.xbel', but failed: Failed to rename file '/home/jan/.recently-used.xbel.VAC7YU' to '/home/jan/.recently-used.xbel': g_rename() failed: Is a directory

(file-roller:1607): Gtk-WARNING **: Attempting to store changes into `/home/jan/.recently-used.xbel', but failed: Failed to rename file '/home/jan/.recently-used.xbel.2U1FZU' to '/home/jan/.recently-used.xbel': g_rename() failed: Is a directory

---

### Post by fluffman86 on 2009-08-29
A few things:
Can you post a screenshot of the other tabs while this is happening?  Specifically the processes tab, showing what file-roller is doing.

Can you post a link to the bug report?

Thanks!

---

### Post by DeMus on 2009-08-29
> **fluffman86 said:**
> A few things:
Can you post a screenshot of the other tabs while this is happening?  Specifically the processes tab, showing what file-roller is doing.

Can you post a link to the bug report?

Thanks!

Here is the screenshot you asked for. As you can see unrar is doing almost nothing, just a few percent. Still it manages to slow down everything.

The link to the bugreport is [_here_]("https://bugs.launchpad.net/bugs/420904").

---

### Post by fluffman86 on 2009-08-29
Thanks.

Try Johnny B's command again, but this time change the 20 to -20
```
nice -n -20 file-roller 
```
This will make file-roller run in highest priority instead of lowest.  You can also change this from the System Monitor.

Another thought is that it could be a bottleneck on reading and writing to the same hard drive.  Just something to keep in mind.

---

### Post by DeMus on 2009-08-29
> **fluffman86 said:**
> Thanks.

Try Johnny B's command again, but this time change the 20 to -20
```
nice -n -20 file-roller 
```
This will make file-roller run in highest priority instead of lowest.  You can also change this from the System Monitor.

Another thought is that it could be a bottleneck on reading and writing to the same hard drive.  Just something to keep in mind.

I've been thinking about the idea of the disks as well. Isn't much I can do about it, is there?

Now file-roller (which I had to start with sudo this time since I had no privileges to change the nice value to -20) is occupying the pc so much, system monitor doesn't even show it. I tried top in another terminal and got a high score of 42%, average it was around 20%.

Thanks for all your help, but I have a feeling it is a hardware issue, could be the disk although it's not a slow one. Can I measure the disk activity somewhere?

---

