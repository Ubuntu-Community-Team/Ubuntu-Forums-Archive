---
title: "Kubuntu won't start!"
date: 2009-09-30
forum: General Help
---

### Post by amschmid on 2009-09-30
I can't get Kubuntu to boot.

Last night I left it running with Amarok playing.  This morning I am confused to see Amarok closed.  When I try to open it a gain, I get an error message. I think it said that a location was read only.  

I then try to start firefox (shiretoko) and get a message saying that firefox 3.5 is already running and must me closed, sounding like something I used to hear in windows.  That same message also suggests rebooting, so I do.

It runs some sort of system check well before getting to the GUI (looks like full screen terminal) and then asks me to press ctrl-D to restart, so I do.  It says exit and restarts.  That only gets as far as a flashing small horizontal line (dash or underscore) in the top left corner.  After a few minutes I turned the computer off and restarted again with the same result.  

I'm running Kubuntu 9.04 64 bit on a dell inspiron 1501 laptop, dual booting with vista (which it what I'm using right now)

---

### Post by ianmillington on 2009-09-30
So all you get is a black screen? Did you update anything last night? Try this:

Boot up and at the grub menu select the rescue mode for the lowest-numbered kernel on your system. If you don't see a menu (you might just see a countdown) hit esc immediately after the BIOS post and you will see the various options. You should soon be presented with a list of options. The 2 key ones are fix packages (in case an update has gone pear-shaped)and fix X (in case Xorg has fallen over). After running those options try the normal boot option. 

Any joy?

---

### Post by Giblet5 on 2009-09-30
Do you have room mates? A cat?

They have some explaining to do, I think.

If not, then Amarok may have made your system overheat and become unstable. Most systems have barely adequate cooling systems and can't actually handle a continuous load for extended periods.

If you get no Grub menu/prompt, you might need to boot from a Live install CD and do some detective work.

Here's [how to get grub working]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") again.

---

