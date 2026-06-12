---
title: "Selecting a window"
date: 2006-06-10
forum: General Help
---

### Post by jan247 on 2006-06-10
I don't know if it has been like this all along. But can I select a window just by clicking anywhere in it? (Not having to click on the title bar) I saw the select a window by mouseover option, but I want to have to click it but not just on the title bar. (Silly problem, I know)

---

### Post by meng on 2006-06-10
I've always selected a window by clicking anywhere on it, both in Windows and in Ubuntu.

---

### Post by aysiu on 2006-06-10
Same here.

What desktop environment are you using--Gnome, KDE, XFCE?

---

### Post by jan247 on 2006-06-11
Gnome.. hrm... so somthin must've gone wrong. I noticed it when Ubuntu just logged off, then restarted... Is there any way for me to fix this? (i.e., reinstall gnome, etc?)

---

### Post by oscar on 2006-06-11
I just had a look in gconf-editor and there is a setting in apps > metacity > general called raise_on_click , it looks like setting it to true should help. It is set to true by default. To run gconf-editor open up a terminal and go:
```
gconf-editor
```
Description:
Whether raising should be a side-effect of other user interactions

Long Description:
Many actions (e.g. clicking in the client area, moving or resizing the window) normally raise the window as a side-effect. Set this option to false to decouple raising from other user interactions. When false, windows can still be raised by an alt-left-click anywhere on the window or a normal click on the window decorations (assuming such clicks aren't used to start a move or resize operation). Special messages, such as activation requests from pagers, may also raise windows when this option is false. This option is currently disabled in click-to-focus mode.

---

### Post by jan247 on 2006-06-11
:-?  it is already set to true....

---

### Post by jan247 on 2006-06-11
please help...

---

### Post by Rui Pais on 2006-06-11
hi,
could you check if that happens with other users account too? 
If you are the only user and don't want to create new users you can temporarily mv your .gconf and .gnome out of the way, with:
cd && mkdir tmp_to_delete
mv .gconf* .gnome* tmp_to_delete/


And in gconf-editor, check that 
/apps/metacity/general/focus_mode is set to 'click'.

---

### Post by oscar on 2006-06-12
Perhaps you could post/look at what is in ~/.gconf/apps/metacity/general/%gconf.xml
```
cat ~/.gconf/apps/metacity/general/%gconf.xml
```
Only settings that are not the default values should be in there, for example mine looks like this:
```
<?xml version="1.0"?>
<gconf>
        <entry name="action_double_click_titlebar" mtime="1150028432" type="string">
                <stringvalue>toggle_shade</stringvalue>
        </entry>
        <entry name="titlebar_font" mtime="1147549700" type="string">
                <stringvalue>Sans Bold 10</stringvalue>
        </entry>
        <entry name="audible_bell" mtime="1147015215" type="bool" value="false">        </entry>
        <entry name="theme" mtime="1147952341" type="string">
                <stringvalue>Clearbox-out</stringvalue>
        </entry>
</gconf>
```
 Maybe you could see if there are any settings different in yours that look like they could cause the behaviour you are experiencing.

---

### Post by jan247 on 2006-06-13
Rui Pais was right. I moved everything then restored my settings manually. Everything was working just right, when I noticed that when I changed my keyboard settings (been tinkering with it for a while since numpad's not working properly), everything went wrong again. Can't select windows properly. Sigh, so I guess I'll just have to move everything again.

---

### Post by Rui Pais on 2006-06-14
hi,
glad to hear that you trace the problem. Good if it's just a config problem and not a borked gnome :)

When you put back your keyboard settings to default didn't the windows came back to narmality too? Or try to get which one of the conf files is responsible for that (copy files one by one from backup folder to ~/... anyway a process so boring then redo personal settings again :()

Btw, i think that the behaviour of windows being afected by a keyboard setting seems like a bug (maybe fill a bug report?).

---

