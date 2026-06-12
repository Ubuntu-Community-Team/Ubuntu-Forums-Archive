---
title: "Cannot move windows, scroll down or move to another workspace with mouse"
date: 2010-10-09
forum: General Help
---

### Post by F1R3H4CK3R on 2010-10-09
I just upgraded my Ubuntu Lucid to Maverick RC and I found some bugs, I've been searching for 14 hours for this error and only found solutions for hardy, karmic, lucid and feisty, so I wanted to know if there's any solution, I tried a lot of things in the CCSM and nothing.
Here are the problems:
- Cannot move windows with mouse
- Cannot move windows to another workspace in expo
- Cannot scroll up/down with the bar, only the button
- Cannot open stacks in AWN
- Non existent plugin crashes in AWN
- When computer boots up it takes 2x the waiting time in comparison to lucid

I was anxious because 10.10 RC was released and it's actually having the worst errors I've ever experimented using Ubuntu since 8.10, And upgrading I never had to get help, In addition this never happened to me

What I did to try to solve this (And I failed):
- Disable all CCSM options a then enable
- Disbled auto sorting, enabled move
- Reinstalled Compiz

I thought it was a CCSM problem and I just discovered all that stuff I spent doing 14 hours was for nothing, so I came here to get help and I hope that someone answers me.

Thanks!

---

### Post by sendblink23 on 2010-10-09
> **F1R3H4CK3R said:**
> I just upgraded my Ubuntu Lucid to Maverick RC and I found some bugs, I've been searching for 14 hours for this error and only found solutions for hardy, karmic, lucid and feisty, so I wanted to know if there's any solution, I tried a lot of things in the CCSM and nothing.
Here are the problems:
- Cannot move windows with mouse
- Cannot move windows to another workspace in expo
- Cannot scroll up/down with the bar, only the button
- Cannot open stacks in AWN
- Non existent plugin crashes in AWN
- When computer boots up it takes 2x the waiting time in comparison to lucid

I was anxious because 10.10 RC was released and it's actually having the worst errors I've ever experimented using Ubuntu since 8.10, And upgrading I never had to get help, In addition this never happened to me

What I did to try to solve this (And I failed):
- Disable all CCSM options a then enable
- Disbled auto sorting, enabled move
- Reinstalled Compiz

I thought it was a CCSM problem and I just discovered all that stuff I spent doing 14 hours was for nothing, so I came here to get help and I hope that someone answers me.

Thanks!

its probably your hardware(post your system specs)... for me the RC has worked perfectly fine on 4 computers of mine: 1 netbook, 1 laptop & 2 gaming desktops 

Anyways tomorrow already official 10.10 will be released - hopefully it doesn't repeat the same issue you encountered - if it does... maybe you need to try other drivers or simply newer *Ubuntu's aren't snappy to your hardware anymore

Also another note - Fresh install always goes better - upgrades sometimes tend to have issues(yes there are the case where upgrade goes smoothly, but sometimes it isn't a happy caddy)

---

### Post by P4man on 2010-10-09
Well, your problems all seem compiz related. Does everything work properly without it? Just press alt+F2 and run

```
metacity --replace
```

If that works fine, then I suspect a driver issue. What videocard do you have and what drivers are you using?

---

### Post by F1R3H4CK3R on 2010-10-10
I have a:
Dell Latitude D810
2GB Ram
512 MB ATI Video card
250 GB hard drive
1650x1080 resolution
1.88 GHz processor Inten Centrino
Ubuntu/Xubuntu 10.10 RC
Now I'll upgrade and see if it works well

However, thanks for all the support!

---

### Post by P4man on 2010-10-10
Looks like you have an ATI X300 or X600 mobility in there. My previous laptop had the integrated version of it (radeon xpress, product code is Rs480), but its essentially the same chip, just slower, and I remember it being blacklisted for compiz due to known stability issues. In fact it still is one of only 2 cards blacklisted:

[http://wiki.compiz.org/Hardware/Blacklist](http://wiki.compiz.org/Hardware/Blacklist)

Definitely a driver issue, but good luck with 10.10.

---

### Post by F1R3H4CK3R on 2010-10-12
Thanks but still I'm having the same troubles


Should I uninstall compiz? if yes could you please tell me the complete command?

Thanks!

---

### Post by P4man on 2010-10-12
Just turn off the effects  in system > preferences > appearance > visual effects.

---

### Post by F1R3H4CK3R on 2010-10-13
I'll see if that works to solve this, if nothing works, I'm just gonna do a fresh install of Ubuntu 10.10

---

