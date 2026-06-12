---
title: "Lost my desktop icons and right-click, log attached"
date: 2011-10-07
forum: General Help
---

### Post by L a r r y on 2011-10-07
I installed an NVIDIA driver and indeed it does support 1152x8864 resolution, the 4:3 resolution between 1024x768 and 1280x1024.

But it was a sloppy installation:  I told it to install, gave my password and waited for it to finish.  It didn't do anything, so I closed the program, It wouldn't close and I restarted the computer.

Now the hardware devices say I am using the new driver, the driver is incompatible with Preferences ==> Monitors,  Do I want to use the NVIDIA tool instead?  Yes.

The NVIDIA tool couldn't access something, so I went to uninstall the driver using Hardware Drivers.  It ended up reinstalling NVIDIA, and then I had a whole range of resolutions, including 1152864.

I set my resolution and had everything looking good.  But it could not parse my /etc/X11/xorg.conf when I attempted to save my resolution settings.

I sudo nautilus and navigate to /etc/X11, and renamed xorg.conf to 1xorg.conf, then created a new empty file, named xorg.conf.

I then successfully saved my resolution settings and viewed the resulting xorg.conf.  It appeared to be complete, listing keyboard and mouse as well as video settings.

I auto-configured my monitor and the Desktop looks great.

Restart.

Panels come up and background comes up.  No context menu for right-click.  No cursors.

I navigate to my Desktop in Places, and the folder named Desktop is present and filled with everything that should be on the desktop.

A look in my home folder with Terminal, ls -l shows my permissions as I would expect them to be,there is a "Desktop folder icon" representing the desktop folder,versus the plain vanilla envelope (yes, it's supposed to be "manila!").

I had three programs that did not start when I restarted the computer, I sent the reports in and canceled the Firefox that came up each time for me to send a bug report in to Launchpad.

There is this thread titled [_**[ubuntu] Desktop Icons Missing, No Right-Click, etc**_]("http://ubuntuforums.org/showthread.php?t=849089") that covers this topic elsewhere on this forum.

Suggested there is to [I]
sudo apt-get install ubuntu-desktop[/I] which resulted in my already having the latest software installed, no changes made.

User "mcduck" offered this:  "[I]HAve you tried actually starting Nautilus? (As that sounds like for some reason or other Nautilus wasn't started).

Just open a terminal and run "nautilus &".[/I]

[B][FONT="Courier New"]$ nautilus &
[1] 1874[/FONT][/B]

This was my result from the Terminal,and a Nautilus window came up.

Well, **WELL,** Well!

I run that *nautlus &* _again_ and I saw different number on the Terminal, another window opened, but I also have an icon on the Desktop!

Here is the result of my second run:

[B][FONT="Courier New"]$ nautilus &
[2] 1885
[1]   Done                    nautilus
[/FONT][/B]

So I had to run it twice:```
me@Fast:~$ nautilus &
[1] 1874
me@Fast:~$ nautilus &
[2] 1885
[1]   Done                    nautilus
me@Fast:~$ 

```

OK I will post this, and then restart and if need be I will either mark it solved or post a follow-up if I still encounter problems.

Larry

---

### Post by L a r r y on 2011-10-07
**_My video settings are all fouled up following reboot_**

After I posted my last, in which I had run the *nautlus &* twice and recovered my icons on the Desktop, I restarted the computer, and I was without Desktop icons and panels, and right-click.

CTRL+ALT+DEL was my only option short of a keyboard shortcut to run something (not familiar with those).  After the three-finger salute, I was given opportunity to reboot or shut down, among the choices available.

Eventually had to drag out a PS/2 keyboard, as my USB keyboard has no access to the grub2 menu, and did a package repair, and a restart, then did a video repair to defaults.

With defaults I am and I am not running the NVIDIA driver, back to the spot where Preferences ==> Monitors isn't supported by my driver, but the NVIDIA tool can't access the driver either.  But I have my stuff on the Desktop.

While I was off, I thought of running the Live CD and reinstalling the system.  But my home folder was totally invisible, and I guess that comes with Ubuntu 10.04 and ext4 file systems.

I tried to provide the Xorg.0.log contents, but when I previewed the post, there was no scroll mechanism on the CODE box, and no way to see the overflowed 

Thankscontents according to my preview.  

You tell me what you need and I will send it up.

---

