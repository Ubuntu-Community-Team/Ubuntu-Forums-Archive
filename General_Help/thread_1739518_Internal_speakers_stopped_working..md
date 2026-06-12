---
title: "Internal speakers stopped working."
date: 2011-04-26
forum: General Help
---

### Post by piratemari on 2011-04-26
So I've been running Ubuntu on my Dell Studio 1749 laptop since I got it, around 8 months ago. I recently upgraded to Maverick 10.10 64-bit, reformatting and partitioning my hard drive in the process (got rid of windows since I never use it) and it was working perfectly until last Wednesday (22.4.2011). On Wednesday I unplugged my usb headset while in a Skype call to switch to the internal speakers and my computer freaked out, black-screened, and froze. When I rebooted, the internal speakers had stopped working completely, even though the sound works perfectly on both sets of headphones I have.

I've tried most of the fixes that have been presented in other threads and none of them are working, including rebooting the laptop with the headset in. I've tried that with both of my usb headsets, even though I don’t like using the one that it froze on for the exact reason that any time I have audio playing with that headset and it gets unplugged, it black-screens and freezes my laptop. Actually audio doesn’t even have to be playing, sometimes unplugging it even with nothing playing still freezes my laptop. It does it once in a while with my other usb headset, as well, but not every time or anything close to that often.

One thread suggested that modifying /etc/modprobe.d/alsa-base.conf by appending the following line to the file would work:
```
options snd-hda-intel model=dell-m6
``` But that did nothing at all. Someone else said that they saved a copy of alsa-base.conf and replaced the whole thing with that line, so I did that, with no change. Then I purged alsamixer using ```
sudo apt-get purge alsa-base
``` and ```
sudo apt-get purge alsa-utils
``` Then I rebooted, and reinstalled them, which did not fix the issue. However, it did replace the  alsa-base.conf file that I modified which shows me that it actually did purge it. (I was an idiot the first time I tried to purge it and only purged and reinstalled alsa-utils..xD So the file did not get  replaced, which was when I realised my mistake) I have NOT modified the new file, although I did copy the contents to a text file in case I need to try that fix again.

I should also mention that the speakers **do** work when first booting up Ubuntu to the log-in screen, both with and without headphones

I ran the alsamixer diagnostic at the beginning of all this, here's the link: [http://www.alsa-project.org/db/?f=429351bec35a3fea587c5906aa12dd709385abb4](http://www.alsa-project.org/db/?f=429351bec35a3fea587c5906aa12dd709385abb4)

And then ran it again after purging and reinstalling alsamixer, here's the new link: [http://www.alsa-project.org/db/?f=f5e8e6b409da8c33368e34626fb89f208691d10b](http://www.alsa-project.org/db/?f=f5e8e6b409da8c33368e34626fb89f208691d10b)

Maybe that'll give someone a better view of what is going on?

I have tried messing with the settings, disabling the headset, setting the input and output manually to internal speakers while the headset is still plugged in, making sure with GNOME alsa-mixer that the speakers are not muted, rebooting with the headsets in and then unplugging them, basically everything I have seen suggested in other threads that had the same issue.

Any help would be greatly appreciated. I really do not want to have to re-install Ubuntu, because of how I have my hard drive partitioned. I'm not at all sure that I wouldn't somehow mess something up and lose all of my files.

If you need any more information please let me know what and I'll try to get it for you.

---

### Post by piratemari on 2011-04-28
Bumping this since it's been several days and still no response...

---

