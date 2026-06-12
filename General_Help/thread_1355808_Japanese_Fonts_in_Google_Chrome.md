---
title: "Japanese Fonts in Google Chrome"
date: 2009-12-15
forum: General Help
---

### Post by nac.est on 2009-12-15
I'm trying out Google Chrome and everything seems to work ok, except for some glitches in Asian (Japanese) font rendering.
When the (serif styled) kanji are bold they appear "empty", when they are not bold they look somewhat "fuzzy", as can be seen in the attachments.

Also in some prompts, like the one asking confirmation to install a new extension (see attachments), the characters are just rendered as a boxy mess.

I've searched a lot but couldn't find anyone with a similar problem. What could be the cause?

Here's my ~/.fonts.conf file:
```
<?xml version="1.0"?><!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
    <match>
        <test qual="any" name="family">
            <string>sans-serif</string>
        </test>
        <edit name="family" mode="prepend" binding="strong">
	    <string>DejaVu Sans</string>
	    <string>VL PGothic</string>
            <string>Sazanami Gothic</string>
            <string>Kochi Gothic</string>
        </edit>
    </match>
    <match>
        <test qual="any" name="family">
            <string>serif</string>
        </test>
        <edit name="family" mode="prepend" binding="strong">
	    <string>DejaVu Sans</string>
	    <string>VL PGothic</string>
            <string>Sazanami Mincho</string>
            <string>Kochi Mincho</string>
        </edit>
    </match>
    <match>
        <test qual="any" name="family">
            <string>monospace</string>
        </test>
        <edit name="family" mode="prepend" binding="strong">
	    <string>DejaVu Sans Mono</string>
	    <string>VL Gothic</string>
            <string>Sazanami Gothic</string>
            <string>Kochi Gothic</string>
        </edit>
    </match>
    <match target="font">
 		<test name="lang" compare="contains">
			<string>ja</string>
		</test>
		<edit name="embeddedbitmap" mode="assign">
			<bool>false</bool>
		</edit>
		<edit name="autohint" mode="assign">
			<bool>true</bool>
		</edit>
                <edit name="antialias" mode="assign" >
                        <bool>true</bool>
                </edit>
		<edit name="hintstyle" mode="assign">
			<const>hintnone</const>
		</edit>
	</match>
</fontconfig>
```

I'm on Ubuntu 9.10.

---

### Post by svamppi on 2010-01-16
I have the same problem. Not sure if it's Chrome's or Ubuntu's developers' fault. Ubuntu has pretty crappy Japanese fonts by default anyway.

---

### Post by Zorael on 2010-01-16
I present to you [issue 18159](http://code.google.com/p/chromium/issues/detail?id=18159#makechanges).

Basically, Chromium isn't aware of **fontconfig**, which is what reads your **~/.fonts.conf** file and every other preset Ubuntu setting in **/etc/fonts/conf.d/**.

I have a pretty detailed setup over what fonts should be used, but Chromium disregards it entirely and runs its own race, guessing along the way. As a result I don't get bitmap fonts, resulting in fuzziness when they're at smaller pixel sizes, and it generally chooses fonts I don't want it to. For instance, some fairly common font that's used as headers in Wikipedia gets translated to my Kanji Stroke Order font (**ttf-kanjistrokeorders** in the repos). So if I zoom in, I can see the little numbers next to each stroke.

I've been meaning to comment on that issue for a while now, detailing my use case and presenting comparative screenshots, but I haven't had the time. So the only way to decently view Japanese pages right now is in other browsers. After having grown used to Chromium they're all awfully slow, though. *Especially* Firefox.

---

