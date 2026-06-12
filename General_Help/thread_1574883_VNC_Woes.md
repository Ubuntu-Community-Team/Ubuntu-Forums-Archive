---
title: "VNC Woes"
date: 2010-09-14
forum: General Help
---

### Post by ICANSEEYOU7687 on 2010-09-14
I have tried several different vnc servers and many different guides, but I still cant get it to work exactly how I would like.

Since I do a lot of traveling, I really wanna have it set to use display :0, and to start at boot (in the case that I need to remotely reboot)

My main problem (is not that I cant get vnc to work) but I cant get it to work on display :0

Now I unistalled all of my VNC applications (including vino) and I reinstalled vnc4server

normally I would run a command like this to get everything to work

vnc4server :0 -httpport 5900 or somethign similar

but this only works for vnc4server :1 and above.  Whenever I try to start something on :0 it tells me there is already a vnc service started on that port and when I try to access :0 all I get is a gray screen with the old school crosshair and :1 (on 5901) works just fine, but starts a new X session

If I kill the vnc server... and start it again on :1, it still tells me the same thing about :0...im so confused.  I have forwarded the ports correctly in my router so I know thats an issue.

Please! any help?

---

### Post by asmoore82 on 2010-09-14
check out the howto in my signature

---

### Post by ICANSEEYOU7687 on 2010-09-14
thanks for the quick reply!

Ill give everything a run through and see how it works!

I messed with xrdp before but didnt really know what I was doing so I gave it up, haha, thanks

*EDIT*
Did everything as said, and I get "Job Failed to start"

so I was thinking that maybe I needed to chmod -x the file, but that didnt work either.

---

### Post by anglican on 2010-09-15
> **ICANSEEYOU7687 said:**
> I have tried several different vnc servers and many different guides, but I still cant get it to work exactly how I would like.

Since I do a lot of traveling, I really wanna have it set to use display :0, and to start at boot (in the case that I need to remotely reboot)

My main problem (is not that I cant get vnc to work) but I cant get it to work on display :0

Now I unistalled all of my VNC applications (including vino) and I reinstalled vnc4server

normally I would run a command like this to get everything to work

vnc4server :0 -httpport 5900 or somethign similar

but this only works for vnc4server :1 and above.  Whenever I try to start something on :0 it tells me there is already a vnc service started on that port and when I try to access :0 all I get is a gray screen with the old school crosshair and :1 (on 5901) works just fine, but starts a new X session

If I kill the vnc server... and start it again on :1, it still tells me the same thing about :0...im so confused.  I have forwarded the ports correctly in my router so I know thats an issue.

Please! any help?
Try:
```
sudo apt-get install x11vnc
x11vnc -display :0 -usepw -ncache 10 -q
```H

---

### Post by ICANSEEYOU7687 on 2010-09-15
that has magically worked....

I dunno why this was so simple...and everything else I tried would not work...

---

### Post by ICANSEEYOU7687 on 2010-09-15
It works, but it does so strangely.

If i put this into putty, or even a terminal window on the local machine and I run
x11vnc -display :0 -usepw -ncache 10 -q

it works as intended, but once I connect with VNC, and then disconnect, I have to run the script again to work... which isnt too big of a deal.  If i ever wanna VNC, I guess I can just SSH in and then run the command, and then run vnc

x11vnc -display :0 -usepw -ncache 10 -q &
 Does the same thing.  Any thought?

---

### Post by anglican on 2010-09-16
> **ICANSEEYOU7687 said:**
> It works, but it does so strangely.

If i put this into putty, or even a terminal window on the local machine and I run
x11vnc -display :0 -usepw -ncache 10 -q

it works as intended, but once I connect with VNC, and then disconnect, I have to run the script again to work... which isnt too big of a deal.  If i ever wanna VNC, I guess I can just SSH in and then run the command, and then run vnc

x11vnc -display :0 -usepw -ncache 10 -q &
 Does the same thing.  Any thought?
Yes, I hadn't paid close enough attention to your requirements! From the x11vnc man page:
>        -once

              Exit after the first successfully connected viewer disconnects,
              opposite of -forever. This is the Default.

       -forever

              Keep listening for more connections rather than exiting as soon
              as the first client(s) disconnect. Same as -many
So just add "-forever" to the command line.

H

---

### Post by HermanAB on 2010-09-16
Yah well, the thing that always bugs me, is that since you got SSH to work, why on earth do you want to run VNC on top of it?  Is it just to make it slow and clunky? Probably not...

Your local machine already has a desktop, so why overwrite it with another one, when all you need is a remote taskbar:
$ ssh -X -C -c blowfish user@server gnome-panel

and then you can go click happy on the remote machine and applications will run transparently on the local desktop.

BTW, that works from Windows too.  Using either Cygwin or Xming and PuTTY, you can make remote programs run transparently on Windows too.

---

### Post by anglican on 2010-09-16
> **HermanAB said:**
> Yah well, the thing that always bugs me, is that since you got SSH to work, why on earth do you want to run VNC on top of it?  Is it just to make it slow and clunky? Probably not...
Well in my case it's because I need to access software that is running equipment connected to the remote computer. A second instance of the program is obviously not permitted - it would be dangerous to have two different users trying to control the equipment at the same time! So I need to access the existing instance of the program and not try and open a new one. However...
> **HermanAB said:**
> Your local machine already has a desktop, so why overwrite it with another one, when all you need is a remote taskbar:
$ ssh -X -C -c blowfish user@server gnome-panel

and then you can go click happy on the remote machine and applications will run transparently on the local desktop.

BTW, that works from Windows too.  Using either Cygwin or Xming and PuTTY, you can make remote programs run transparently on Windows too.Is all a fair point if all you want to do is run a some program on the remote computer rather than access an existing instance.;)

H

---

