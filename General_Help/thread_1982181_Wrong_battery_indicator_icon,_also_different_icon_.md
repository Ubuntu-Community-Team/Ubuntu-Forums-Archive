---
title: "Wrong battery indicator icon, also different icon in other themes"
date: 2012-05-18
forum: General Help
---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-05-18
This morning something happened with my battery indicator icon. It changed to an icon which is not a part of my icon theme. Also, no matter which Icon theme I change to, the battery icon does not seem to be from that icon theme:
Faenza theme:
[IMG]http://files.myopera.com/tomica/files/indicators_faenza.png[/IMG]
Ubuntu Dark theme:
[IMG]http://files.myopera.com/tomica/files/indicators_ubuntu_dark.png[/IMG]
Gnome theme:
[IMG]http://files.myopera.com/tomica/files/indicators_gnome.png[/IMG]

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-05-18
And another weird thing just happened. The icon changed back to normal by itself, I didn't even notice when. So I took a screenshot of it. Here's the normal battery icon:
[IMG]http://files.myopera.com/tomica/files/icon_normal.png[/IMG]
But right after I took the screenshot, the very next moment the icon changed to the wrong one again! It looks like this again:
[IMG]http://files.myopera.com/tomica/files/indicators_faenza.png[/IMG]

---

### Post by ubiquitin.jf on 2012-05-18
This is a known bug in the Faenza iconset - you need to use the "Faenza-Ambiance" variant of the theme.

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-05-18
I am using the Faenza Ambience theme... Since my post, the icon keeps changing back and forth between these two. Is there any solution? It really wasn't happening befre, and I've been using Faenza for 3 months.

---

### Post by AliFeraoon on 2012-05-18
Yaa It happened with me too and I'm trying to find the solution

---

### Post by AliFeraoon on 2012-05-19
Try this Link:
[http://askubuntu.com/questions/73545/faenza-ubuntu-mono-power-icon-problems](http://askubuntu.com/questions/73545/faenza-ubuntu-mono-power-icon-problems)

---

### Post by portermiked on 2012-05-19
image 1 = plugged in
image 2 = unplugged.

using the default ambient theme, not sure when it happened, is making me more sad than it should lol, i take pride in the beautiful appearance of ubuntu and this is a bummer!

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-05-19
AliFeraoon thanks for the link. I didn't try it out, but in any case, that's just a workaround. I'd like to find the cause for this bug...

---

### Post by ricardofilipemoreira on 2012-05-19
this happened to me too. I'm using ambiance, the default theme. I guess it must have been an update, but I hope this isn't final. Though the icon has a light and a dark version. But the Power Statistics dialog (clicking on the indicator and then the "N:NN remaining" menu) still shows the original icon. :(

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-05-23
I think I've managed to solve it by re-installing the Faenza Theme. I did it a couple of days ago and since then the icon remained propper.

---

### Post by AliFeraoon on 2012-05-24
Yes good it's work if you re-instal that theem named Faenza but what about other theems like [portermiked]("http://ubuntuforums.org/member.php?u=1548182")'s theem

---

### Post by AliFeraoon on 2012-05-24
mmmmm after (installing) Faeza theem as [&#1058;&#1086;&#1084;&#1080;&#1094;&#1072;]("http://ubuntuforums.org/member.php?u=922312") posted the battery icon changed successfully as i wrote in the previous post, but when i return to the Ubuntu-Mono-dark theem it return to the strange icon again , after that i found a new update and after restarting i found the Ubuntu-Mono-Dark battary icon fixed to normal ^_^ ..... I hope this long story help anyone need solution ..lol

---

### Post by The Bright Side on 2012-09-18
Issue occurs again for me... Was fine on my old laptop for over a year, but I just installed Ubuntu on my new laptop and the problem is back. I have no way of getting the correct icon back, unless I go back to the Ubuntu Mono themes.

I solved it by turning the indicator off. I don't need it anyway, as I'll probably never run the laptop off battery power. But I'm curious... Do you guys know if Ubuntu will still give you a low battery warning even when in the power settings, the indicator icon is set to never appear?

Anybody else have this problem?

---

### Post by jrog on 2012-10-20
> **The Bright Side said:**
> Issue occurs again for me... Was fine on my old laptop for over a year, but I just installed Ubuntu on my new laptop and the problem is back. I have no way of getting the correct icon back, unless I go back to the Ubuntu Mono themes.

I solved it by turning the indicator off. I don't need it anyway, as I'll probably never run the laptop off battery power. But I'm curious... Do you guys know if Ubuntu will still give you a low battery warning even when in the power settings, the indicator icon is set to never appear?

Anybody else have this problem?
I'm having this problem. Haven't solved it yet.

---

### Post by jrog on 2012-10-21
For those of you still suffering from this issue, I figured that I'd mention that I've temporarily fixed it, at least to my satisfaction (and hopefully to yours, as well). 

The basic solution is this:

1. Go into the main Faenza directory (wherever you've installed your icons -- and not Faenza-Dark, Faenza-Ambiance, etc., but just Faenza) and delete the following files from the status/scalable folder:

battery-full-charged-symbolic.svg
battery-caution-charging-symbolic.svg 
battery-full-charging-symbolic.svg 
battery-low-charging-symbolic.svg 
battery-empty-charging-symbolic.svg 
battery-good-charging-symbolic.svg

2. Recreate those files as symbolic links pointing to the appropriate icon for the version of Faenza that you are using. For example, if you are using Faenza-Dark, then you'll want to create a link in the Faenza/status/scalable folder pointing to <directory-path>/Faenza-Dark/status/22/battery_charged.png. 

In my case, Faenza is located at /usr/share/icons/Faenza, so I first go to /usr/share/icons/Faenza/status/scalable and remove the above files, then, still in the /usr/share/icons/Faenza/status/scalable folder, I create symbolic links with those filenames that point to /usr/share/icons/Faenza-Dark/status/22/battery_charged.png, e.g.:

```
ln -s /usr/share/icons/Faenza-Dark/status/22/battery_charged.png battery-full-charged-symbolic.svg
```

I do this for each of the files that I originally deleted, in step 1. 

NOTE: The only minor problem that I can see with this solution is that there are not a variety of good-looking Faenza icons for the 'charging' battery states. The ugly ones, about which people are complaining in this thread, are at least nice in that they reflect the current state of the battery (e.g., low, good, full, etc.) **even while it is charging**. The nice-looking icons only reflect the current state of the battery **when it is unplugged** -- when it is plugged in, you only get one (nice-looking!) icon that shows only that the battery is plugged in, but that does not show its current state. I can live with that if it means that I won't have those ugly icons any more, but your opinion might vary.

BTW, I wrote a script that will perform these steps automatically, for anyone interested. It's attached to this message. I've only tested it a few times under a few scenarios, and I'm sure it has bugs (for example, it will crash if, for some reason, you type a word instead of entering a number at one point in the script -- but you shouldn't enter a word unless you're trying to crash the script anyway, and I don't have time to fix it!), so you've been warned. Every time I've tried it and not tried to crash it by intentionally giving bad input, it's worked.

---

### Post by madkox1 on 2012-11-24
**jrog**, thanks for great script, but it does not worked for me. In my case there are no *.png files in icons folder at all - only *.svg. So I replaced this part of your script:

```

# Now we create symbolic links to the appropriate icon for our chosen style.
ln -sv "$ICON_PATH"/battery_charged.png battery-full-charged-symbolic.svg
ln -sv "$ICON_PATH"/battery_charged.png battery-caution-charging-symbolic.svg
ln -sv "$ICON_PATH"/battery_charged.png battery-full-charging-symbolic.svg
ln -sv "$ICON_PATH"/battery_charged.png battery-low-charging-symbolic.svg
ln -sv "$ICON_PATH"/battery_charged.png battery-empty-charging-symbolic.svg
ln -sv "$ICON_PATH"/battery_charged.png battery-good-charging-symbolic.svg

```with this one:
```

# Now we create symbolic links to the appropriate icon for our chosen style.
ln -sv "$ICON_PATH"/gpm-battery-charged.svg battery-full-charged-symbolic.svg
ln -sv "$ICON_PATH"/gpm-battery-020-charging.svg battery-caution-charging-symbolic.svg
ln -sv "$ICON_PATH"/gpm-battery-100-charging.svg battery-full-charging-symbolic.svg
ln -sv "$ICON_PATH"/gpm-battery-040-charging.svg battery-low-charging-symbolic.svg
ln -sv "$ICON_PATH"/gpm-battery-000-charging.svg battery-empty-charging-symbolic.svg
ln -sv "$ICON_PATH"/gpm-battery-060-charging.svg battery-good-charging-symbolic.svg

```and it works. Also it creates links to different state files, so you now get nice looking battery icons all the time, even when your battery is charging (in 6 steps).

---

### Post by jrog on 2012-11-25
First, I'm glad this worked out for you. I've been hoping that someone else would give this a try and let us know. Thanks for the additional info. that you provided, too!

I'm curious about the fact that the .png files weren't in place for you. Do you know what version of the Faenza icon theme you have installed? And can you mention which variant of the theme you were using (e.g., Faenza, Faenza-Ambiance, Faenza-Dark, etc.)? 

The reason I ask is that I'm using version 1.2 of the icon theme, and it does seem to include the relevant .png files for Faenza and the Faenza-Dark variants, but **not** for the Ambiance and Radiance variants (see the output below this paragraph). This has me concerned that maybe the script that I uploaded won't work for the Ambiance and Radiance variants, which I originally thought were simply dependent on the original Faenza for the battery icons; I might have to poke around a bit and edit it. I never use the Ambiance or Radiance variants, so I'm less familiar with how they work.

```
$ dpkg-query -L faenza-icon-theme | grep \/22\/battery_charged
/usr/share/icons/Faenza-Ambiance/status/22/battery_charged.svg
/usr/share/icons/Faenza/status/22/battery_charged.png
/usr/share/icons/Faenza-Dark/status/22/battery_charged.png
/usr/share/icons/Faenza-Radiance/status/22/battery_charged.svg

```

EDIT: It might just be better for me to edit the script to include the lines you mentioned anyway, if that truly does give you different state icons for charging the battery that are still pleasant looking, but I'm curious about the above stuff either way. I'll be playing around with the script in either case.

SECOND EDIT: Yeah, based on a very quick check, it does look like there are those different state icons for charging in each variant of the theme, so I'll try to fix the script so that it works with them "out of the box." Oddly, the files are .png files for Faenza and Faenza-Dark(er|est), but they're .svg files for the other variants, but that's a minor annoyance. Thanks for your help with this!

---

### Post by madkox1 on 2012-11-27
As you already have guessed, I'm using Faenza-Ambiance. It's version 1.3 from tiheum-equinox-quantal ppa, and:
```

dpkg-query -L faenza-icon-theme | grep \/22\/battery_charged
/usr/share/icons/Faenza-Ambiance/status/22/battery_charged.svg
/usr/share/icons/Faenza-Radiance/status/22/battery_charged.svg
/usr/share/icons/Faenza-Dark/status/22/battery_charged.png
/usr/share/icons/Faenza/status/22/battery_charged.png

```
..it's still *png for Faenza and Faenza-Dark, and *.svg for Ambiance/Radiance. 

I'm glad to be helpful, anyways.

---

