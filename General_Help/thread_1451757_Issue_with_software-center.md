---
title: "Issue with software-center"
date: 2010-04-10
forum: General Help
---

### Post by vncfrrll on 2010-04-10
I have an issue with software center that causes it not to run. I have run all of the cleaning scripts and even deleted all associated packages and reinstalled them, but I continue to get the same error when starting software-center.

Here is the dump from terminal: (running most current 64-bit Lucid Lynx)

> vince@LucidLynx:~$ software-center
/usr/share/software-center/softwarecenter/view/appview.py:856: GtkWarning: gtk_tree_view_column_set_fixed_width: assertion `fixed_width > 0' failed
  column.set_fixed_width(0)
No styling hints for HumanLogin were found... using Human hints.
No styling hints for HumanLogin were found... using Human hints.
No styling hints for HumanLogin were found... using Human hints.
No styling hints for HumanLogin were found... using Human hints.
No styling hints for HumanLogin were found... using Human hints.
Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 200, in __init__
    self.view_switcher = ViewSwitcher(datadir, self.db, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 57, in __init__
    store = ViewSwitcherList(datadir, db, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 203, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 277, in _update_channel_list
    self.append(self.available_iter, [channel.get_channel_icon(),
AttributeError: 'list' object has no attribute 'get_channel_icon'
vince@LucidLynx:~$ 
Could someone help me out please? A quick response would be appreciated immensely.

---

### Post by RedSingularity on 2010-04-11
Have you tried removing software center **including all the hidden config files?**

---

### Post by vncfrrll on 2010-04-11
I have removed software center, but could you please direct me to the hidden files?

---

### Post by RedSingularity on 2010-04-11
Ok, remove the software center again and use this command to find any residual files.

sudo find / -name software-center*

---

### Post by vncfrrll on 2010-04-12
Alright, I removed software-center, and used the command you said and deleted all of the files and directories it found. Then I reinstalled software-center and got the exact same error from Terminal.

---

### Post by vncfrrll on 2010-04-16
bump...

---

### Post by RedSingularity on 2010-04-16
Did you have it working at one time in the past?

---

### Post by vncfrrll on 2010-04-16
Yes I did...and beautifully at that.

---

### Post by RedSingularity on 2010-04-16
Ok lets try it one step at a time.

First remove it.  Let me know when its removed.

---

### Post by RedSingularity on 2010-04-16
When it is removed post the output of 

sudo find / -name software-center

and

sudo find / -name .software-center

---

