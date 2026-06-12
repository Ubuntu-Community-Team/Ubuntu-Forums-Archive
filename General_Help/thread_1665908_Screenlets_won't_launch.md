---
title: "Screenlets won't launch"
date: 2011-01-12
forum: General Help
---

### Post by Hobble on 2011-01-12
Hi, I'm new to Linux so I'm sorry if this is a stupid one. I googled a few variations but couldn't find a problem that matched exactly.
I recently installed Screenlets, but for some reason it won't launch. It gives no error message at all.

In terminal I get this message when trying to run it.

```

** (screenlets-manager.py:21400): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (screenlets-manager.py:21400): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (screenlets-manager.py:21400): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
mkdir: cannot create directory `/home/shane/.screenlets': Permission denied
/usr/share/screenlets-manager/screenlets-manager.py:93: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips = gtk.Tooltips()
/usr/share/screenlets-manager/screenlets-manager.py:414: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but1, _('Launch/add a new instance of the selected Screenlet ...'))
/usr/share/screenlets-manager/screenlets-manager.py:415: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but2, _('Install a new Screenlet, SuperKaramba or Web Widget or Web Application  ...'))
/usr/share/screenlets-manager/screenlets-manager.py:416: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but3, _('Permanently uninstall/delete the currently selected Screenlet ...'))
/usr/share/screenlets-manager/screenlets-manager.py:417: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but4, _('Reset this Screenlet configuration (will only work if screenlet isnt running)'))
/usr/share/screenlets-manager/screenlets-manager.py:418: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but5, _('Install new theme for this screenlet'))
/usr/share/screenlets-manager/screenlets-manager.py:419: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but6, _('Restart all screenlets that have auto start at login'))
/usr/share/screenlets-manager/screenlets-manager.py:420: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but7, _('Close all Screenlets running'))
/usr/share/screenlets-manager/screenlets-manager.py:421: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but8, _('New Screenlets Options/Properties'))
/usr/share/screenlets-manager/screenlets-manager.py:422: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but9, _('Create a Desktop shortcut for this Screenlet'))
/usr/share/screenlets-manager/screenlets-manager.py:477: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but_about, _('Show info about this dialog ...'))
/usr/share/screenlets-manager/screenlets-manager.py:478: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but_download, _('Download more screenlets ...'))
/usr/share/screenlets-manager/screenlets-manager.py:479: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but_close, _('Close this dialog ...'))
File /home/shane/.screenlets/config.ini not found
Traceback (most recent call last):
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 1308, in <module>
    app = ScreenletsManager()
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 95, in __init__
    self.create_ui()
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 487, in create_ui
    self.recreate_infobox(None)
  File "/usr/share/screenlets-manager/screenlets-manager.py", line 522, in recreate_infobox
    f = open(DIR_USER + '/config.ini', 'w')
IOError: [Errno 2] No such file or directory: '/home/shane/.screenlets/config.in

```Has anybody had this problem or know how I can fix it?

---

### Post by Vaphell on 2011-01-13
this part looks suspicious
mkdir: cannot create directory `/home/shane/.screenlets': Permission denied

did you play with permissions in your home folder?
what does **ls -la ~** say? Does everything have your name next to it and rw in the first triplet of permissions (owner's read/write/execute)? especially check . and .screenlets (if it exists)

---

### Post by Hobble on 2011-01-13
Thank you for the quick reply.

Everything has my name next to it except for Mozilla and Veetle which have 1016 instead.
What does the command I just put in mean by the way?

---

### Post by Vaphell on 2011-01-13
ls = list stuff (probably has different meaning in reality ;-))
-l = long detailed description (without you get only names)
-a = means show hidden stuff too (beginning with . or ending with ~), here combined into 1 piece with -l 
~ = your home dir

together: list all stuff located in home folder (hidden stuff included), with a detailed info.

**ls --help** to see what you can get from ls command. 99% of the commands has --help/-h option that gives a rich description of available options, if you don't know what to do, check it first. There is also a **man <command>**

are you able to create .screenlets dir manually in file browser (ctrl+h to show hidden files/dirs)? something is definitely not right, judging from the permission denied error, screenlets can't create their hidden config dir and it falls apart later where files from that dir are required.

---

### Post by Hobble on 2011-01-13
I checked my home/shane folder and found that both owner and group are set to 1016 or user #1016. I've found some discussions about this so I'll see what it's about.

---

### Post by Hobble on 2011-01-13
Okay, so I changed the permissions from user 1016 to me, and now screenlets opens fine. I'll keep looking into the 1016 issue because it's pretty creepy. Thank you so much for your help.

---

