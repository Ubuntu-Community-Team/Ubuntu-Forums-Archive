---
title: "GUI Not responding"
date: 2010-01-22
forum: General Help
---

### Post by gadLinux on 2010-01-22
Hi all, 

I suffering a strange problem. I don't know if someone else has this problem also.


The problem is that I cannot click in buttons like "Next", "Acept", etc. I mean, I do click 
with the mouse, the button pushes and makes it sound but nothing happens. No next screen on a wizard or acept a panel, no nothing. 

The curious thing here is that the button is pressed and makes the theme sound but nothing happens.

Also it appears like the mouse button is still pressed because it behaves like the hover function. Passing the cursor over the button makes it pressed and getting it out it raises...

Other controls has problems also. For example checkboxes behave as it had the focus causing not be able to click in other places...

java applications that make use of the GTK toolkit suffers of this problem.

Native applications does not.

Eclipse is one clear case of this. 
Android ADT tool also suffers of this problem.

It's hard work like this. 

What I discarded right now:

Is not the java jre/jdk -> I tested several ones.
Is not compiz -> Metacity also has this problem.
Is not gtk alone -> Native applications works.


Any help on this?

I tested the problem in two different computers...

Thank you.

---

### Post by clhsharky on 2010-01-22
HI

What Distro are you using, and what app's are you trying to install?

Sharky

---

### Post by gadLinux on 2010-01-25
> **clhsharky said:**
> HI

What Distro are you using, and what app's are you trying to install?

Sharky

It's Ubuntu Karmic Koala. But this happens long time ago.

My problem happens with all applications that make use of java and the gtk toolkit.

I attached a video that autoexplains it. 

In this case I clicked in the details buttons that makes sound but does nothing until the end when I do "enter" to activate it.

The clicks are highlighted via control key. I push it to show that I do click...

---

### Post by NEUR0M4NCER on 2010-01-25
It's a common issue, and there's a relatively simple fix, I'll have a look around for you now...

[http://mou.me.uk/2009/10/31/fixing-eclipse-in-ubuntu-9-10-karmic-koala/](http://mou.me.uk/2009/10/31/fixing-eclipse-in-ubuntu-9-10-karmic-koala/)

Should do the trick. I was having the same issue in Azureus (Vuze), and the gtk-native-windows thing fixed everything for me.

---

### Post by gadLinux on 2010-01-25
> **NEUR0M4NCER said:**
> It's a common issue, and there's a relatively simple fix, I'll have a look around for you now...

[http://mou.me.uk/2009/10/31/fixing-eclipse-in-ubuntu-9-10-karmic-koala/](http://mou.me.uk/2009/10/31/fixing-eclipse-in-ubuntu-9-10-karmic-koala/)

Should do the trick. I was having the same issue in Azureus (Vuze), and the gtk-native-windows thing fixed everything for me.


Oh!!! I had this set into my old computers but something has changed between one computer and the new one. Maybe I recreated the account removing my old .bashrc settings that included the fix...

I thought that the problem with the java windows was already resolved via mainstream fix tough...

Thank you very much for your feedback!!!

Best regards...

---

### Post by StevieRG on 2010-02-25
That's just spot on Neur0m4cer! I changed from using 9.04 on my old HP to 9.10 on a new Revo last week and since then this problem with Eclipse has been driving me nuts - the fix works a treat for me, many thanks for your post.

---

