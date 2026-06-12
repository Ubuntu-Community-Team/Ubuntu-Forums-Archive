---
title: "TightVNC Server 64 bit SEGFAULT Issues"
date: 2010-02-02
forum: General Help
---

### Post by rmccarri on 2010-02-02
Hi Everyone,
I've posted this on a different branch of the forum and haven't gotten any replies after months.  Perhaps it was in the wrong location.

Basically, I'm having terrible segfault issues with Tightvnc server.  I'm running Ubuntu 9.10 64 bit version.  The problem is that whenever I open anything that tries to use OpenGL, I get a glxinfo segfault which causes xtightvnc to also have a segfault.  I've been pulling my hair out for months looking for a solution to this.  Obviously, OpenGl is not supported under tightvnc.  I've tried TurboVNC and still had issues.  Is there any way to disable attempts to use OpenGL over VNC.  Is there something that I might be able to put in my xstartup file to avoid this issue?

Any help would be greatly appreciated.  This is the one remaining issue on an otherwise flawless Linux box.

---

### Post by Bystroi on 2010-06-14
I got the same issue with Ubuntu 10.04 desktop 64bit. Tightvnc sessions to my server get dropped due to TightVNC segfaults.

Did you manage any kind of a solution?

---

### Post by rmccarri on 2010-06-14
It's disappointing to see that the problem still lingers.  The only solution that I was able to find was to use X11VNC.  It's less than ideal as it connects to the X session, so you can't have a separate desktop open when someone else is using the computer.  However, I've found that just establishing an SSH session with the -X option (which diverts the X window to your local machine) is a fair compromise, albeit slow.

---

### Post by krunge on 2010-06-15
> **rmccarri said:**
> It's disappointing to see that the problem still lingers.  The only solution that I was able to find was to use X11VNC.  It's less than ideal as it connects to the X session, so you can't have a separate desktop open when someone else is using the computer.
If you install the 'xvfb' package you can run x11vnc with it -create option to create virtual (RAM only) X sessions:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-xvfb](http://www.karlrunge.com/x11vnc/faq.html#faq-xvfb)
[http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-create](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-create)[/INDENT]
It won't be as fast as vncserver/Xvnc, but it provides the same type of desktop and won't crash.

---

### Post by gmoore777 on 2010-07-29
I am having the same issue on 64-bit LucidLynx.

The tightvncserver crashes with this in the /var/log/syslog:
  Jul 29 16:51:06 bee02 kernel: [26781.194464] Xtightvnc[9827]: segfault at 7fffa1eec000 ip 000000000044e4f1 sp 00007fffa1ee98d0 error 6 in Xtightvnc[400000+17e000]

I can make it crash within minutes by merely trying to start up Update Manager or SynapticPackageManager fromo within my vnc viewer.

I'm using RealVNC client 4_1_3-x86_win32 on a Windows XP machine.

(trying to find an alternative to vino-server as that requires a user to log in first so that the vino-server will start up. That's unacceptable for remote users after machine reboots)

This product is DOA (Dead-On-Arrival)?

(would vnc4server behave the same way? Installing....)

---

### Post by gmoore777 on 2010-08-02
continuing,...

I also had 2 other users who also experienced the tightvncserver
crashing problem on their 64-bit LucidLynx machines. So this product is unstable within minutes.

I have now installed vnc4server and it's running smoothly
for about one hour. 
The client is not disconnecting, and the vnc4server is not crashing.

(I find it a bit strange that since both vnc4server and
 tightvncserver uses Xvnc under the covers that they would
 behave differently. I don't have time to investigate that
 difference. We will continue to use the vnc4server and will
 report any anomalies if we find any.)

---

### Post by gmoore777 on 2010-08-03
One thing that I had to do to get vnc4server started properly.
The ~/.vnc/xstartup file needs to be this:

#!/bin/sh
xrdb $HOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
#x-window-manager &
# Fix to make GNOME work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession

(and strangely enough this file above I got from the ~/.vnc/xstartup that gets created when I run tightvncserver. the xstartup file that gets created when I run vnc4server works but I get a gray background with one xterm window. No menus, etc.)

---

### Post by Bystroi on 2010-10-21
It still seems to be an issue. I have now alternate setup with Xvfb but it starts with empty X desktop and there are lots of issues with keys. 
I guess I'll try vnc4server then and see.

---

### Post by perspectoff on 2010-10-21
> **rmccarri said:**
> It's less than ideal as it connects to the X session, so you can't have a separate desktop open when someone else is using the computer.

Can you do that with any VNC server?

I thought only XDMCP could do that...

---

### Post by rmccarri on 2010-10-22
I could be wrong, but to my understanding, the tighvnc and vnc4 servers cannot connect to desktop :0, the X session that's running locally with the video card.  The X11 VNC server specifically either connects or creates a session (if no X session is running) using the video card, so only one session can be running at a time (and the session is channeled through the monitor, so anyone in the room can see what you are doing).

I'm currently having a key mapping issue with the X11VNC server, so I'm not even using that anymore.  Now, I just open an SSH connection with the -X option and run whatever X-based software I need diverting the display over the SSH tunnel.  It's pretty slow and not every program that I would need works, but it's serviceable.

---

### Post by krunge on 2010-10-23
> **rmccarri said:**
> 
I'm currently having a key mapping issue with the X11VNC server, so I'm not even using that anymore.
There is a recent change in ubuntu X desktop software that requires supplying the "-xkb" option to x11vnc to get the keyboard mapping correct.  Try it and see if it solves the problem you are seeing.

This setting, -xkb, is now the default in x11vnc for the past 6 months, but hasn't been picked up by debian/ubuntu yet.

---

### Post by ppk007 on 2010-10-31
This article shows you how to install the new tightvnc that fixes this problem.

[http://pietercvdmlinux.blogspot.com/2010/07/running-tightvncserver-on-ubuntu-1004.html](http://pietercvdmlinux.blogspot.com/2010/07/running-tightvncserver-on-ubuntu-1004.html)

I just installed it and haven't had any issues for the past hour.

YMMV.

---

### Post by wcorey on 2011-02-01
SO that leads to the next logical question where there is a new release of this out why hasn't Ubuntu upgraded existing users with a usable vnc especially since they dropped the old one that worked fine.

---

### Post by dnoyeb on 2011-05-09
Same problem.  Is there a bug report on this?

---

### Post by twignation on 2011-07-19
> **ppk007 said:**
> This article shows you how to install the new tightvnc that fixes this problem.

[http://pietercvdmlinux.blogspot.com/2010/07/running-tightvncserver-on-ubuntu-1004.html](http://pietercvdmlinux.blogspot.com/2010/07/running-tightvncserver-on-ubuntu-1004.html)

I just installed it and haven't had any issues for the past hour.

YMMV.

Has anyone else tried this, and found that it worked?

I have been using it for about 30 minutes now, and I have not had any problems

---

### Post by twignation on 2011-07-20
> **twignation said:**
> Has anyone else tried this, and found that it worked?

I have been using it for about 30 minutes now, and I have not had any problems

Actually strike that, I thought I had installed the new version correctly, but actually I didn't know what I was doing, and I was just running the old version still - which crashed out a few hours later.

Does anyone know of a slightly more detailed tutorial on how to install the new version? I can not get it to work....

---

### Post by twignation on 2011-07-20
> **dnoyeb said:**
> Same problem.  Is there a bug report on this?

I just put one up [https://bugs.launchpad.net/ubuntu/+source/tightvnc/+bug/813442](https://bugs.launchpad.net/ubuntu/+source/tightvnc/+bug/813442)

---

### Post by Chruchnar on 2011-10-26
> **krunge said:**
> If you install the 'xvfb' package you can run x11vnc with it -create option to create virtual (RAM only) X sessions:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-xvfb](http://www.karlrunge.com/x11vnc/faq.html#faq-xvfb)
[http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-create](http://www.karlrunge.com/x11vnc/x11vnc_opts.html#opt-create)
[/INDENT]It won't be as fast as vncserver/Xvnc, but it provides the same type of desktop and won't crash.
 
Just wanted to say a big thanks to this idea! I got so frustrated with TightVNC crashing, also the newer version. The other VNCs required an existing X server which is hard when running headless. 
 
This is a cool and flexible way to do it. I also found it much more responsive and better looking than TightVNC. Could run 1600x900 16bit but not 32 (not sure but I guess some kind of mem allocation issue?). I guess it's not very performant but I'm always connecting from a PC in another room so it's cool.
 
Thanks again!

---

### Post by krunge on 2011-10-26
> **rmccarri said:**
> 
I'm currently having a key mapping issue with the X11VNC server, so I'm not even using that anymore.  Now, I just open an SSH connection with the -X option and run whatever X-based software I need diverting the display over the SSH tunnel.  It's pretty slow and not every program that I would need works, but it's serviceable.

If you are using an older version of x11vnc, it may help to add the "-xkb" option if there are some problems with the keymappings.

---

### Post by DanaG on 2011-11-26
I've managed to get vnc4server to work with LightDM, with just a small amount of hackery.
I dpkg-diverted the stock Xvnc4 executable out of the way:
```
sudo dpkg-divert --local --add --rename /usr/bin/xvnc4.distrib
```
After the dpkg-divert, I used nano (text editor) to create a new wrapper script with the same name:
```
sudo nano /usr/bin/Xvnc4
```
```
#!/bin/sh -x 
if [ -e "$HOME/.vnc/passwd" ] ;
then
        exec Xvnc4.distrib -rfbauth "$HOME/.vnc/passwd" $@
else
        exec Xvnc4.distrib -SecurityTypes None $@
fi

```
Finally, I marked that wrapper script executable:
```
sudo chmod +x /usr/bin/Xvnc4
```


Oh yeah, and I had to edit lightdm.conf to set depth=16 for the VNC server; until I did so, the colors were all screwed up.

I'll have to double-check where the lightdm user's rfbauth file is actually supposed to go; this will let you set a password to connect to the lightdm VNC server itself.

---

