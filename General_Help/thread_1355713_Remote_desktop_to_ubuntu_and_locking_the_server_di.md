---
title: "Remote desktop to ubuntu and locking the server display"
date: 2009-12-15
forum: General Help
---

### Post by magneze on 2009-12-15
Hi,

I'd like to control my Ubuntu Karmic install remotely but without the ability for what I'm doing to be shown on the remote display.

Similar to the way Windows XP works with remote desktop - when someone is connected then it just shows a locked screen and doesn't actually display what is being done.

Is this possible? I don't mind which protocol I use, but he above requirement is very important security wise.

... and no I can't turn off the monitor because it's an Apple and doesn't have an off switch for the monitor. :(

Thanks .. :)

---

### Post by cj13579 on 2009-12-15
If you are happy using the command line you could use SSH. Take a look at:

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

---

### Post by magneze on 2009-12-15
No, I need graphical access.

I know I can do "ssh -X .." etc but that is really slow.

VNC works apart from the fact that what I do is visible remotely at that someone can just sit at my terminal and take control. It's a security issue.

---

### Post by cj13579 on 2009-12-15
In which case you could....

1.On the remote machine: install vncserver:

```
sudo apt-get install vnc4server
```

2. Create a second desktop that will run in the background and create a password for it:

```
sudo vncserver :1
```

3. Edit $HOME/.vnc/xstartup to look like the following using fav text editor:

```

#!/bin/sh

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc

#[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
#[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
#xsetroot -solid grey
#vncconfig -iconic &
#xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &

```

4. Restart vncserver:

```

sudo vncserver -kill :1
sudo vncserver :1

```

5. Use vnc viewer to access this desktop and instead of port 5900 repleace the end digit with desktop number. E.g. to connect to 192.168.0.10 desktop :1 it would be 192.168.0.10::5901. The desktop that the user sees by default is desktop :0.

Hope this helps!

---

### Post by magneze on 2009-12-15
That almost works. I have a few issues though.

I can see my desktop if I don't edit $HOME/.vnc/xstartup ... but if I change it to what you said then I get nothing but a grey box with an X cursor in it.

Once in the desktop my keyboard doesn't work - all the keys seems to be mapped to something else...

So near and yet ... so far :)

---

### Post by cj13579 on 2009-12-15
Try this for your $HOME/.vnc/xstartup file:

```
    #!/bin/sh

    xrdb $HOME/.Xresources
    xsetroot -solid grey
    #x-terminal-emulator -geometry 80×24+10+10 -ls -title &#8220;$VNCDESKTOP Desktop&#8221; &
    #x-window-manager &
    export XKL_XMODMAP_DISABLE=1
    /etc/X11/Xsession
```

---

### Post by magneze on 2009-12-16
That's done the trick - thank you!

What did it do?

---

### Post by cj13579 on 2009-12-16
It seems as though the keyboard mapping gets all corrupted. This just disables the remapping.

The crucial line is:

```
export XKL_XMODMAP_DISABLE=1
```

Glad I could help. You should mark your thread as solved now if you are happy it is working. It's good to keep a tidy house!!

---

### Post by 3rdalbum on 2009-12-16
> **magneze said:**
> No, I need graphical access.

I know I can do "ssh -X .." etc but that is really slow.

Do ssh -Y instead. It's faster. Having said that, ssh -X should still be fast enough over a local area network.

---

### Post by magneze on 2009-12-16
> **cj13579 said:**
> It seems as though the keyboard mapping gets all corrupted. This just disables the remapping.

The crucial line is:

```
export XKL_XMODMAP_DISABLE=1
```

Glad I could help. You should mark your thread as solved now if you are happy it is working. It's good to keep a tidy house!!Done. Many thanks for your help again. :)

---

### Post by hernanp on 2010-05-28
I work in my office PC and at home and need to share my office desktop (display 0) because I leave my applications running there (mail client, etc), is there a simple way to do this?
I found a way in [http://blog.nistu.de/A_kiosk_setup_with_nxclient.html](http://blog.nistu.de/A_kiosk_setup_with_nxclient.html) but it seems that there is a performance penalty doing that way

Thanks

---

### Post by magneze on 2010-05-28
Oh, good bump. I actually now do this using NX because it creates a separate session.

I followed the instructions here: [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

NX is loads faster than VNC too. :guitar:

---

### Post by cgarre on 2011-09-30
i think i will try the first approach where cj13579 suggested the changes. i dont know why people ask to use different session and nx etc ... vnc is pretty fine. The moment you ask nx to shadow it also becomes slow. I dont use NX at all now, it is heavy too. So all people are looking for is locking the screen when it is in vnc session. If you use different sessions then when you come back to office you have different things on the desktop ... all you want is seameless working either at home or office. So i hope people realize that there is no other alternative (i hope cj13579's method ) works for me, i will try and post my results here. I have been looking for this for a long time.

---

### Post by arnie001 on 2012-06-04
In case your resolution is too low, do this:

*vncserver -geometry 1024x768 :1*

to get resolutions that you want. I have tried 1680x1050 and that worked too.

---

