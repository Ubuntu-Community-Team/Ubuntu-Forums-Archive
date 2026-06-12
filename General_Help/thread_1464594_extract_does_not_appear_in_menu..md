---
title: "extract does not appear in menu."
date: 2010-04-28
forum: General Help
---

### Post by shini-kire on 2010-04-28
hello.
my problem is the following not aparese the option  to extract or compress.

[IMG]http://farm3.static.flickr.com/2719/4560306387_dd883a2b90_o.png[/IMG] 

to extract it I have to open the file manager and extract and not is grace.

please!! help me! 

my respects!

Ubuntu 10.04 (lucid)

---

### Post by dino99 on 2010-04-28
extract is a built-in feature into ubuntu, no need extra software like in crozoff  :P

only double-click on an archive to extract it. more info if you search into synaptic about "zip" or "rar" or "archive"

---

### Post by shini-kire on 2010-04-28
> **dino99 said:**
> extract is a built-in feature into ubuntu, no need extra software like in crozoff  :P

only double-click on an archive to extract it. more info if you search into synaptic about "zip" or "rar" or "archive"



friend if I have zip, rar, ace, etc .... Just want to know that does not appear to extract or compress, when I click lefty do not see this.

---

### Post by dino99 on 2010-04-28
forget crozoff and its stuff

---

### Post by shini-kire on 2010-04-28
> **dino99 said:**
> forget crozoff and its stuff

What is crozoff?

sorry but I used ubuntu 6 in next.... but in 9.10 not have... :confused::confused:

---

### Post by dino99 on 2010-04-28
> **shini-kire said:**
> What is crozoff?

sorry but I used ubuntu 6 in next.... but in 9.10 not have... :confused::confused:

well you dont know bill and its windoz :confused:

---

### Post by shini-kire on 2010-04-28
> **dino99 said:**
> well you dont know bill and its windoz :confused:

sorry, not use winbug of mocosoft

---

### Post by dannyboy79 on 2010-04-28
not sure what the other guy is saying but i understand your problem. basically nautilus should have a build in "Extract Here" within the right click context menu when in nautilus. I am not sure how to get it back as I have been googling for the last 5 minutes. It has something to do with nautilus using file-roller to extract the archive. you could always temporarily create a nautilus-script and store it within /home/user/.gnome/nautilus-scripts/
and then the extract script will appear in the context menu.

here's a whole mess of temporary solutions:
[http://g-scripts.sourceforge.net/cat-archiving.php](http://g-scripts.sourceforge.net/cat-archiving.php)

at least until you find out why file-roller isn't giving you the "Extract Here" within nautilus context menu.

---

### Post by shini-kire on 2010-04-28
> **dannyboy79 said:**
> not sure what the other guy is saying but i understand your problem. basically nautilus should have a build in "Extract Here" within the right click context menu when in nautilus. I am not sure how to get it back as I have been googling for the last 5 minutes. It has something to do with nautilus using file-roller to extract the archive. you could always temporarily create a nautilus-script and store it within /home/user/.gnome/nautilus-scripts/
and then the extract script will appear in the context menu.

here's a whole mess of temporary solutions:
[http://g-scripts.sourceforge.net/cat-archiving.php](http://g-scripts.sourceforge.net/cat-archiving.php)

at least until you find out why file-roller isn't giving you the "Extract Here" within nautilus context menu.

you have the same problem? or am I not more have this problem?
XDD

---

### Post by dannyboy79 on 2010-04-28
i don't have the problem and not sure how to help you. i provided a temporary solution until someone else comes along to help you.

---

### Post by dannyboy79 on 2010-04-28
you do have file-roller installed right? it should be by default but you can check that out

---

### Post by shini-kire on 2010-04-28
> **dannyboy79 said:**
> you do have file-roller installed right? it should be by default but you can check that out
I have installed file-roller...

but ... thks!! for you help with inprovice =D

---

### Post by fsando on 2010-06-26
To bump this thread
I'm seeing the same missing 'Extract here' issue but only for *.gz files not any other compressed formats. When I double click it opens nicely in file-roller and can be dragged and dropped into the folder but it sure would be nice if the menu returned like for all the other formats.

It must be specifically related to the file extension because if I change the extension to one of the supported ones the "Extract here..." options returns (but gives an error if used).

Could it be a mime database bug?

Should I maybe report it as a bug?

I tried to delete the mime-database and restore it - didn't help.

I'm using the simplified nautilus version.

EDIT:
... and then I found a reasonable solution:

1. Install nautilus-actions
2. Open "nautilus-actions-config-tool"
3. Add a new action
4. Choose a suitable icon and label
5. In the command tab use 
Path: file-roller -h
Parameters: %d/%f
6. In the Conditions tab: set to "*.gz"

---

