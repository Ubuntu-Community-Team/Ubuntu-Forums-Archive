---
title: "Maybe trashed"
date: 2012-06-05
forum: General Help
---

### Post by s9032g@comcast.net on 2012-06-05
I just caused myself problems by deleting some Gnome files I thought were not needed. Now, when I start up I get a message "Your screen. graphics card, and input device settings could not be detected correctly. You will need to configure these yourself."
When I click on "ok" I am given some options none of which work.
The thing progresses to starting and stopping anch(h)cron. Then to checking battery state. Then it just stops.
If I ask it to "start in low graphics mode one time" it says, "standby one minute while display restarts" but nothing ever happens.
I have always been willing to take chances with Ubuntu but this time I got burned.
Running 12.04, plugged in, wired.
Help?

---

### Post by snowpine on 2012-06-05
I recommend you boot to recovery mode and then:

```
sudo apt-get install ubuntu-desktop
```

This will reinstall all of the default Ubuntu software and hopefully fix your system.

In the future do not delete files outside your /home :)

---

### Post by s9032g@comcast.net on 2012-06-05
Thanks.

I would like to do this but I see no "recovery mode". I can get to the boot menu which lists these options:

hard drive
cd/dvd/cd-rw
removable devices
network boot
diagnostics

I tried hard drive, network boot, and diagnostics. All of them ended up nowhere. Maybe I have to create a 12.04 DVD and boot from that???? I would rather do it a simpler way???

---

### Post by snowpine on 2012-06-05
What happens when you choose "hard drive"?

[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by s9032g@comcast.net on 2012-06-05
When I choose "hard drive" it goes through the same things described in my original query. It always boots from "hard drive" unless I give it an alternative source.

---

### Post by snowpine on 2012-06-05
Do you have a GRUB menu from which you can select Recovery Mode as detailed in the link I posted above?

---

### Post by s9032g@comcast.net on 2012-06-05
Yes.

One has to be really quick. Once I got through hitting esc. I ran the repair selection than went on to boot and the same thing happened as in my original note.

What about this?
NOTE: Users of Ubuntu Karmic (9.10) and higher will need to press and hold the left Shift key instead of Escape in step 4, and may not see the "Grub loading, please wait..." message in step 3. 

Didn't work for me.

I am trying to hit esc fast again w/o success

---

### Post by s9032g@comcast.net on 2012-06-05
ok.

I was fast enough to get to the "right screen" again. 
So far the I have run:
dpkg repair
grub update boot loader

It didn't help.

The other choices are:
resume
clear
fail safe x
fsck check files
network enable networking
root go to root shell prompt
sustem summary

What to do????????????????

---

### Post by s9032g@comcast.net on 2012-06-05
All is now ok. I am doing this on my Ubuntu laptop

Using a quick esc I once again got to the Grub menu. This time I tried "root  drop to root shell prompt". That got me to something like terminal. Then I used the command suggested in your first response i.e. sudo apt-get install ubuntu-desktop. That ran all sorts of corrections.

I was then able to login. Things did not look the same as my original setup until I shut down and restarted a few times, the all was back to my "normal".

I ran the Ubuntu Tweak Janitor to clean up and all is 100%.

THANKS A BUNCH!!!!!!!!!!

---

### Post by snowpine on 2012-06-05
I would choose "go to root shell prompt" and enter:

```
apt-get install ubuntu-desktop
```

You will need a wired connection to the interweb.

(edit: cross-posted; glad you got it fixed! :))

---

