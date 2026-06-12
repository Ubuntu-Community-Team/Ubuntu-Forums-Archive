---
title: "Ubuntu 10.04 is awful: Abandon or Fix, need your help?"
date: 2010-07-30
forum: General Help
---

### Post by spookware on 2010-07-30
So I have been having nothing but problems with 10.04 and considering this is an LTS I am thinking of just abandoning Ubuntu but I wanted to ask around and see what others think. Admittedly this post is a bit of a rant but I also honestly asking for feedback on some of my proposed fix ideas so bear with me. I am not just trolling or lashing out. 

The story:
My first problem with 10.04 was a kernel bug that caused a 60 second or so pause in bootup. I did all the work myself and some 70 or so kernel compiles later I tracked it down. See the bug report here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595448](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/595448). But the bug report has been absolutely silent. No comment from the devs or anything. What am I supposed to do if I just hit a wall of deafening silence, especially since I provided the solution?

Next up I run in to trouble with mountall (the current bane of my existence). The maintainer for this thing is insane. He is not going to fix simple and obvious bugs in for an LTS release. Take a look at this report: [https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/523587](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/523587)
So what Mr. Remnant is saying is that for the entire lifespan of an LTS release you can not ever put /usr on a separate partition. His solution is to track Maverick. Are you kidding me?? This is an LTS release. You are supposed to back port fixes to an LTS release.

Next when trying to trouble shoot this thing I tried typing in "man mountall". give it a shot yourself it will make you laugh or cry. The man page basically has no real documentation in it outside of saying that "mountall" is just a temporary kludge until upstart is actually complete. So in an LTS release the program that is responsible for mounting your filesystems is a bunch of throwaway code. I mean that is only the most essential thing the init system does. 

So next I download the source for mountall only to find it is a single giant C file with nary a comment in site. A few of the global variables have a comment line to tell you what they are but then the code itself has almost zero comments. 

So for the time being I ignore mountall and move on to getting union mounts working. Much to my surprise. sudo apt-get install aufs-tools returns an error. Thats right, because its not packed with 10.04. It seems ubuntu decided to ship a new version of aufs but debian had not finished packaging the new version of aufs-tools. So an LTS release has the aufs module built in to the kernel but no user space tools to use it. WTF!!!!! Again the solution is to wait for 10.10 when it should be ready. Hello?!?! 10.04 is the LTS release right, not 10.10?

So I go and grab the aufs-tools from the debian NEW-QUEUE and install those. Great now I can use aufs that ships with lucid. Oh wait I can't because of my old friend mountall. It seems what mountall does is parse /etc/fstab and construct a dependency graph of mount points and their associated devices. It then waits for the device to apear via udev and then tries to mount the file system in question. It is smart enough to understand that / needs to be mounted before /var but thats about it. For example it cant reliably mount aufs file systems because it often tries to mount the aufs file system before the underlying file systems are mounted. Folks who are using crypto loop back file systems are having the same problem. In all cases a simple mount -a does works but mountall can't handle what the old venerable tool can.

So at this point I am just about ready to give up completely. Between the junky kernel, Grub2 (whos brilliant idea was it to require a functioning system to run an update-grub script to repair a broken grub conf, if I could boot I wouldn't need to repair the grub conf), upstart, plymouth, policykit, and the most hated of all "mountall" I am at my whits end.

So now I ask you, I need a box for getting real work done including complex file system layout. Should I just abandon this release and go with Debian testing or RHEL5, or should I try to fix mountall.

Actually patching mountall is out of the question. I have read the code and for the life of me I can't tell all of what it is supposed to be doing. Its hard to follow as it is communicating with two other processes (Plymouth,  and Dbus). Heck I can't even tell when it runs because if you look at the package details for both upstart and mountall you will see that they both provide /sbin/init, which makes me wonder which one is actually running and when.

My idea for getting the broken as hell mountall to work is to replace it. What I am wondering is if a simple bash script that say waits for 10 seconds (long enough for networking and and the device files to appear) and then runs mount -a and then emits all of the upstart events that mountall is supposed to emit to tell /sbin/init to go forward with the boot. 

What do you all think? will that work? I am not sure because it looks like mountall hangs around for a while and I am not sure what triggers it to close out. 

This is really sad frankly. I have been using ubuntu exclusively for years but this release is nothing but pain. I don't want to go learn another distro if I can avoid it but putting everything on one big root partition is just not an option for me. 

Cheers and thanks in advance for any insight in to how to get mountall to not suck.
Spookware

---

### Post by sydbat on 2010-07-30
tl;dr

What is your hardware? Could be that 10.04 is too much for it, if it is significantly old. I have yet to run into any major problem with 10.04 (I know..."works for me"), but both my boxen are less than 6 years old.

Also, there are many, many, many, etc, other distros out there. Why not try one of those and see if they work better with your hardware. The choice is yours.

---

### Post by philinux on 2010-07-30
spookware,

Why does /usr have to be on it's own partition?

---

### Post by prodigy_ on 2010-07-30
I'd suggest you to move to another distro. Try Fedora 13. I did and I liked it way more than all the previous Fedora releases.

---

### Post by snowpine on 2010-07-30
Hi Spookware, I think you know what you need to do (Red Hat, CentOS, Debian Stable, etc). :) Best of luck with your new choice of distro!

---

### Post by prodigy_ on 2010-07-30
> **snowpine said:**
> CentOS
Yeah, might want to try CentOS too. It's very stable and bug-free. A bit slow for a regular desktop, but really good for a workstation/server.

---

### Post by snowpine on 2010-07-30
> **prodigy_ said:**
> Yeah, might want to try CentOS too. It's very stable and bug-free. A bit slow for a regular desktop, but really good for a workstation/server.

I disagree; I have CentOS 5.5 (full Gnome desktop) installed on a pentium 3 with 128mb ram! CentOS is much "lighter" and faster than Ubuntu will ever be (in my experience/opinion). I will agree it is a little slow to boot sometimes, but that is largely irrelevant for my needs.

---

### Post by dnguyen1963 on 2010-07-30
me too...10.04 LTS was nothing but trouble.  I have since been using PCLinuxOS without a problem.  Fedora 13 is fine too, but I did have one instance of random freeze (reboot took care of the problem).

---

### Post by prodigy_ on 2010-07-30
> **snowpine said:**
> I will agree it is a little slow to boot sometimes
Yeah, I meant boot times, nothing else. This may be annoying, however, unless your PC is on 24/7.

---

### Post by spookware on 2010-07-30
> **sydbat said:**
> tl;dr

What is your hardware? Could be that 10.04 is too much for it, if it is significantly old. I have yet to run into any major problem with 10.04 (I know..."works for me"), but both my boxen are less than 6 years old.

Also, there are many, many, many, etc, other distros out there. Why not try one of those and see if they work better with your hardware. The choice is yours.
All hardware is quite new and VERY VERY standard. I am not new to Linux. I thought that should have been clear by the fact that I new how to bisect my kernel. So I am very particular with my hardware. 

I have lots of hardware. A Dell T710 Server with 24 cores and 48GB of ram, lots of VMWare images, two bog standard development workstations. Both are built using Intels own "Stable Image Platform" motherboards. IOW these things are meant to be as standard as you get and supported for ages. One is an Intel DQ45CB and the other is an Intel DQ57TM. These boards have intel chipsets, with intel nics and intel graphics. everything in them is standard and supported well by Linux. Heck that DQ45CB is so well supported by Intel that is still has a dedicated team doing regular BIOS releases even though the board is a couple years old now.

The Dell Sever is even on Ubuntus own hardware compatibility list.

---

### Post by spookware on 2010-07-30
> **philinux said:**
> spookware,

Why does /usr have to be on it's own partition?
Well there are a ton of reasons to put /usr on a separate partition. 
1. NFS mounted /usr
2. /usr on LVM
3. read only /usr (as recommended in the official debian security guide) 
4. union mounted /usr
etc....

i mean the whole point of the Linux File System Hierarchy standard is so that /usr can be separated from /. But apparently this was not even a test case for the upstart maintainer.

---

### Post by spookware on 2010-07-30
So how about the proposed fix idea? Is there anyone out there that understands how upstart and mountall interact? 

I know ubuntu like the back of my hand so I am loath to switch distros over this issue but I just don't know what to do. All I really want is for the old behavior in prior releases (prior to 9.10) where you fire up mount -a and let it do its thing. 

But I can't simply edit /etc/init/mountall.conf and replace the line that invokes mountall with something else because upstart will wait for events that mountall is supposed to generate before proceeding with the rest of the bootup process.

--------------
Maybe an alternative idea is to patch all of the /etc/init/*.conf files that depend on any of the following events:
mounted, mounting, virtual-filesystems, local-filesystems, remote-filesystems, all-swaps, filesystem

to instead wait on a new event, lets call it "my-fs". Then I modify my fstab to only contain the very basic mounts like /, /usr, and /var. I then create my own upstart job definition that waits on "filesystem" which should be the final event emitted by mountall (for what I can tell anyway). It then does the more complex mounts in a script (stuff like NFS, CIFS, or union mounts) and when its done it emits the "my-fs" event 

Maybe this is cleaner than trying to out right replace mountall. Any thoughts? I could use anyones input that has some experience with this. 

Cheers,
Spookware

---

### Post by prodigy_ on 2010-07-30
> **spookware said:**
> Is there anyone out there that understands how upstart and mountall interact?
Not me, although I understand the purpose of Upstart quite well. By the way, you might find [this article](http://0pointer.de/blog/projects/systemd.html) an interesting reading. It's about **systemd** which is going to replace Upstart in the upcoming Fedora 14. A very promising concept, although it's still in development. The source is available, maybe it'll help you somehow.

---

### Post by libssd on 2010-07-30
> **spookware said:**
> This is really sad frankly. I have been using ubuntu exclusively for years but this release is nothing but pain. I don't want to go learn another distro if I can avoid it but putting everything on one big root partition is just not an option for me....
Spookware
Unless I am misreading your quote, previous versions of Ubuntu were working for you. If so, why not revert to the last version that was stable for you?

9.04 was my introduction to Ubuntu; 9.10 solved a few compatibility issues, and I initially had major problems with 10.04 and grub2. However, after RTFM, I solved the grub2 problems, and 10.04 has been rock solid for me, with zero hardware issues. However, I realize that others have had different experiences.

---

### Post by qdub on 2010-07-30
I've had problem after problem with 10.04 as well and finally gave up since spending hours trying to resolve everything didn't make sense. I'm hoping a lot of fixes are rolled into 10.10 but in the meantime I'm still running 9.10 and using 10.04 repositories for a few things. Some of these are obviously testing repos but they're working great. I'm not into a lot of the other distros and this has been a pretty good compromise so far.

---

### Post by linux18 on 2010-07-30
I've got a command line distro (see sig) based on ubuntu. it's super fast and I upload a new version every week.

---

### Post by spookware on 2010-07-30
> **libssd said:**
> Unless I am misreading your quote, previous versions of Ubuntu were working for you. If so, why not revert to the last version that was stable for you?

9.04 was my introduction to Ubuntu; 9.10 solved a few compatibility issues, and I initially had major problems with 10.04 and grub2. However, after RTFM, I solved the grub2 problems, and 10.04 has been rock solid for me, with zero hardware issues. However, I realize that others have had different experiences.
Because 10.04 is the LTS release. The last LTS I can go back to is 8.04 which is very old at this point. If I go back that far I am going to run in to hardware compat problems with systems and besides its only going to be supported for one more year.

Problem is that right now there are no good Linux distros that will be well supported for a few years. I guess if I can't resolve this problem I will just revert to something like 9.04 and plan to wipe my servers and reset them up in a year or so when BTRFS is stabilized or RHEL6 comes out or Ubuntu gets its init system sorted out. As I said this is really a downer for me because if it was anything but the init system I could probably work around it. I mean I can handle compiling and installing my own stuff to /usr/local for pretty much anything else. But there is not good way to "override" the ubuntu init system.

Anyway I am still willing to invest some more energy in fixing up ubuntus init system so if anyone out here has experience I would appreciate the input.

---

### Post by snowpine on 2010-07-30
> **spookware said:**
> Problem is that right now there are no good Linux distros that will be well supported for a few years.

:LOL:

Good luck! ;)

---

### Post by spookware on 2010-07-30
here is yet another example.
[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/603363](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/603363)

This one also prevents /usr from existing on a separate partition and again its fixed in 10.10 but not yet back-ported to 10.04?!?

---

### Post by snowpine on 2010-07-30
> **spookware said:**
> here is yet another example.
[https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/603363](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/603363)

This one also prevents /usr from existing on a separate partition and again its fixed in 10.10 but not yet back-ported to 10.04?!?

This is typical of Ubuntu's development cycle. Ubuntu is a forward-thinking distro always focused on the *next* release rather than retroactively improving past releases. Many 8.04 bugs are still open, and there is no reason to believe 10.04 will be any different. The entire Ubuntu project is designed as a "showcase" for the latest in Linux on the desktop, not a stable, enterprise platform like Red Hat, CentOS, Debian, SLED, etc.

I think you already know you need a more stable distro and you're just venting at this point. ;)

---

### Post by spookware on 2010-07-30
> **snowpine said:**
> This is typical of Ubuntu's development cycle. Ubuntu is a forward-thinking distro always focused on the *next* release rather than retroactively improving past releases. Many 8.04 bugs are still open, and there is no reason to believe 10.04 will be any different. The entire Ubuntu project is designed as a "showcase" for the latest in Linux on the desktop, not a stable, enterprise platform like Red Hat, CentOS, Debian, SLED, etc.

I think you already know you need a more stable distro and you're just venting at this point. ;)
Actually I don't need a more stable distro. I don't need my packages to stay at one version for five years. As I said I have been an happy ubuntu user for many years now. This is the first release (sadly an LTS at that) that is causing such problems. 

As for what Ubuntu is I have to disagree. I think canonical disagrees with that considering they offer LTS support contracts. I would refer you to ubuntu's own policy on this:
[https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)
Specifically, "Bugs which represent severe regressions from the previous release of Ubuntu."

Being unable to mount /usr on a separate partition is a big regression. being unable to use aufs is a big regression. Also I think your memory might be a bit fuzzy. The ubuntu team did quite a good job getting fixes in for 8.04. Sure I had problems with that release but if you recall by now they had already released the 8.04.1 update disk with loads of bug fixes.

---

