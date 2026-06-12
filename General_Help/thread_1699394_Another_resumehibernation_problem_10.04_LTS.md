---
title: "Another resume/hibernation problem 10.04 LTS"
date: 2011-03-03
forum: General Help
---

### Post by zSeries on 2011-03-03
I have been using 10.04 LTS for about 6 months. I have it installed on a laptop and 3 desktops all completely different hardware.

All machines are more of less running exactly the same installed applications and update levels, currently 2.6.32-29. All machines have a swap disk at least twice the size of RAM.

Hibernate and suspend works on all but one desktop. It is an ASUS A7V8X with Nvidia MX400 graphics card and Dell 1907FP monitor, I am using the recommended NVIDIA accelerated graphics driver(V96). Originally the problem was that the machine would not complete hibernation or suspend. In both cases the PSU remained on (it has a loud fan). Last night after literally months of browsing the web and newsgroups for clues I made some progress. I went into System>Appearance Visual Effect tab and clicked the Extras tab, then set it back to none. Now the machine seems to hibernate and suspend OK, the PSU goes OFF.

During the hibernation I get a black screen followed by a purple screen with the top of "U" and "t" in "Ubuntu" and half the Ubuntu icon. The power goes off.

Now the problem is the resume. On a normal start up you would see
1 BIOS screens
2 Grub2
3 Blinking cursor
4 Ubuntu logo
5 Logon panel

But when I resume this problem machine I get

1 BIOS screen
2 Grub2
3 Blinking cursor
3 Purple screen with top of "U" and "t" abnd half the Ubuntu icon. (the same screen I see shutting down)

At this point the machine appears dead and the only thing I can do is hit the power button. It does not respond to any key presses or mouse. All my other machines present the prompt for the user password here.

However underneath it is alive and well. I have NX Server installed on it and I can logon to the machine remotely with any of my other computers and have a full X session and it works fine. So my only problem appears to be getting the logon screen up again.

Something I noticed that seems odd when in this strange state. I have a terminal open that is constantly pinging the machine. I get about 10 pings of 0.2ms then one at 3000ms one at 2000ms then one at 1000ms, then the cycle repeats like clockwork.

Finally, if I disable the NVIDIA graphics driver it goes back to hanging on hibernation and I have to reactivate it to enable the "extras".

Can anyone point me at what the problem might be or where to look for diagnostics.

Thank you,
Tony.

---

### Post by zSeries on 2011-03-09
Bump.
Does anyone have any suggestions here?
Thanks,
Tony.

---

