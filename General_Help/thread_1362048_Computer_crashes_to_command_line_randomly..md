---
title: "Computer crashes to command line randomly."
date: 2009-12-22
forum: General Help
---

### Post by susanw on 2009-12-22
My computer keeps randomly crashing. I think it does it most when playing videos in web browsers (google chrome and firefox equally). I've  been on Karmic on this machine since before it was released with no problems at all up to now.

When it crashes a black screen comes up, tells me a random time when I last logged in to the machine which can be a few days before or a few hours never correct or relevant (unless there's something I'm missing). It then either asks for my login or just just gives me a prompt like I would see in the terminal. When I type 'login' on the command line it says, in true ubuntu style: 'can't possibly login without root' or something like that, then it logins anyway.

After this it returns to my normal login screen (complete with the misplayed opening tune I've not yet managed to fix) and I login as normal, all my programs have crashed but it works fine again for a while.

I wondered if it was lack of memnory so repartitioned, checked there was lots of space on that partition and doubled the swap size, plus turned swapon - haven't figured how that turns itself on and off randomly but it seems to. None of this made a difference.

I'm not sure what information about the system I'm running would be useful to put in here:
I'm on Release 9.10 with kernel 2.6.31-16-generic with an Intel(R) Pentium(R)M processor triple booting between windows, 9.10 and 9.04 I could go back to 9.04 but I prefer 9.10.


Thank you for reading, any ideas gratefully received.

Susan

---

### Post by dcstar on 2009-12-22
> **susanw said:**
> M
.........
I wondered if it was lack of memnory so repartitioned, checked there was lots of space on that partition and doubled the swap size, plus turned swapon - haven't figured how that turns itself on and off randomly but it seems to.


Changing the Swap partition changes the UUID, so you have to manually edit files to reflect this change. Do a search for detailed instructions.

---

### Post by 3rdalbum on 2009-12-22
Video playback puts a lot of load onto graphics card drivers; that would be the first thing I'd check. Update them if you can.

---

### Post by susanw on 2009-12-28
Thank you for the replies. I've learnt about SWAP partitions, UUIDs and now have a large SWAP which the PC recognises and appears to use,

So Cheers to David.

Problem still occurs but learning took place so that's good.

As for graphics card drivers I've come a bit unstuck. Having googled and searched the Ubuntu forums I'm still none the wiser.

Issues are:

1) How do I find what graphics card I have?
-> found it: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

2) How I find which graphics card driver I'm currently using?
3) Which one(s) would be better?
4) Whether graphics card /driver(s) are actually the issue or whether I should look for other solutions of why my PC randomly hangs?

All help gratefully received.
Thank you,

Susan

---

### Post by Portmanteaufu on 2009-12-28
Apologies if you've already tried this or something similar. Perhaps the easiest thing to do would be to allow Ubuntu to search for applicable proprietary drivers on your behalf. (Obviously this is no good if you're philosophically opposed to closed-source software.) If you're unfamiliar with the difference between the proprietary drivers and the defaults, just say the word and I'll explain.

[This article]("http://www.ghacks.net/2009/04/15/using-proprietary-drivers-in-ubuntu/") shows you how to do it -- it's a pretty automated process. Just some simple menus.

---

### Post by susanw on 2009-12-28
Nice idea Portmanteaufu and I've been looking at this a little. I used it on a previous incarnation of Ubuntu to find wireless drivers. 

Unfortunately 'Hardware Drivers' is empty so I cannot click through nice little menus and looking at the help section has not helped either. Any ideas how to populate the drivers menus with appropriate drivers would be very handy to see if others work better?

Cheers,

Susan

---

### Post by Portmanteaufu on 2009-12-28
Hrm, that's unfortunate. Perhaps have a look [at this thread]("http://ubuntuforums.org/showthread.php?t=207794") now that you know what graphics driver you need?

---

### Post by susanw on 2009-12-28
Portmanteaufu said
Perhaps have a look at this thread now that you know what graphics driver you need?

Should I know which driver I am supposed to use now?
Perhaps you are saying that since I have now discovered I have a Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) card I need a specific driver?

If it is a specific one and if this thread :  [http://ubuntuforums.org/showthread.php?t=207794](http://ubuntuforums.org/showthread.php?t=207794)
is talking about the correct one (xserver-xorg-driver-i810/i915) then trying to install it is proving tricky:

I cannot find my xorg.conf file!?
sudo gedit /etc/X11/xorg.conf gives an empty file, changing directory to /etc/X11 lists other files but not this one. Could it be somewhere else? Could I have deleted it? Would I have caused other random badness in my PC if I have? All ideas welcome.

Thank you,

Susan

---

### Post by susanw on 2009-12-28
I just found out Karmic does not have an xorg.conf file. Phew, I thought I'd lost it some how! Perhaps there is thus a better way to install proprietary drivers than forcibly make it do it through an xorg.conf file when it would be the only thing in the file?

Any ideas on how to:
- install new drivers
- make 'hardware drivers' recognise drivers so that one can choose one
- tell the PC to choose one graphics driver over other ones???

Thank you

Susan

---

### Post by susanw on 2009-12-28
These events when the computer just hangs really are getting quite annoying. Perhaps it is the graphics card driver or perhaps something else entirely. It appears many people have had bad encounters with Intel chips on Karmic yet it is very hard to find a workaround. Any advice on fighting my way through the deluge of bug reports and threads on similar yet seemingly unique issues would be much appreciated. 

Outstanding issues:
Is it silly to create an xorg.conf file to just prioritise use of a particular driver - surely there is a better way than this?
Is there a good way of finding what driver one needs for a particular graphics card?
How do you login from a screen showing only commandline - is there a phrase which means restart?

Thank you for the people who have put in their ideas, many different avenues have been tried because of these.

Susan

---

### Post by susanw on 2009-12-30
Bump. 
Still got issues here and searching forums and google extensively, reading countless bug reports and tutorials has not helped yet. Any ideas very welcome,

thank you

susan

---

### Post by susanw on 2009-12-30
Hello,

Just found out that the screen I keep getting to is tty1. Why I should get there I'm not sure still though. The message I get when logging in from there is about a render error which looks similiar to one in launchpad bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404064](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/404064) 
but it comes up and goes too quickly to see properly and occurs after a while instead of on start and shutdown.

---

