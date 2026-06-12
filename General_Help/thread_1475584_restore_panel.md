---
title: "restore panel"
date: 2010-05-07
forum: General Help
---

### Post by luftadler on 2010-05-07
Hi all,

I have deleted notification area from the top panel and now I need few items from there, like volume mixer. It is a way to restore top panel at the default status in Lucid Lynx?
I've tried wit add to panel but i didn't  succeed to get what i want. 


Regards,
Cristian

---

### Post by WorMzy on 2010-05-07
I think the item you need to readd is either Indicator Applet Session, or Indicator Applet, or Notification Area. Try those first.

If none of those are what you're looking for, you can force your panels to revert back to the state they were in when you first installed Ubuntu. To do this, open a terminal and write the following:
```
mkdir ~/.oldpanel
```then
```
mv ~/.gconf/apps/panel ~/.oldpanel
```then
```
*gconftool-2 --shutdown*
```finally
```
pkill gnome-panel
```

NOTE: This will completely reset your panels to the default configuration, they will look the same as if you'd done a fresh install.

---

### Post by darolu on 2010-05-07
This will restore your panel to the default values. Open a terminal and run:
```
$ gconftool-2 --shutdown
$ rm -rf ~/.gconf/apps/panel
$ pkill gnome-panel
```
And that should get your default items back.

---

### Post by luftadler on 2010-05-07
It works with Indicator Applet Session and Indicator Applet. 


Thanks folks,
Cristian

---

### Post by SKhan on 2010-05-08
> **darolu said:**
> This will restore your panel to the default values. Open a terminal and run:
```
$ gconftool-2 --shutdown
$ rm -rf ~/.gconf/apps/panel
$ pkill gnome-panel
```And that should get your default items back.
thanks man. i had same problem. today's my first day on ubuntu & i accidently deleted top panel. you solved it.

---

### Post by luftadler on 2010-05-08
Hi,

I've solved the problem with Add to panel and I added Applet Session and Indicator Applet.
if you don't now how, just right click on the panel and select add to panel. If you deleted the entire panel i think the previous post it will help you.

And welcome to Ubuntu.

Regards,
Cristian

---

### Post by pril on 2010-06-20
I'm obviously a real newby, i have now idea how to even do that lol. I have worked out how to add pannel there, and put icons on it, but the original one was better and already had everything there..

---

### Post by pril on 2010-06-20
thank you so so much it worked!

---

### Post by bonde on 2010-06-21
> **SKhan said:**
> thanks man. i had same problem. today's my first day on ubuntu & i accidently deleted top panel. you solved it.I managed the same today, to delete the whole panel. Had to figure out how to open a terminal, but when I did, this worked like a charm. Cheers.

---

### Post by stijnblommerde on 2010-08-11
had the same problem. i removed indicator applet, indicator applet session and clock. 

- 'add to panel' did not work inside the right part of the top panel.
- then i could not find the needed applets in the 'add to panel window'
- read the help information about panels; could not find the answer

anyway. i found them using this post. thanks a lot. 

greetings from a newbe (installed Ubuntu a few days ago)

---

### Post by ieBrazil on 2010-09-28
Tnx man! You're the one :-)

> **WorMzy said:**
> I think the item you need to readd is either Indicator Applet Session, or Indicator Applet, or Notification Area. Try those first.

If none of those are what you're looking for, you can force your panels to revert back to the state they were in when you first installed Ubuntu. To do this, open a terminal and write the following:
```
mkdir ~/.oldpanel
```then
```
mv ~/.gconf/apps/panel ~/.oldpanel
```then
```
*gconftool-2 --shutdown*
```finally
```
pkill gnome-panel
```

NOTE: This will completely reset your panels to the default configuration, they will look the same as if you'd done a fresh install.

---

### Post by pschalkx on 2010-09-29
@WorMzy:

Thanks! I had messed up my panels. Your tip saved me a lot of trouble.

Philip

---

### Post by jean noel on 2010-11-19
> **darolu said:**
> This will restore your panel to the default values. Open a terminal and run:
```
$ gconftool-2 --shutdown
$ rm -rf ~/.gconf/apps/panel
$ pkill gnome-panel
```
And that should get your default items back.

Absolutely brilliant stuff. Many thanks
Jean Noel

---

### Post by Mawsley on 2011-02-24
> **WorMzy said:**
> I think the item you need to readd is either Indicator Applet Session, or Indicator Applet, or Notification Area. Try those first.

If none of those are what you're looking for, you can force your panels to revert back to the state they were in when you first installed Ubuntu. To do this, open a terminal and write the following:
```
mkdir ~/.oldpanel
```then
```
mv ~/.gconf/apps/panel ~/.oldpanel
```then
```
*gconftool-2 --shutdown*
```finally
```
pkill gnome-panel
```NOTE: This will completely reset your panels to the default configuration, they will look the same as if you'd done a fresh install.

Thank you.

As someone who doesn't consider himself stupid - I quickly found out what the panel was and not just the bit where my name used to be!

This has solved everything. Cheers.

---

### Post by TJ1916 on 2011-03-28
Joined the ranks of those that lost panels ... and wanted them back.

Many thanks; docks aren't for me.

---

### Post by atulsingh7890 on 2011-04-02
> **darolu said:**
> This will restore your panel to the default values. Open a terminal and run:
```
$ gconftool-2 --shutdown
$ rm -rf ~/.gconf/apps/panel
$ pkill gnome-panel
```
And that should get your default items back.
i have done these commands..
but nothing has happende..
$ gconftool-2 --shutdown
$ rm -rf ~/.gconf/apps/panel
$ pkill gnome-panel
i have previosly installed avant-window-manager and deleted the panel from
gconf-editor  -> desktop -> gnome -> sessions -> required components 


can u plz help me out to restore my top panel...

---

### Post by WorMzy on 2011-04-02
If you've removed gnome-panel from the required components, then it's probably not even running. Run it by pressing Alt+F2, then typing
```
gnome-panel
```
then clicking "Run".

Unless you re-add gnome-panel as a required component, you'll either need to run this command manually every time you log into Ubuntu, or add it to your startup applications (System -> Preferences -> Startup Applications)

---

