---
title: "Firefox Tab switching w ctrl-tab - screenshots don't highlight"
date: 2010-08-19
forum: General Help
---

### Post by finny388 on 2010-08-19
Is this an Ubuntu thing?

When I press ctrl-tab but hold ctrl down, screenshots of all tabs pop up - awesome!

I want to highlight one and release - as with alt-tab in Ubuntu/ Windows

But none of them highlight. I have no idea what tab will come up when I release ctrl.

I disabled all extensions to eliminate that side of things but no change - it appears to be a native thing.

But I first reported this on Mozilla's site and one user says it is not a default feature.

Is this an Ubuntu thing?  (Disabling all included disabling Ubuntu Firefox Modifications)

running:
Firefox 3.6.8
Ubuntu 10.04.1

---

### Post by M4he on 2010-08-19
Using the same setup as you; can't reproduce this bug though...
My tabs are highlighted just fine.

Are you using a special gnome theme? If so, did you try to change the theme back to Radiance and see if it happens there too?

---

### Post by finny388 on 2010-08-19
I changed theme to Radiance, didn't help

1. So this is a default feature in Ubuntu Firefox (as opposed to Windows)?

2. > My tabs are highlighted just fine. Your screen thumbnails are highlighting or the actual tabs? Do you get the thumbnails popping up?

3. How to disable this? It's useless and annoying as is.

---

### Post by finny388 on 2010-08-19
fyi I was using Dust theme with Ambiance borders

for the sake of reproducing setup.

thanks

---

### Post by M4he on 2010-08-19
1. I don't know exactly but you should be able to enable this in Windows too.

2. The thumbnails are highlighted just like that:
[ATTACH]166934[/ATTACH]
(click to enlarge)

3. You can disable the thumbnails (so the tabs are just switching with ctrl + tab) by

[LIST]
[*]typing "about:config" into the url bar (without the quotes)
[*]set "browser.ctrlTab.previews" to "false" (it should be set to true right now)
[/LIST]

---

### Post by finny388 on 2010-08-19
Thanks M4he

Darn it, it would be so nice for this to work!

side note: On my WinXP machine, I see browser.ctrlTab.previews set to True but it shows no thumbnails at all - as did that user on Mozilla's site.

Could this have to do with Compiz?

---

### Post by finny388 on 2010-08-21
bump

---

### Post by finny388 on 2010-08-23
nobody?

---

### Post by finny388 on 2010-08-27
anyone?

---

### Post by WorMzy on 2010-08-27
If I set that key/value to true, I get ctrl+tab previews (normally have them disabled, instant switch), and I have compiz.

[[IMG]http://img839.imageshack.us/img839/1791/lolololov.th.jpg[/IMG]]("http://img839.imageshack.us/img839/1791/lolololov.jpg")

Due to the colour scheme matching my GTK theme, I think that the lack of highlight may be caused by your current theme. Try changing your theme in System -> Preferences -> Appearance -> Theme, and seeing if that makes any difference.

---

### Post by finny388 on 2010-08-28
Thanks WorMzy,

Can you get yours to highlight by changing themes?

I tried changing from Dust to Radiance with no luck.

I'll try some others and report back. This is a rather weak flaw in my opinion.

---

### Post by finny388 on 2010-08-28
I've tried Dust, Radiance, Ambiance, and Clearlooks

They all show a black frame with a slight gradient lightening towards the top. I've attached another screenshot with Clearlooks theme enabled.

:(

---

### Post by WorMzy on 2010-08-28
I couldn't get it to change by switching GTK theme, but I have the AnyColor extension installed for Firefox, and editing the colours that I've set in that affects the highlight.

[[IMG]http://img834.imageshack.us/img834/8504/lolololox.th.jpg[/IMG]]("http://img834.imageshack.us/img834/8504/lolololox.jpg")
^ With white ^

[[IMG]http://img838.imageshack.us/img838/1372/lolololo.th.jpg[/IMG]]("http://img838.imageshack.us/img838/1372/lolololo.jpg")
^ With green ^

So there's a possible solution, albeit not the most convenient one.

I'd imagine that personas may have a similar affect, if you're into those.

---

### Post by finny388 on 2010-08-29
I'm not seeing any highlighting in your screenshots - correct?

Safe to say you have the exact same bug that I do?

arg, is this Mozilla or Ubuntu's fault?

---

### Post by WorMzy on 2010-08-29
?

No, I have highlighting.

In this [image]("http://img839.imageshack.us/img839/1791/lolololov.jpg") it was brown.
In this [image]("http://img834.imageshack.us/img834/8504/lolololox.jpg") it was light-grey.
In this [image]("http://img838.imageshack.us/img838/1372/lolololo.jpg") it was green.

In all three, it was the second tab that was highlighted. ;)

---

### Post by finny388 on 2010-08-29
ok thanks
very subtle color changes

I thought a band-aid solution would be to try Anycolor.

I went to [**firefox addons**]("https://addons.mozilla.org/en-US/firefox/addon/6991/") but it says it's only available for Windows.

are you having trouble with it? You're clearly using ubuntu (nice desktop btw)

---

### Post by WorMzy on 2010-08-29
Actually, it's Arch Linux, not Ubuntu, but it works on Ubuntu too. You should get the option to install it anyway:

[[IMG]http://img594.imageshack.us/img594/3050/201008292254261440x900s.th.png[/IMG]]("http://img594.imageshack.us/img594/3050/201008292254261440x900s.png")

I'm not sure why the developer has it listed as Windows only, but I can assure you that it works fine. Although, in the recent version of Firefox you may need to set a persona before it'll colourise the interface.

---

### Post by finny388 on 2010-08-29
I use Noia 2.0 as my theme.

I tried another and now I can see the highlighting. Perhaps Noia just doesn't support that.

phew.

thanks again for the feedback

---

### Post by WorMzy on 2010-08-30
So it's all sorted now, you just needed to change your Firefox theme? Hopefully that'll work for other people with this problem.

---

### Post by finny388 on 2010-08-30
Noia was one of the most popular themes before personas and still is.

It just didn't occur to me that the developer would overlook this.

With so many themes out there, it's no wonder I go so few replies.

Thanks MorMzy for helping me through
:)

---

