---
title: "Firefox 3.5 UI text too big"
date: 2009-07-14
forum: General Help
---

### Post by Dave_Jackson on 2009-07-14
I just downloaded Firefox 3.5 final from the Proposed Updates repo. 
The problem is its interface. The menu text is rendered unproportionally large and it's not aliased at all. 

This only occurs in Firefox 3.5. In all other programs text is rendered according to my gnome theme settings. Does anyone have any ideas about this? Thanks in advance.

Here's a screenshot below so it's really clear what I'm talking about:
Compare the UI text sizes of Firefox 3.0.11 and 3.5 and you'll see a big difference.

---

### Post by DeMus on 2009-07-14
> **Dave_Jackson said:**
> I just downloaded Firefox 3.5 final from the Proposed Updates repo. 
The problem is its interface. The menu text is rendered unproportionally large and it's not aliased at all. 

This only occurs in Firefox 3.5. In all other programs text is rendered according to my gnome theme settings. Does anyone have any ideas about this? Thanks in advance.

Here's a screenshot below so it's really clear what I'm talking about:
Compare the UI text sizes of Firefox 3.0.11 and 3.5 and you'll see a big difference.

Maybe my eyes are not that good, but I don't see the difference. Can you send 2 more pictures with exactly the same content? This way it is better noticeable.

---

### Post by itsjareds on 2009-07-14
Yep, this is a known problem. I just fixed this on my computer yesterday. It has to do with Ubuntu's Firefox addon not being compatible with 3.5 yet. That's the main reason why Ubuntu doesn't release 3.5 standard yet. This addon changed the fonts, at least that's what I think.

Anyways, different solutions work for different people. Here's the thread where a bunch of workarounds are listed:

[http://ubuntuforums.org/showthread.php?t=1128929]("http://ubuntuforums.org/showthread.php?t=1128929")

For me, I made a ~/.fonts.conf file with some font settings. This is what worked for me:

~/.fonts.conf:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
	<match target="font">
		<edit mode="assign" name="antialias">
			<bool>true</bool>
		</edit>
		<edit mode="assign" name="hinting">
			<bool>true</bool>
		</edit>
	</match>
</fontconfig>
```

Now my Firefox looks like it used to :)

edit: This may only be a problem with the Firefox 3.5 Beta installed from Synaptic. That's what I did.

---

### Post by khelben1979 on 2009-07-14
I have downloaded and installed Firefox 3.5 directly from mozilla.org and I don't have the problem which you have described here.

Just thought you should know.

---

### Post by Dave_Jackson on 2009-07-14
Thanks to all who took the time to respond. After perusing itsjared's forum link [http://ubuntuforums.org/showthread.php?t=1128929&page=4]("http://ubuntuforums.org/showthread.php?t=1128929&page=4"), I believe I have found the simplest way to correct this problem.

In that thread, amn108 wrote: > Funny i just removed all /etc/files/conf.d/10-* and after that "dpkg-reconfigure fontconfig" and Firefox 3.5 started to obey my Gnome text rendering ways. That is all it took..

Although, in my case, the correct path was **/etc/fonts/conf.d** and I just deleted all files in that folder that had a 10 in their name. Should only be a few of them. After rebuilding the fonts cache with dpkg-reconfigure fontconfig, all was well with no ill effects. By the way, you must do this as root with su or sudo. 

It really is as simple as that. 
Now my Firefox 3.5 fonts look identical to my other applications in gnome.

Other users in that thread suggested modifying font files like ~/.fonts.conf. Someone said that this approach messed up their fonts (maybe multiple font file problems?), so this may not be the cleanest workaround and if done wrong it may hurt more than it helps. 

I hope Ubuntu can fix this soon. I know it hasn't been out that long, but if anyone at Canonical had actually loaded the program, they would have seen the font discrepancies. Yes, I know this was in proposed updates, so maybe I shouldn't complain much, but still...

---

### Post by itsjareds on 2009-07-14
Hmm, I just disabled my .fonts.conf and tried your way, and it also worked for me. I like your way better, it doesn't depend on one file. And it seems more integrated.

Thanks :P

---

