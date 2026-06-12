---
title: "Customizing Live CD : Edit Default Theme"
date: 2012-04-04
forum: General Help
---

### Post by lordbux on 2012-04-04
Hi all

I am trying to make a customized live CD using debootstrap
I succeed in creating it and ran it , It WOrks

I had Followed the instructions here
[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)
and
[http://ubuntuforums.org/showpost.php...73&postcount=1](http://ubuntuforums.org/showpost.php...73&postcount=1)

What i wnat to do is change the default gtk-them and Icon Theme
of the LiveCD

DISTRO:: Lucid Lynx 10.04

For this i tried editing the /etc/gconf/gconf.xml.defaults/%gconf-tree.xml
which now is :
Code:

```
<gconf>
	<entry name="primary_color" mtime="1333426712" type="string">
		<stringvalue>#000000000000</stringvalue>
	</entry>
	<entry name="secondary_color" mtime="1333426712" type="string">
		<stringvalue>#646467676a6a</stringvalue>
	</entry>
	<entry name="color_shading_type" mtime="1333426712" type="string">
		<stringvalue>solid</stringvalue>
	</entry>
	<entry name="picture_options" mtime="1333426712" type="string">
		<stringvalue>zoom</stringvalue>
	</entry>
	<entry name="picture_filename" mtime="1333426712" type="string">
		<stringvalue>/usr/share/backgrounds/Table_and_Bench.jpg</stringvalue>
	</entry>

	<entry name="menus_have_icons" mtime="1330334145" type="bool" value="true"/>
	<entry name="buttons_have_icons" mtime="1330334145" type="bool" value="true"/>
	<entry name="accessibility" mtime="1319885909" type="bool" value="true"/>
	<entry name="icon_theme" mtime="1313334262" type="string">
		<stringvalue>Faenza</stringvalue>
	</entry>
	<entry name="gtk_theme" mtime="1310091969" type="string">
		<stringvalue>Revamp</stringvalue>
</entry>

</gconf>

```
Revamp is a theme i wnat as default and Faenza is icon theme

But this does not seem to be working, dont get why
Please help

---

### Post by lordbux on 2012-04-04
I also tried changing directories inside did not help

---

