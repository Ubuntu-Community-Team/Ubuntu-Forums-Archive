---
title: "bleachbit is not in the &quot;System tools&quot; !!"
date: 2010-10-10
forum: General Help
---

### Post by shaon3343 on 2010-10-10
**[SIZE=3]Hi , I've installed Bleachbit a few months ago. it was working fine. and It was on the "system tools" . today I updated/ installed  Bleachbit to 8.01 and  it vanished from the system tools area!! but I can access it from the terminal . So please help me , how can I again place it in system tools ? thanks in advance ! [/SIZE]**

---

### Post by dcstar on 2010-10-10
> **shaon3343 said:**
> Hi , I've installed Bleachbit a few months ago. it was working fine. and It was on the "system tools" . today I updated/ installed  Bleachbit to 8.01 and  it vanished from the system tools area!! but I can access it from the terminal . So please help me , how can I again place it in system tools ? thanks in advance !

[LIST=1]
[*]Have logged out/in or rebooted?
[*]Do NOT use highlighting to attract attention in your posts - you are no more important or deserving of attention than anyone else here.
[/LIST]

---

### Post by shaon3343 on 2010-10-10
**Yes I've rebooted after that. But still no working ! its not in the system tools area ! please help **

---

### Post by fooman on 2010-10-10
right-clcik on "applications" in the top panel and choose "edit menus" from the list.

when the main menu window opens,  click on "system tools" in the left column,  if bleachbit is in the middle column, put a check next to it.  if it is not there...  then on the right, choose "new item"

in the "create launcher" window...type bleachbit in the name space.  then click "browse".  in the next window,  go to > file system > user > bin

find bleachbit in the list,  click once on it,  then click "open".  back at the "create launcher" window,  click ok.  close the main menu window and you should be set.

hope that helps.

---

### Post by inameiname on 2010-10-10
I just did this too today, and noticed the same thing. 

I found it not under 'System Tools', but 'System -> Administration'

---

### Post by shaon3343 on 2010-10-10
> **fooman said:**
> right-clcik on "applications" in the top panel and choose "edit menus" from the list.

when the main menu window opens,  click on "system tools" in the left column,  if bleachbit is in the middle column, put a check next to it.  if it is not there...  then on the right, choose "new item"

in the "create launcher" window...type bleachbit in the name space.  then click "browse".  in the next window,  go to > file system > user > bin

find bleachbit in the list,  click once on it,  then click "open".  back at the "create launcher" window,  click ok.  close the main menu window and you should be set.

hope that helps.

thanks!! From now I can add new Item in those application list!! :guitar::guitar:

---

### Post by shaon3343 on 2010-10-10
> **inameiname said:**
> I just did this too today, and noticed the same thing. 

I found it not under 'System Tools', but 'System -> Administration'

Yes ! I just  checked it ,  same here! thanks for help !! :P:P:P

---

### Post by inameiname on 2010-10-10
Not sure what is the reason, or rationale, for the change.

---

### Post by Andrew.Z on 2010-10-15
> **inameiname said:**
> Not sure what is the reason, or rationale, for the change.

The change was made at Ubuntu or GNOME.  I left everything as is, but the whole menu disappeared in Ubuntu version 10.10, so I had to put it in a new place.  The [BleachBit 0.8.1 release notes](http://bleachbit.sourceforge.net/news/bleachbit-081-evercookie) references a Launchpad bug ticket you can read for more info.

---

### Post by inameiname on 2010-10-15
Ah, I see. Thanks, Andrew.



On another note, has anybody got bleachbit-bonus (0.7.1) to work on Maverick, and bleachbit (0.8.1)?

---

### Post by Andrew.Z on 2010-11-15
> **inameiname said:**
> On another note, has anybody got bleachbit-bonus (0.7.1) to work on Maverick, and bleachbit (0.8.1)?

[BleachBit 0.8.2 bonus pack installs on Ubuntu Maverick 10.10](http://bleachbit.sourceforge.net/news/bleachbit-082-released).  You are best off getting the .debs there for the 0.8.2 app as well as the 0.8.2 bonus pack (two 2 .deb files).

---

### Post by samacaster on 2010-11-16
The new Bleachbit upgrade now allows you to run as a regular user or as an admin. You should see two bleachbit entries in the administration menu. If you don't it didn't install properly.

---

