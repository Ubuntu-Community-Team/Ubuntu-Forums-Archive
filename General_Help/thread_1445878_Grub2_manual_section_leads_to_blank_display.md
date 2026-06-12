---
title: "Grub2 manual section leads to blank display"
date: 2010-04-03
forum: General Help
---

### Post by imbjr on 2010-04-03
Today, just hurry the boot process up a few seconds, I manually selected the kernel to boot to. Everything went well and got to the point where I heard the bootup sound and then the screen went blank and my monitor on-switch went orange - indicating nothing to display.

If I pressed the delete key I could hear the sound made when there's nothing more to delete. I switched to one of the virtual terminals and the monitor switch went green but no display.

I rebooted and let the bootup process as normal and everything was OK. I repeated the initial bootup process, with the manual selection, and it went blank again. The odd thing is, I'm sure I've recently done this before and all was fine.

Anyone else experience this?

---

### Post by imbjr on 2010-04-03
Well, recovery mode for the latest kernel works.

And manually selecting the previous kernel works.

Let's try the newest again ...

---

### Post by imbjr on 2010-04-03
I tried manually scrolling down the menu entries and then back up the latest. That works.

I tried repeating the initial effect and instead of a blank screen there was a delay whilst the screen displayed "Auto Adjusting etc" and then back to normal.

Hopefully this is nothing serious. Just struck me as odd.

---

### Post by warfacegod on 2010-04-03
This might be useful:

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+basics]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+basics")

---

### Post by oldfred on 2010-04-03
Was this in Karmic?

I had a similar issue with my inital beta install of Lucid. It turned the monitor total off and I could not get anything to work. I have it in a separate partition and separate MBR so I went in & blacklisted nouveau added nomodeset and was only able to use recovery. I updated and manually installed the nvidia drivers and everything has worked since.

---

### Post by imbjr on 2010-04-04
> **oldfred said:**
> Was this in Karmic?

I had a similar issue with my inital beta install of Lucid. It turned the monitor total off and I could not get anything to work. I have it in a separate partition and separate MBR so I went in & blacklisted nouveau added nomodeset and was only able to use recovery. I updated and manually installed the nvidia drivers and everything has worked since.

Yes, this was Karmic.

I looked at warfacegod's link and didn't see any issue that resembled mine. So far, I think the effect is relatively minor, since it's not quite repeatable. Note also I have an old ATI card that now is driven by the open-source driver.

---

### Post by warfacegod on 2010-04-04
If the issue gets worse, you might try reinstalling GRUB. The link I posted has a section on that.

---

