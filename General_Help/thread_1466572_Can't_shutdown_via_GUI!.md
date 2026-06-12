---
title: "Can't shutdown via GUI!"
date: 2010-04-30
forum: General Help
---

### Post by Mike_IronFist on 2010-04-30
Hey, this is a weird problem that happened to me after installing 10.04. When I click the menu in GNOME to select "Shut Down", I click it, it brings up the dialog asking if I want to shut down the computer, and I click "Shut Down", but then NOTHING happens! I can only shutdown if I open the terminal and use the "halt" command with root privaleges. Can anyone help me?

---

### Post by ajgreeny on 2010-04-30
I had the same problem with my test of Lucid a few times, when it was an updated version from the beta2 daily release of April 2nd.  It was not happening in the normal situation, however, and only happened a couple or so times, then righted itself.  I never did sort out why it occurred; whether it followed some activity of mine, eg using update manager, but seems to have gone away for the moment, though I don't use Lucid a lot yet; still on karmic.

---

### Post by to0w1r3d on 2010-04-30
Same here...could not shutdown or reboot...the toobars disappear but sit looking at the desktop...

Something with Grub?

---

### Post by vettie on 2010-04-30
Had the same issue

I did a manual shut down. Power all the way off.

IF you are running a dual boot, boot into OTHER OS. Then go thru normal shut down.

Give it a min or 2 and reboot to Lucid and whatever the issue is goes away, it worked for me and I have not had an issue with it since.

luck

---

### Post by sveterv on 2010-04-30
And another same story, I had this problem after upgrading from 9.10 to 10.04 Release Candidate (a week ago), it was like that for a two or three days after RC was released, then it stopped acting this way and now everything is working fine. 

Guys have you downloaded official and final ISOs of Ubuntu (not Release Candidate)? Some mirrors may still have old files. If there is "-rc-" in the ISO file name than it is RC not final. If it is, and you have installed system and don't want to wait for new ISO to download, simply update system and problem should disappear, you will get to the final version of Ubuntu also only by installing all the updates without need for downloading final ISO.

---

### Post by ottosykora on 2010-04-30
same story here, fresh install of 10.04, it just wont shut down , reminds me of lang years ago, w98se...

---

### Post by jave on 2010-04-30
I have the same problem with a fresh install of 10.04 64-bit.  It did shutdown for me via GUI at first, then  I logged out for testing, logged back in, and tried to shutdown/restart but couldn't.  Only way to shutdown was through "sudo shutdown -h now".

Maybe it's a secret plot by the Ubuntu gods to keep us all using Ubuntu and to never go back to the dark side.... :lolflag:

---

### Post by Mike_IronFist on 2010-04-30
I guarantee you it is -not- GRUB, because GRUB is out of the picture once Ubuntu is booted, that much I know.

> **jave said:**
> I have the same problem with a fresh install of 10.04 64-bit.  It did shutdown for me via GUI at first, then  I logged out for testing, logged back in, and tried to shutdown/restart but couldn't.  Only way to shutdown was through "sudo shutdown -h now".

Maybe it's a secret plot by the Ubuntu gods to keep us all using Ubuntu and to never go back to the dark side.... :lolflag:


This matches my problem almost exactly.

---

### Post by garvinrick4 on 2010-04-30
ALT/F2  type in gconf-editor and click run.

Click APPS go to indicator-session

uncheck restart menu item

uncheck shutdown menu item

Should go directly to restart and or shutdown when asked with no time element.

---

### Post by Kylerobhew1 on 2010-04-30
I am having the almost same problem. When I try to shut-down or restart everything closes then the screen goes blank and the system stalls. I think this also may have something to do with why my splash-screen is in 256 color and why my games wont run in full-screen without crashing the system.

If you having any problems shutting down, for the time being, you might want to use this workaround. Press these keys in this order one by one while holding ctrl+alt+print screen: R, S, E, I, U, B. An easy way to remember this is; Raising Skinny Elephants Is Utterly Boring.

This wont work if you have already selected either shut-down or restart in the drop down menu. It should be preformed while gnome or your current desktop manager is running. This will provide you with a gentler way to shut down your system without having to hold down the power button. this can also be used when apps are misbehaving and your cant get into a terminal or back to your desktop.

---

### Post by Mike_IronFist on 2010-05-01
> **Kylerobhew1 said:**
> I am having the almost same problem. When I try to shut-down or restart everything closes then the screen goes blank and the system stalls. I think this also may have something to do with why my splash-screen is in 256 color and why my games wont run in full-screen without crashing the system.

If you having any problems shutting down, for the time being, you might want to use this workaround. Press these keys in this order one by one while holding ctrl+alt+print screen: R, S, E, I, U, B. An easy way to remember this is; Raising Skinny Elephants Is Utterly Boring.

This wont work if you have already selected either shut-down or restart in the drop down menu. It should be preformed while gnome or your current desktop manager is running. This will provide you with a gentler way to shut down your system without having to hold down the power button. this can also be used when apps are misbehaving and your cant get into a terminal or back to your desktop.

No that's not even close to my problem. My system stays totally normal and responsive in performance after I try and shut down. It just acts like I never clicked "shut down" after I confirm the shutdown from the dialog box.

---

### Post by Mike_IronFist on 2010-05-01
> **garvinrick4 said:**
> ALT/F2  type in gconf-editor and click run.

Click APPS go to indicator-session

uncheck restart menu item

uncheck shutdown menu item

Should go directly to restart and or shutdown when asked with no time element.

They're all already unchecked.

---

### Post by mbuller10 on 2010-05-02
I'm have the same problem, as if I never pushed shutdown...please help

---

### Post by dino99 on 2010-05-02
some users successed by adding acpi=force to /etc/default/grub

change: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"

work for some only sadly, some need to remove "splash" on that line.

---

### Post by perlhead on 2010-05-16
> **Mike_IronFist said:**
> No that's not even close to my problem. My system stays totally normal and responsive in performance after I try and shut down. It just acts like I never clicked "shut down" after I confirm the shutdown from the dialog box.

I, on the other hand, am having exactly the same problem you have: the system will shutdown normally if I do a "sudo halt", reboot with no problem if I do "sudo reboot", both of which completely rule out any GRUB-related issues. I cannot even log out of the session: the system asks whether I really want to log out, but after my confirmation everything stays exactly the same.

Are you running OpenOffice.org's systray accelerator? I have found that disabling the systray accelerator will restore logout/shutdown/restart functionality. Maybe Gnome doesn't know how to kill it?

In any case, this is a serious usability bug: if the system can't log out for some reason, it should give the user some feedback on what keeps it from following orders.

---

### Post by antony_css on 2010-05-20
I get this problem too and I discovered that it is due to the openoffice systray:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/562027]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/562027")

---

