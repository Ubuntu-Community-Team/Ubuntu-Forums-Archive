---
title: "I cannot boot into Ubuntu - Blank Screen + Cursor, 0 Second Load Default on GRUB"
date: 2009-08-14
forum: General Help
---

### Post by Godmanliving on 2009-08-14
Well I started following a guide to install another desktop environment (E17) but I got a phone call in the middle of the installation that was very important to me.  I was in Starbucks, my phone died, I got pretty frustrated and clicked the hibernate button and shut the lid of my laptop, and rushed out of Starbucks to go home and charge my phone.  SO, when I tried to turn on my laptop after that point, after grub tries to load my default choice (ubuntu 9.04) I end up with just a blank screen with a flashing cursor.  I had set my GRUB to load the default with a 0 second delay through startup manager (stupid, I know.  Very stupid) but I didn't think I would break my installation that easily.  SO, now I have no way to change modes in GRUB (that I know of) and no way to boot into anything (that I am aware of) to fix the problem.  I have been using Ubuntu for about 3 months now, which is the longest I have ever used it (I have tried every version sense 6.04)  and I would really like to stick with it now.  I don't have a live cd with me because I am away from home.  So my first question is, is there a way to fix this without a live CD?  And then my second question is, how would I fix this with a live CD if that is my only real option.  Thank you all in advance for your time.
-Jason

---

### Post by soapBAR2 on 2009-08-14
Boot into the liveCD, get into the terminal and run grub-install. Here's a tutorial for recovering grub (although it focuses on fixing for a windows install, it's the same process, but you stop before "Your Windows stanza should look something like this" line.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Godmanliving on 2009-08-14
Thank you for the quick response.  I'll give this a try as soon as I can get my hands on a LiveCD.

---

### Post by Godmanliving on 2009-09-02
> **soapBAR2 said:**
> Boot into the liveCD, get into the terminal and run grub-install. Here's a tutorial for recovering grub (although it focuses on fixing for a windows install, it's the same process, but you stop before "Your Windows stanza should look something like this" line.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Did not work.

---

### Post by Vaphell on 2009-09-02
you can try modifying grub file in liveCD mode to set timer to a non-zero value, that way you would be able to pick some other option

---

### Post by petrus4 on 2009-09-02
Use the LiveCD, and go into /boot/grub on the hard drive of your system.

Then edit the file menu.lst in that directory, and delete every instance of the words "quiet splash" that you can find.  This will stop Ubuntu from blocking out information about the boot process as it loads, so you can watch it and get an error message about what is going wrong.

Once you've done that, boot it up again, and let it run through to the point where it stops.  Then record the last text/message that comes up on the screen, and paste it here.

We will be able to help you more then, since we will be able to tell more about the nature of the problem.

---

