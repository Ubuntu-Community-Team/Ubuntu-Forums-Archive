---
title: "How to enable TCP connections to XServer?"
date: 2009-11-02
forum: General Help
---

### Post by phoenix49 on 2009-11-02
Hello there!

I need to enable TCP connections to my X server on Ubuntu Karmic, in order to run remote X applications via SSH. On older Ubuntu's I could just unmark "Deny TCP connections to Xserver" and restart GDM. But now, XServer is new, and has new gdmsetup.

Any help would be appreciated!

There was file called custom.conf in /etc/gdm, containing following string:

[security]

DisallowTCP=false

Thanks!

---

### Post by b12gold on 2009-11-02
sudo gedit /etc/gdm/gdm.schemas

find:

<schema>
      <key>security/DisallowTCP</key>
      <signature>b</signature>
      <default>true</default>
</schema>

shift from true to false:

<schema>
      <key>security/DisallowTCP</key>
      <signature>b</signature>
      <default>false</default>
</schema>

save file gdm.schemas
restart Ubuntu
it works for me

---

### Post by burgundy on 2009-11-02
This guy talks about this issue here:
[http://www.peppertop.com/blog/?p=671](http://www.peppertop.com/blog/?p=671)

He fixes it here:
[http://www.peppertop.com/blog/?p=690](http://www.peppertop.com/blog/?p=690)

I don't know if the above works, but these URLs solved my problem.

:)

---

### Post by phoenix49 on 2009-11-03
Thanks b12gold! That worked for me! :popcorn:

burgundy, thanks for more information ;)

---

### Post by b12gold on 2009-11-03
Glad that works for you, you're welcome again :)

---

### Post by jaimehum on 2009-12-22
Thanks it works great.

Regards,

---

### Post by k.sangeeth on 2011-06-28
> **b12gold said:**
> sudo gedit /etc/gdm/gdm.schemas

find:

<schema>
      <key>security/DisallowTCP</key>
      <signature>b</signature>
      <default>true</default>
</schema>

shift from true to false:

<schema>
      <key>security/DisallowTCP</key>
      <signature>b</signature>
      <default>false</default>
</schema>

save file gdm.schemas
restart Ubuntu
it works for me

cool .. it works :)

---

### Post by mpenda on 2011-10-17
Hello. I just upgraded from Natty to Oneiric and I can't get this to work. I had it working fine on Natty but now its broken again. Here's what I did:
1. Went and removed "-nolisten TCP" from /etc/X11/xinit/xserverrrc
2. Changed True to False for the DisallowTCP in /usr/share/gdm/gdm.schemas (/etc/gdm/gdm.schemas was already set to false)
3. Did xhost + on my Ubuntu desktop (tried just as myself and also with sudo)

Still getting the "Can't open display" message.....

What am I missing??
Thanks for the tips!

---

### Post by jllarden on 2011-10-20
I was asking myself the same question... The answer ist that on Ubuntu Oneiric Ocelot (11.10) the display manager has changed to LightDM, which doesn't apparently read neither/etc/X11/xinit/xserverrc nor /usr/share/gdm/gdm.schemas.

To enable TCP connections to the Xserver on Ubuntu Oneiric Ocelot (11.10):
1) Open /etc/lightdm/lightdm.conf with your favorite editor.

2) Add the following line to section [SeatDefaults]:
xserver-allow-tcp=true

[While you're at it you may want to add as well:
allow-guest=false
to prevent unrestricted guest access to your computer, see this for more information (in Spanish) [http://hmontoliu.blogspot.com/2011/10/deshabilitar-la-cuenta-de-invitado-en.html](http://hmontoliu.blogspot.com/2011/10/deshabilitar-la-cuenta-de-invitado-en.html).

Your /etc/lightdm/lightdm.conf should look similar to this:
[B][SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
xserver-allow-tcp=true
allow-guest=false[/B]

3) Reboot.

4) Enjoy.

---

### Post by cjpetrie on 2012-03-13
> **mpenda said:**
> Hello. I just upgraded from Natty to Oneiric and I can't get this to work. I had it working fine on Natty but now its broken again. Here's what I did:
1. Went and removed "-nolisten TCP" from /etc/X11/xinit/xserverrrc
2. Changed True to False for the DisallowTCP in /usr/share/gdm/gdm.schemas (/etc/gdm/gdm.schemas was already set to false)
3. Did xhost + on my Ubuntu desktop (tried just as myself and also with sudo)

Still getting the "Can't open display" message.....

What am I missing??
Thanks for the tips!

I'm running 10.10 and have the same problem.  I have also edited the gdm/custom.conf as suggested by a blog. No joy. Really frustrating that Ubuntu has made a basic linux networking function so difficult.

---

### Post by ubudog on 2012-03-13
Hi, it'd be best to start a new thread.

---

