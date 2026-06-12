---
title: "No GUI?"
date: 2012-02-23
forum: General Help
---

### Post by Kissell on 2012-02-23
I don't know how this happened...  but when i reboot I don't get a GUI...  

Running Ubuntu 11.10 64-bit.

I can hit CTRL-ALT-F1 to get a login screen, then I can do > sudo -s and then I can do > startx

That gets me a GUI, although all my shortcuts are gone off the launcher because it is root's GUI.

When I try to run "startx" as my regular user I get an error.
```
Fatal server error:
Cannot move old log file "/var/log/Xorg.0.log" to "/var/log/Xorg.0.log.old"

Please consult the The X.Org foundation support
          at http://wiki.xorg
 for help.

 ddxSigGiveUp: Closing log
xinit: giving up
xinit: unable to connect to X server: Connection refused
xinit: server error

```

> 
cd $HOME
ls -lais|grep X

```

8389223  4 -rw-------   1 myuser myuser     111 2012-02-23 15:20 .Xauthority

```

---

### Post by sunfromhere on 2012-02-23
Did you update your graphic card drivers before that?
Did you do anything related to graphics?

---

### Post by Kissell on 2012-02-23
No, I don't think so...

I recently re-formatted this computer to do full-system encryption with the root partition and swap partition encrypted, instead of just the home and data partitions...  so its pretty much a fresh install.  

It's been online and XBMC has been identifying my multimedia files and retrieving data on them...  can't remember now why I rebooted...  maybe the system hung and I had to power it off improperly... 

But I can't think of any reason this would have happened...  Re-installing would be very time consuming, because my internet connection is very slow and there are lots of updates and programs to download...  I was hoping someone could help me fix this so I wouldn't have to reformat.

---

### Post by sunfromhere on 2012-02-23
What graphics card do you have? Do you have proprietary or free drivers?

I'm asking because of this error: (I got it only when I had drivers/graphics issues)


Fatal server error: Cannot move old log file "/var/log/Xorg.0.log" to "/var/log/Xorg.0.log.old"

It helped to purge Xorg & stuff, to reinstall drivers, but it would be more helpful if you could write more details (software&hardware).

---

### Post by Kissell on 2012-02-23
It's an ATI Radeon card...  4550 HD i think...

I didn't install any drivers...  I just used the defaults.

When the system popped up a message about using restricted drivers I did try to install them, but it said it failed...  but I think I've rebooted successfully since then...  maybe not... 

I do have the ATI catalyst driver ".run" file that I downloaded a few weeks ago for this system, but never installed it...  the reason I've never installed it is it always told me it conflicted with the default drivers already installed and I should uninstall them first, but I didn't know how to do that, so I never did it.

So I just did it now...  using the --force parameter... to override those messages about the previous driver being installed...  

now I get the same errors as before, plus a new one:
```

xauth: error in locking authority file /home/myuser/.Xauthority

```
So I changed the owner and group on that file to myuser.  
but everytime I run "startx" I get that additional error now.

I don't know much about X.  Maybe there is a way I can just reset this to the defaults?

---

### Post by Kissell on 2012-02-23
I tried purging xorg using these commands, but it made no difference.
```
sudo apt-get purge xorg
sudo apt-get install xorg
```

---

### Post by Kissell on 2012-02-23
Ran these commands I found in another post.

```

  sudo /usr/share/ati/fglrx-uninstall.sh  # (if it exists)
  sudo apt-get remove --purge fglrx*
  sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon 
  sudo apt-get install xserver-xorg-video-ati
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg
```

but didn't work...  the reconfigure just says no such file or directory...  obviously those were not commands for ubuntu 11.10.

---

### Post by Kissell on 2012-02-23
oh wait...  dpkg-reconfigure was giving errors because my working directory no longer existed after the purge...

now I run "startx" and no longer get any errors...  but just get a blank screen...  no mouse, no background...  and I'm completely hosed...  CTRL-ALT-F# doesn't work, or at least it doesn't display anything...

appears to actually have killed more than the display...  I can't ssh into the computer, or ping it...

---

### Post by sunfromhere on 2012-02-23
> **Kissell said:**
> It's an ATI Radeon card...  4550 HD i think...

I didn't install any drivers...  I just used the defaults.


ATI. This sounds like an integrated graphics? If it's an hp laptop, sorry man, but you're gonna **** blood.

As much as you hate, if in fact hp with chip, I would recommend a clean install. You can back-up entire /home folder. 

Anyways, try to purge everything you can connected to the fglrx and xorg and anything related to graphics from the command line, and then reinstall xorg and free drivers.*

Also, can you boot normally from a Ubuntu Live CD?

EDIT: do not, at any instance, try to enable ATI proprietary! Leave that for once the computer is running stable.

---

### Post by sunfromhere on 2012-02-23
> **Kissell said:**
> oh wait...  dpkg-reconfigure was giving errors because my working directory no longer existed after the purge...

now I run "startx" and no longer get any errors...  but just get a blank screen...  no mouse, no background...  and I'm completely hosed...  CTRL-ALT-F# doesn't work, or at least it doesn't display anything...

appears to actually have killed more than the display...  I can't ssh into the computer, or ping it...

Do you have your internet connection at this point? Is the command line working properly? Manually find and remove anything related to ATI/AMD/Xorg. 

On Arch and Debian I did this, also removed all mesa/vesa/etc and reinstalled those.

---

### Post by Kissell on 2012-02-23
After reboot it doesn't go to the GUI...  but I can switch to a login with CTRL-ALT-F1 and now I can start X as my normal user.

so that's a huge victory.

but how can I make it start the GUI by default after reboot?

---

### Post by sunfromhere on 2012-02-23
Add it to daemons? :confused:

---

### Post by Kissell on 2012-02-23
weird problems...  like the unity plugin wasn't checked in compiz, and even though I checked it, any settings changes to it aren't happening...  so I can't make that launcher bar not auto-hide which is a horrible default setting in Ubuntu.

anyway, did this
```

cd /etc/init.d
ln /usr/bin/startx startx
update-rc.d startx defaults

```

but it didn't work... after I reboot I still have to login to the terminal and run startx manually.

---

