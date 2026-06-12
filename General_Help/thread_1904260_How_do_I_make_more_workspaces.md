---
title: "How do I make more workspaces?"
date: 2012-01-04
forum: General Help
---

### Post by pretty_whistle on 2012-01-04
I have Ubuntu 11.04 with Unity.

The workspaces are set to a default of 4 but I want 6.  How do I add 2?

I tried right clicking it but nothing happens.

I want to add more but not use compiz to do it.

Is there a way?
.
.

---

### Post by drmrgd on 2012-01-04
If I remember correctly, I think you can change this using gconf-editor, available in the repos.  There should be a section in there devoted to workspaces.  Memory's a bit hazy on the specifics, though.  Hope it helps!

---

### Post by pretty_whistle on 2012-01-04
> **drmrgd said:**
> If I remember correctly, I think you can change this using gconf-editor, available in the repos.  There should be a section in there devoted to workspaces.  Memory's a bit hazy on the specifics, though.  Hope it helps!
I'll try that.

---

### Post by pretty_whistle on 2012-01-04
Well, I tried that but couldn't find it in there.

---

### Post by philinux on 2012-01-04
> **pretty_whistle said:**
> I have Ubuntu 11.04 with Unity.

The workspaces are set to a default of 4 but I want 6.  How do I add 2?

I tried right clicking it but nothing happens.

I want to add more but not use compiz to do it.

Is there a way?
.
.

Compizconfig-settings-manager General>Options>Desktop Size Tab. Not sure how without ccsm. But I'm looking now.

---

### Post by philinux on 2012-01-04
> **pretty_whistle said:**
> Well, I tried that but couldn't find it in there.

Using gconf. Have a play around in there.
[http://askubuntu.com/questions/42787/how-do-i-enable-multi-row-layout-for-the-workspace-switcher-applet-in-metacity](http://askubuntu.com/questions/42787/how-do-i-enable-multi-row-layout-for-the-workspace-switcher-applet-in-metacity)

---

### Post by pretty_whistle on 2012-01-04
> **philinux said:**
> Using gconf. Have a play around in there.
[http://askubuntu.com/questions/42787/how-do-i-enable-multi-row-layout-for-the-workspace-switcher-applet-in-metacity](http://askubuntu.com/questions/42787/how-do-i-enable-multi-row-layout-for-the-workspace-switcher-applet-in-metacity)
I read the link but the person said he was using gnome classic desktop.  I'm using Unity.

---

### Post by pretty_whistle on 2012-01-04
> **philinux said:**
> Using gconf. Have a play around in there.
[http://askubuntu.com/questions/42787/how-do-i-enable-multi-row-layout-for-the-workspace-switcher-applet-in-metacity](http://askubuntu.com/questions/42787/how-do-i-enable-multi-row-layout-for-the-workspace-switcher-applet-in-metacity)
You know more than you speak, I found it!!!!

Ah...more workspaces...ah...  Cool.

Thanx.  Because you said to "Have a play around in there" I decided to have another look and there it is!

---

### Post by pretty_whistle on 2012-01-04
Here it is if someone else should need it:


> in gconf go to:

apps>compiz-1>general>screen0>options

It's the last 2:
hsize
vsize
hsize is horizintal size
vsize is vertical size

---

