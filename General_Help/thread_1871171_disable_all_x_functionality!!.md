---
title: "disable all x functionality?!?!"
date: 2011-10-28
forum: General Help
---

### Post by withoutfences on 2011-10-28
Hi Everyone;

Fresh installation of 11.10 Desktop.  I was too impatient to wait for the server ISO to download so I just rolled out what I had.

what I would like to do is disable the login gui and x all together..don't need em. I've tried 

sudo update-rc.d x11-common remove as well as varients with gdm, xdm and kdm, which is what I found from searching out information.

It would appear that perhaps the sequence or the location/control of x has changed.

What I would like to have is jsut a basic terminal machine similar to what you get from Server.

Would it just be easier to remove the x packages and call it a day or is there a better way?

Thanks for all your help in advance.\

Cheers,
Gary

---

### Post by gsmanners on 2011-10-28
The DM in standard 11.10 is lightdm. That's the one you want to remove (if any).

---

### Post by withoutfences on 2011-10-28
yeah tried no soap...unity rules all.

After spending too much time on this, i'm going to just install server.

I would however welcome suggestions for disabling all x functionality on desktop in case someone else is looking for a solution

cheers,
Gary

---

### Post by haqking on 2011-10-28
[s]```
gksudo gedit /etc/default/grub
```

change

GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221;

to

GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash text&#8221;


```
sudo update-grub
```

on some systems.

In 11.10 im pretty sure that

"command mode" put into your /boot/grub/grub.cfg would work but i cant be bothered to boot my 11.10 VM up to test this, but it used to make it boot straight into command mode instead of loading GUI.[/s]

However i cant see why anyone running a desktop edition would want to remove GUI or boot only to a console, if you need console you can just ctrl + alt + f1

If you dont want GUI then dont run a desktop edition IMO

edit: just did a quick test of that in 11.10 and doesnt work, but i havent got the energy right now to figure out a different method, i may post back

---

### Post by gsmanners on 2011-10-28
Yeah, if you want a DIY version of Ubuntu, you really should start here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by oldos2er on 2011-10-28
Try [http://ubuntuforums.org/showpost.php?p=10798400&postcount=4](http://ubuntuforums.org/showpost.php?p=10798400&postcount=4)

It's for 11.04 but should work on 11.10 too.

---

### Post by withoutfences on 2011-10-28
The reason, was pretty simple, I had a desktop ISO handy, and installed it, not really recalling that there was no option for selecting install options.
 
The reason I wanted x gone was strictly from a resource pool option.
 
and to be honest the statement of why would you do that to desktop, the nature of the operating system dictates that we be able to manipulate it to whatever end we want, as long as we abide by whatever GPL/etc binding it.
 
Anywho, I've got another box running desktop and I'm going to see what I can do to get it boot without and x functionality and will post the results.
 
thanks for all of the help, and now on to a content filtering system for the home,(13 year old boys need filtering :( )

---

