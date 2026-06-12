---
title: "Yiddish Keyboard in Ubuntu 12.04"
date: 2012-07-16
forum: General Help
---

### Post by gettheinfoandgo on 2012-07-16
Hi everyone,
i've found information on how to use unicode [here ]("http://www.cs.uky.edu/%7Eraphael/yiddish/unix.html")but have not gotten it to work.  I've also seen windows and mac solutions, maybe i should use a VM...

Is there some way to modify the hebrew keyboard layout to include the missing Yiddish characters?  

Also, when I type in Libreoffice with hebrew characters the comma reverts to left to right.  Any thoughts?

Any help would be very much appreciated!!!

---

### Post by danilius on 2012-07-16
Which missing letters are you referring to? I appear to have them all, including Nekudot.

---

### Post by gettheinfoandgo on 2012-07-17
Thanks for responding.

Unless I'm missing something obvious, I think I have to go through a character map to use vowels like Pasekh Alef and Komets Alef and the characters with yud and vov.  Any way around that?

---

### Post by danilius on 2012-07-17
If you have the standard Hebrew keyboard, then in LibreOffice the Nekudot can be inserted by holding down the Alt-Gr key (the Alt key to the right of the space bar) and then tapping any of the numbers above the main part of the keyboard. This will provide you with the Dagesh as well, which is what I think you wrote "and the characters with yud and vov".

---

### Post by gettheinfoandgo on 2012-07-17
Thank you, that's a bit easier...it's still time consuming, though, considering the frequency those vowels are used.  i really need to be able to type quickly (taking notes in class, etc.)

Is there a way to set up a key board like one of [these]("http://www.shoshke.net/uyip/keyboards.htm")?  The phonetic one is particularly appealing.

---

### Post by danilius on 2012-07-17
It's only moderately painful, but spend a half-hour or so perusing [this link]("https://help.ubuntu.com/community/Howto%3A%20Custom%20keyboard%20layout%20definitions") and having a go, you will probably find it quite straightforward.

If you have any success, make a pint of sharing it; this thread would be a great place to start.

---

### Post by gettheinfoandgo on 2012-07-17
So after a few hours of poking around and trying different approaches, I ended up following these steps, which gave me [this keyboard]("http://www.cs.uky.edu/%7Eraphael/yiddish/keymap.pdf"):

**xkb**

 Instead of using X-windows keymaps, you can use the X keyboard extension, known as xkb.  This facility lets you establish several keyboard layouts and switch between them.  This facility is independent of all X-windows applications.  It does not give you multiple-key translations. Here are instructions for Ubuntu Linux. 
[LIST=1]
[*] Make sure you don't have XKB_DISABLE set in your environment variable.
[*] As root, append to /usr/share/X11/xkb/symbols/us the contents of [this file]("http://www.cs.uky.edu/%7Eraphael/yiddish/xkb.txt").
[*] In /usr/share/X11/xkb/rules, put the following line at the end of the us: section (around line 269) of both base.lst and evdev.lst:  yiddish         us: Yiddish 
[*] In /usr/share/X11/xkb/rules, put the following line within the "us" <layout>, in the variantList after the Russian phonetic variant, in both base.xml and evdev.xm::        <variant>           <configItem>             <name>yiddish</name>             <description>Yiddish</description>             <languageList><iso639Id>yid</iso639Id></languageList>           </configItem>         </variant> 
[*] Run setxkbmap us
[*] Using gnome-keyboard-properties, under the "Layouts" tab,
[LIST=1]
[*] 	Add a layout: By language &#8594; Yiddish 	&#8594; USA Yiddish
[*] 	Set Layout Options so you know the keys to change 	layout.  You might want to use keyboard LED to show alternative layout.
[/LIST]
 
[*] Run setxkbmap -option grp:switch,grp:alts_toggle
[*] You can now use (1) whatever you set up in the previous step to switch layouts, (2) the shift key to switch levels and (3) the right-alt key to switch groups (a few keys have a second group of symbols).  The keyboard looks like [this pdf file]("http://www.cs.uky.edu/%7Eraphael/yiddish/keymap.pdf").  If you need to type non-precomposed letters, separating an alef from its pasekh, for instance, use the vowels positioned on the Q key or the group-two symbols on various other keys.
[/LIST]

I found these directions on Raphael Finkel's page [Yiddish and Unix]("http://www.cs.uky.edu/%7Eraphael/yiddish/unix.html#xkb"), which is quite helpful and has links to many other Yiddish related resources.  

It doesn't seem perfect, but it's functional!

Let me know what you think.

---

### Post by videonaut on 2012-09-15
Ran steps 2-5 above. Ubuntu 12.04 does not have gnome-keyboard-properties installed (nor is it available in the repository) so I went through the normal Keyboard Layout UI. Still don't see a Yiddish option.

I ran "echo $XKB_DISABLE" in a terminal window and got no response, so it doesn't appear to be set.

Any way I can diagnose what is wrong?

Update: I'd installed xfce earlier today. First time I logged into xubuntu was 15 minutes ago: lo and behold, the Yiddish keyboard layout was there in the keyboard layout choices. I'm now happily typing pasekh alef and such into LibreOffice.

---

