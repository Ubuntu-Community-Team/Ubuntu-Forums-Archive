---
title: "Fontconfig error: &quot;~/.fonts.conf&quot;, line 8: junk after document element"
date: 2010-06-19
forum: General Help
---

### Post by Silvernail on 2010-06-19
On Lucid Lynx
On several apps when called from the command line, I get this warning:
> 
dave@dave:~$ gedit .fonts.conf
Fontconfig error: "~/.fonts.conf", line 8: junk after document element


First part of ".fonts.conf" below:
> 
<?xml version='1.0'?>
<!DOCTYPE fontconfig SYSTEM 'fonts.dtd'>
<fontconfig>
    <dir>/home/dave/.fontmatrix</dir>
    <dir>/home/dave/.Fontmatrix/Activated</dir>
</fontconfig>

<?xml version="1.0"?><!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
	<test name="weight" compare="more">
		<const>medium</const>
	</test>
	<edit name="hintstyle" mode="assign">
		<const>hintnone</const>
	</edit>
</match>
** snip snip snip snip snip **

This sounds like none of the configuration is getting done.
What do I  need to do to get this to work properly?

---

### Post by ajgreeny on 2010-06-19
Interesting!

I don't have a **.fonts.conf** file at all, so wonder what would happen if you just removed it, or renamed it so it is not read.

If that's not what you want to do try changing line 8 from
```
<?xml version="1.0"?><!DOCTYPE fontconfig SYSTEM  "fonts.dtd">
```
to
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM  "fonts.dtd">
```
so it is more like the paragraph above, ie on two lines, not just one.

---

### Post by Silvernail on 2010-06-19
Thanks ajgreeny.
I tried your second suggestion first and no joy.
Called 'gedit' got message.
Rebooted, called 'gedit' got message.

Moved .fonts.conf to .fonts.conf.backup.
Called 'gedit', [COLOR="Red"]DID NOT[/COLOR] get message.

Later I am going to reinstall '.fonts.conf' and see if my '/var/log/fontconfig.log' file still has all the message as exampled below:
> /usr/share/fonts/X11: skipping, existing cache is valid: 0 fonts, 6 dirs
/usr/share/fonts/X11/100dpi: skipping, existing cache is valid: 0 fonts, 0 dirs
/usr/share/fonts/X11/75dpi: skipping, existing cache is valid: 0 fonts, 0 dirs
/usr/share/fonts/X11/Type1: skipping, existing cache is valid: 163 fonts, 0 dirs
/usr/share/fonts/X11/encodings: skipping, existing cache is valid: 0 fonts, 1 dirs
/usr/share/fonts/X11/encodings/large: skipping, existing cache is valid: 0 fonts, 0 dirs
/usr/share/fonts/X11/misc: skipping, existing cache is valid: 0 fonts, 0 dirs
/usr/share/fonts/X11/util: skipping, existing cache is valid: 0 fonts, 0 dirs
/usr/share/fonts/truetype: caching, new cache contents: 4 fonts, 72 dirs
/usr/share/fonts/truetype/adf: skipping, existing cache is valid: 143 fonts, 0 dirs
/usr/share/fonts/truetype/aenigma: skipping, existing cache is valid: 465 fonts, 0 dirs
/usr/share/fonts/truetype/alee: skipping, existing cache is valid: 5 fonts, 0 dirs
/usr/share/fonts/truetype/beteckna: skipping, existing cache is valid: 5 fonts, 0 dirs
/usr/share/fonts/truetype/denemo: skipping, existing cache is valid: 1 fonts, 0 dirs
/usr/share/fonts/truetype/dustin: skipping, existing cache is valid: 20 fonts, 0 dirs
/usr/share/fonts/truetype/engadget: skipping, existing cache is valid: 1 fonts, 0 dirs


I did go looking for the named fonts above and several of the font managers would display them as well as Gimp.

Thanks again..

---

