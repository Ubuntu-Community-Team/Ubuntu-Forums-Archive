---
title: "Ubuntu crashes during big files copy or unzip"
date: 2010-12-08
forum: General Help
---

### Post by sim0ne on 2010-12-08
Hi, I've got a big problem with my ubuntu because it crashes witout error messages during copy of big files (up to 600 Mb) or when unzip (extract) big files.
Without any error message it freezes, I can't move mouse and the keyboard doesn't work.
When I unzip big dimensions files It crashes and after some time the notebook turns off.
I've tried using "top" in another terminal during operations but there's not suspect activities or big consumption of memory.
I also want to say that I've got more than 20Gb of free space, so It's not a space problem.
Using Windows or using the Live CD of the my same Ubuntu version all works perfectly

What can I do?

Is it a OS bug? Is there a solution for my problem or a way to find an error message and solve it? [Even using -v option during copy non error message appear before system crash]

Thanks to all who want to help me!

Bye

Simone

p.s. My Ubuntu version is 10.010 - Maverick Meerkat with GNOME Desktop 2.32.0

---

### Post by dcstar on 2010-12-08
> **sim0ne said:**
> Hi, I've got a big problem with my ubuntu because it crashes witout error messages during copy of big files (up to 600 Mb) or when unzip (extract) big files.
Without any error message it freezes, I can't move mouse and the keyboard doesn't work.
........

This may be worth trying:

[http://ubuntuforums.org/showthread.php?t=1625233](http://ubuntuforums.org/showthread.php?t=1625233)

---

### Post by sim0ne on 2010-12-09
IT WORKS!! IT WORKS!!
Thank you David!! Thank you David!! Thank you David!!!
I'm very happy for that!!!

For ubuntu fresh users, go directly to [http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html](http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html)

I backup here the a backup page of the script written in the link:

Open terminal and paste:

> cd
wget [http://launchpadlibrarian.net/59511828/cgroup_patch](http://launchpadlibrarian.net/59511828/cgroup_patch)
chmod +x cgroup_patch
sudo ./cgroup_patch

then paste:

> sudo /etc/rc.local 

and restart PC (even if you think it's unnecessary It's better!)

In case of errors write manually all the script:

> **Use it in Ubuntu**


**[COLOR=red]Update (November  24): because many people had trouble following the instructions below,  there is now a script that automatically does everything for you. See: [Script To Automatically Apply the "200 Lines Kernel Patch" Alternative In Ubuntu]("http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html")[/COLOR]**


**To use Lennart's solution in Ubuntu (_not tested_ - thanks to Lsh for this), you have to replace "/sys/fs" with "/dev"**. So you would have to add the following commands in your */etc/rc.local* (open it with: *sudo gedit /etc/rc.local*) file,** above the "exit 0" line**:

mkdir -p /dev/cgroup/cpu
mount -t cgroup cgroup /dev/cgroup/cpu -o cpu
mkdir -m 0777 /dev/cgroup/cpu/user
echo "/usr/local/sbin/cgroup_clean" > /dev/cgroup/cpu/release_agent
and make it executable:
sudo chmod +x /etc/rc.local
And then add the following to your *~/.bashrc* file (to open it: *gedit ~/.bashrc*):

if [ "$PS1" ] ; then  
   mkdir -p -m 0700 /dev/cgroup/cpu/user/$$ > /dev/null 2>&1
   echo $$ > /dev/cgroup/cpu/user/$$/tasks
   echo "1" > /dev/cgroup/cpu/user/$$/notify_on_release
fi
Run the following command:
sudo gedit /usr/local/sbin/cgroup_clean
And paste this:

#!/bin/sh
if [ "$*" != "/user" ]; then
rmdir /dev/cgroup/cpu/$*
fi
then save the file and make it executable:
sudo chmod +x /usr/local/sbin/cgroup_clean
And finally, restart the computer or manually run the /etc/rc.local file ("sudo /etc/rc.local").

Bye!!!!

---

### Post by sim0ne on 2010-12-15
I'm really sorry but I have to re-open this thread because my problems persists, even if I've tried to follow **dcstar** advices so, dear friends, forget my last post...

My Ubuntu 10.10 crashes when I copy files with Nautilus and also when I copy files with terminal using ```
 cp 
``` command.

It crashes also using ```
 cat 
``` command to join avi files.

I don't know if it's possible to save a logfile. If yes tell me how, because I'd like to show it to you for having an help and understand what's the matter. The biggest problem is that when my notebook crashes I have to turn it off manually, without any chance to save files or input any command.

I really need an help so your participation is welcome!

---

