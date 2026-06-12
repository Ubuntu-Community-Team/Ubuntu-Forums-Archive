---
title: "Not Displaying to Full Monitor Dimensions"
date: 2012-02-21
forum: General Help
---

### Post by xAGENTP6x on 2012-02-21
Hey, I just got ubuntu installed on my new hard drive. Everything went smoothly. The one thing that's been bugging me tho is that the entire OS doesn't display to my monitor's full dimensions. I have my computer hooked up to a 40inch LN40BN Samsung LCD TV via hdmi cable.

In case anyone wants to ask what my PC specs are here..._[COLOR=Blue][http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02874899&cc=ca&dlc=en&lc=en&product=5097932](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c02874899&cc=ca&dlc=en&lc=en&product=5097932)[/COLOR]_

I have windows on my other hard drive on the same computer and it expands to fit my display, but when I boot ubuntu, I have 3 fingerwidths of black space around the outer edge of my TV. The System Settings>Display menu didn't offer me any solution or any options at all really. The TV is 1920x1080, and that's what I have it set to, but that black space is annoying.

Is this a common problem? Like is there any somewhat well known fix, or am I just gonna have to suck it up?

Oh BTW, I downloaded my GPU drivers and tried tinkering in my GPU Control Centre for display option, but that didn't get rid of the black space either.

---

### Post by Grenage on 2012-02-21
Underscan, isn't it fantastic?  You can try disabling it with xrandr, but I've never had to try it:

```
xrandr --output **DVI-0** --set underscan off
```

If you don't know what the port is called (and why would you?), you can query xrandr with:

```
xrandr -q
```

---

