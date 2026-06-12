---
title: "Need Login Banner for 10.04"
date: 2011-08-09
forum: General Help
---

### Post by vitomacdoc on 2011-08-09
Hello,

I am using Ubunutu 10.04.3.  I need a login banner when any user logs into a machine.  Cannot seem to make it work.  This version does not seem to have the ability to paste a custom logon picture.

I tried all other suggestions on this forum, with gconftool-2, no luck

Does anyone have simple / easy solution to get a login banner?  If I have to make gdm point to an actual text file, like /etc/issue or something, that would be great.

Thank you.

---

### Post by pqwoerituytrueiwoq on 2011-08-09
try setting it in
edit this file as root
/var/lib/gdm/.gconf/apps/gdm/simple-greeter/%gconf.xml

```
<?xml version="1.0"?>
<gconf>
    <entry name="banner_message_text" mtime="1312554196" type="string">
        <stringvalue>**BANNER TEXT HERE**</stringvalue>
    </entry>
    <entry name="banner_message_enable" mtime="1309268220" type="bool" value="true"/>
    <entry name="recent-layouts" mtime="1309187269" type="list" ltype="string">
        <li type="string">
            <stringvalue>us</stringvalue>
        </li>
    </entry>
    <entry name="recent-languages" mtime="1309187269" type="list" ltype="string">
        <li type="string">
            <stringvalue>en_US.utf8</stringvalue>
        </li>
    </entry>
</gconf>
```for wall paper
/var/lib/gdm/.gconf/desktop/gnome/background/%gconf.xml
```
<?xml version="1.0"?>
<gconf>
    <entry name="primary_color" mtime="1309195316" type="string">
        <stringvalue>#000000000000</stringvalue>
    </entry>
    <entry name="secondary_color" mtime="1309195316" type="string">
        <stringvalue>#000000000000</stringvalue>
    </entry>
    <entry name="picture_filename" mtime="1309195316" type="string">
        <stringvalue>**/usr/share/backgrounds/BosqueTK.jpg**</stringvalue>
    </entry>
    <entry name="color_shading_type" mtime="1309195316" type="string">
        <stringvalue>solid</stringvalue>
    </entry>
    <entry name="picture_options" mtime="1309195316" type="string">
        <stringvalue>zoom</stringvalue>
    </entry>
</gconf>
```
Theme:
/var/lib/gdm/.gconf/desktop/gnome/interface/%gconf.xml
```
<?xml version="1.0"?>
<gconf>
    <entry name="gtk_theme" mtime="1309192882" type="string">
        <stringvalue>**HumanLogin**</stringvalue>
    </entry>
    <entry name="icon_theme" mtime="1309192882" type="string">
        <stringvalue>**HumanLoginIcons**</stringvalue>
    </entry>
    <entry name="gtk_color_scheme" mtime="1309192881" type="string">
        <stringvalue>fg_color:#ffffffffffff
bg_color:#000000000000
text_color:#ffffffffffff
base_color:#383838383838
selected_fg_color:#ffffffff0000
selected_bg_color:#00000000ffff
tooltip_fg_color:#000000000000
tooltip_bg_color:#f5f5f5f5b5b5</stringvalue>
    </entry>
</gconf>
```

---

### Post by vitomacdoc on 2011-08-10
Okay, I rebuilt a system from scratch and used the commands listed on other forums.
It modified the %gconf.xml file and works.

sudo -u gdm gconftool-2 --set --type string /apps/gdm/simple-greeter/banner_message_text "message here"

Now, I have a very lengthy banner.  How can I format so it is somewhat in line?
What are the XML characters for formatting?

Also, why can I not use gconf-editor tool?  If I run as root or sudo to gdm, I get nothing populated in the gui window.

Thanx

---

### Post by haqking on 2011-08-10
this is an old thread but might be what you are after.

[http://ubuntuforums.org/showthread.php?t=867475](http://ubuntuforums.org/showthread.php?t=867475)

---

