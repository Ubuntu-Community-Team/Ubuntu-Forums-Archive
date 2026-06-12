---
title: "VMware 6.5 installing devices hangs...Forget about it!!"
date: 2009-07-22
forum: General Help
---

### Post by babygenius55 on 2009-07-22
Well, to start let's have it known that I was actually able to complete an install of WinXP SP3 Today finally!! It didn't even take that long (to be explained).

     I know I wasn't the only one out there that was having this problem with the install hanging at the end of the 'installing devices' section. I found quite a few posts around the net that tried to deal with the problem. One was actually correct, only not very clear to us Noob's...or maybe it was just me. [URL="http://jbopensrc.wordpress.com/2008/07/01/quickfix-vmware-server-winxp-pro-guest-install-hangs-at-installing-devices/"]ClickHere
[/URL]
     To begin,in the middle evidently; I have a laptop I'm experimenting with the specs are thus:
     Acer aspire 5610 - basically out of the box
          If you wanna know more google it.

     After about 2 hours just getting the thing installed...I'm very new but learning fast, I came across some problem with the XP install. First, it needed an inordinate amount of user input. I was always having to touch something on the laptop to keep the install rolling. Sloooow, oh so slow.  After 3 different attack methods I had had enough. did some more searching, and found a download for a scsi driver in a '.flp' format.  It was a godsend or so i thought.
     That's when I discovered that it's sort of hard to find almost anything useful if you're new to linux. I couldn't find anything to mount the image! I had read that there were short commands you could use in the terminal, but there were no supporting hints. What good is that?
     Long story short, I felt like a total @$$ when i realized that I could use the virtual machine i created to mount the image.  I felt like an even larger @$$ when I realized that using the default settings in VMware was retarded. I think they have it set up for huge conglomerates or something.
     For me personally, I'm sure the install using a scsi virtual disk would have finished eventually, it got past the 'installing devices' after about 90 minutes. Yes, I said 90 minutes. Plus I had to stay at the laptop just doing stuff so that the install would continue!  After about 4 hours of waiting on the install, I said, "I'm doing the IDE virtual disk install tomorrow".  You know what?  It worked! Fast as all get out (still needed user input to keep it moving, but FAR fewer instances)
     After about 18 minutes It was installed.  I felt beautiful. I'm soo smart

:confused:

   NOT (Imagine Borat).

     While I'm sure I'm forgetting a few things here I'm gonna stop and try installing WinXP SP3 With drivers...don't ask if you don't know.  Let's see how long that takes.

    To recap;Don't use the default settings if you find you are having problems. The only real change I made was not using a SCSI virtual disk. Why That caused such a problem...?



---------------- Now playing: [Death Cab For Cutie - Company Calls]("http://www.foxytunes.com/artist/death+cab+for+cutie/track/company+calls") via [FoxyTunes]("http://www.foxytunes.com/signatunes/")


Trial 2:

     Either my laptop got better magically, or the super inoculation is to watch Bleach while doing the install!  Maybe watching video, etc. is the input my laptop needed. Got WinXP SP3 'with drivers' to install with almost no extra input. Still using IDE Virtual drive.  It took just over one episode of Bleach. Yes.

---

### Post by Cheesemill on 2009-07-22
You could try VMware Server instead, I've never had any problems installing XP as a guest.

---

### Post by babygenius55 on 2009-07-23
> **Cheesemill said:**
> You could try VMware Server instead, I've never had any problems installing XP as a guest.

I'll probably look into it one of these days, but I stand by "If it ain't broke, don't fix it".

Thanks for the input though.

---

### Post by babygenius55 on 2009-08-01
Adding that most things are still working fine, just trying to get the most for my money. I have 64-bit VMware running on my Desktop just dandy for the most part...stupid live drive.

---

### Post by darkhammer8108 on 2009-08-01
iv been running 6.5 workstation fine for months now with just the default installation (aside from the line that changes the keymap so that ubuntu's default keymap doesnt hate vmware).

---

### Post by babygenius55 on 2009-09-12
i marked this as solved because it really seems like an irrelevant issue since I used a workaround that I like.

---

