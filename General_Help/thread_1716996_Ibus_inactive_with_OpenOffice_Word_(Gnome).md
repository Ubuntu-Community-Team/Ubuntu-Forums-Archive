---
title: "Ibus inactive with OpenOffice Word (Gnome)"
date: 2011-03-29
forum: General Help
---

### Post by Xyldor on 2011-03-29
I have used a stand-alone version of Unikey (Vietnamese input method) for a while but I now want to include Chinese (simplified) and Pinyin input methods. Ibus seems to be the way the industry is going so I have been trying to set up my Ubuntu computer to use Ibus as the input method manager. So far I have managed to remove the original unikey and install the required IBUS methods.
GEdit seems to be working with some reservations, although it requires me to right click the text area and select "input methods->IBUS". The default is "System (X Input Method)". According to documentation I should just be able to use ctl-space to enable IBUS and alt+shift+L to switch methods.
Skype also runs fine too.
However Openoffice and the internet browsers like Firefox do not. The language bar remains inactive even after typing ctl+space.

I assume this problem is something to do with openoffice and the browsers picking up a default input method which is not IBUS.
How do I get OpenOffice and Firefox working with IBUS.

System->Administration->Language Support->Language-> Keyboard input method system is set to ibus.

These lists may help diagnose the problem.

```
mark@ubuntu:~$** im-switch -l**
Your input method setup under en_GB locale as below.
=======================================================
The configuration "/home/mark/.xinput.d/en_GB" is defined as a link pointing to
ibus
This private configuration supersedes the system wide default.
=======================================================
The system wide default is pointed by "/etc/alternatives/xinput-all_ALL" .
xinput-all_ALL - auto mode
 link currently points to default
default - priority 10
default-xim - priority 0
none - priority 0
Current `best' version is default.
=======================================================
The available input method configuration files are:
default default-xim ibus lo-gtk none th-gtk th-xim 
=======================================================
```and 


```
mark@ubuntu:~$ **cat /etc/alternatives/xinput-all_ALL **
#
# This configuration provides default IM setting (user edittable)
# See im-switch(8) and /usr/share/doc/im-switch/README.Debian .

#
# Define IM for traditional X application with XIM
#
#  XIM server name used for XMODIFIERS="@im=$XIM"
#  XIM program /path/filename
#  XIM program command line arguments
#
#  These were traditional setting before uim and scim for CJK languages
#  Language   LC_CTYPE     XIM server XMODIFIERS              Start key
#  Japanese   ja_JP*       kinput2    "@im=kinput2"           Shift-Space
#  Korean     ko_KR*       ami        "@im=Ami"               Shift-Space
#  Chinese(T) zh_TW.Big5   xcin       "@im=xcin-zh_TW.big5"   Ctrl-Space
#  Chinese(S) zh_CN.GB2312 xcin       "@im=xcin-zh_CN.GB2312" Ctrl-Space
# 
XIM=
XIM_PROGRAM=
XIM_ARGS=
XIM_PROGRAM_XTRA=
# Set following variable to non-zero string if program set itself as deamon
XIM_PROGRAM_SETS_ITSELF_AS_DAEMON=
#
# Define GTK and QT IM module
#   They may or may not be using xim as the IM.
#
GTK_IM_MODULE=
QT_IM_MODULE=

#
# Define lists of packages neded for above IM to function
#
DEPENDS=

#
# Define X start up hook script to update IM environment
#

```

I have also tried adding to the ~/.bashrc file
```

export GTK_IM_MODULE=ibus
export XMODIFIERS=@im=ibus
export QT_IM_MODULE=ibus

```
as mentioned for the KDE fix. That didn't change anything.

---

### Post by James.Lazo on 2011-05-11
I'd like to bump this thread. This issue appeared out of nowhere for me in Maverick, and it is still present in LibreOffice for Natty. Firefox 4 seems to accept ibus input now. Any tips on how to get Libre/OpenOffice and ibus communicating again? For what it's worth, my set up is Alt+~ to toggle on/off input method, Ctrl+Space to switch between input methods (Mozc/Pinyin), and English input method removed. I saw no conflicting shortcuts in LibreOffice.

**UPDATE**
I found the preferred method for activating input method in *Office here:
[http://ubuntuforums.org/showthread.php?t=1644951](http://ubuntuforums.org/showthread.php?t=1644951)

```
im-switch -s ibus
```

---

