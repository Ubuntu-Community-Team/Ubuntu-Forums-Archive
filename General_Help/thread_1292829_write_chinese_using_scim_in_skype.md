---
title: "write chinese using scim in skype"
date: 2009-10-16
forum: General Help
---

### Post by fcuk112 on 2009-10-16
has anyone gotten this to work?  there is some info @ [http://forum.skype.com/index.php?showtopic=390611](http://forum.skype.com/index.php?showtopic=390611) but i am not sure which locale to use.

cheers.

---

### Post by fcuk112 on 2009-10-16
bump

---

### Post by fcuk112 on 2009-10-16
bump

---

### Post by fcuk112 on 2009-10-17
bump

---

### Post by mantid on 2009-12-14
[FONT=Verdana][SIZE=2]You should be able to get it working with the following steps:
[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)[/SIZE][/FONT][FONT=Verdana][SIZE=2] - in the section "[/SIZE][/FONT][FONT=Verdana][SIZE=2]Incompatibilities with Some Applications". Worked for me![/SIZE][/FONT] 
[FONT=Verdana][SIZE=2]Edit /etc/profile and add:
```
# SCIM
export XMODIFIERS='@im=SCIM'
export GTK_IM_MODULE="scim"
export XIM_PROGRAM="scim -d"
export QT_IM_MODULE="scim"
scim -d
```[/SIZE][/FONT]
[FONT=Verdana][SIZE=2]
Edit  /etc/scim/global and modify:
[/SIZE][/FONT][FONT=Verdana][SIZE=2]```
/SupportedUnicodeLocales = zh_CN.UTF-8,en_US.UTF-8,en_GB.UTF-8
```[]("http://forum.skype.com/index.php?showtopic=390611")

The zh_CN.UTF-8 is the locale for Chinese. If you wish to add Hong Kong/Taiwan locales, add zh_HK.UTF-8 and zh_TW.UTF-8. Hope that helps.
[/SIZE][/FONT]

---

### Post by darklord06 on 2010-09-01
hello,

I modified /etc/profile and /etc/scim/global as stated above but it still won't work, scim is working with every application exept skype and Amsn, any idea ? thank you

---

