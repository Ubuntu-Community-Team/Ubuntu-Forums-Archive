---
title: "Use OpenOffice 3.2 default theme instead of Gnome-theme"
date: 2010-02-12
forum: General Help
---

### Post by nabilalk on 2010-02-12
Hey all, I posted this question on the OpenOffice.org Linux section and figured I would also enlist the opinions of the Ubuntu community members. If anyone has an idea how I can force OpenOffice to use the OO default theme, and ignore the Gnome-theme, I would sincerely appreciate your input.  

Here is the [_thread_]("http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=27519") at OpenOffice.org

---

### Post by bruno9779 on 2010-02-12
compiling OO from source should do the trick.
But, I have looked it up and it is a pretty complex task.
[http://wiki.services.openoffice.org/wiki/Documentation/Building_Guide/Building_on_Linux](http://wiki.services.openoffice.org/wiki/Documentation/Building_Guide/Building_on_Linux)

---

### Post by nabilalk on 2010-02-12
> **bruno9779 said:**
> compiling OO from source should do the trick.
But, I have looked it up and it is a pretty complex task.
[http://wiki.services.openoffice.org/wiki/Documentation/Building_Guide/Building_on_Linux](http://wiki.services.openoffice.org/wiki/Documentation/Building_Guide/Building_on_Linux)

Yeah, looks complicated to me too. I have no experience with that. Any other ideas besides compiling OpenOffice from scratch?

---

### Post by Hagar Delest on 2010-02-13
I don't understand, the forum topic has been made with hints from this very Ubuntu forum. Hasn't it solved your problem???

---

### Post by lenoirrichelieu on 2010-02-13
[COLOR=black]Did you try that "export SAL_USE_VCLPLUGIN=gen" in .bash_profile mentioned in that thread?[/COLOR]

---

### Post by nabilalk on 2010-02-13
> **lenoirrichelieu said:**
> [COLOR=black]Did you try that "export SAL_USE_VCLPLUGIN=gen" in .bash_profile mentioned in that thread?[/COLOR]I don't understand what is meant by the ".bash_profile"

---

### Post by Hagar Delest on 2010-02-13
Then why don't you edit the openoffice.org3 file in /usr/bin? Less intrusive IMHO.

---

### Post by nabilalk on 2010-02-13
> **Hagar de l'Est said:**
> Then why don't you edit the openoffice.org3 file in /usr/bin? Less intrusive IMHO.

I have been working on just that and the .desktop entries:

Thanks. For a more detailed solution, see this thread over at the CrunchBang Linux forums. Crunchbang is a mod of Ubuntu

[http://crunchbanglinux.org/forums/post/55327/#p55327](http://crunchbanglinux.org/forums/post/55327/#p55327)

---

### Post by Hagar Delest on 2010-02-13
As said in the OOo forum, I don't see what's the difference with the fix proposed by slightlystoopid. Moreover, I don't see why you need to tweak the .desktop entries, there is absolutely no need for that.

---

### Post by nabilalk on 2010-02-13
> **Hagar de l'Est said:**
> As said in the OOo forum, I don't see what's the difference with the fix proposed by slightlystoopid. Moreover, I don't see why you need to tweak the .desktop entries, there is absolutely no need for that.

I guess b/c I don't understand what is meant by > Just to clarify to anyone reading this: the best solution, imo, is to add "export SAL_USE_VCLPLUGIN=gen" to your .bash_profile. I'm really not sure why I felt the need to modify library files before since they're naturally overwritten during upgrades.

Could you help me figure out where to add the suggested text?

With the method I used, if you don't tweak the desktop entries, then executing the desktop entries opens the OpenOffice apps with the original theme before the fix.

---

### Post by Hagar Delest on 2010-02-13
I use the shortcuts from the Start menu and they open with the non dark theme once I've changed the openoffice.org3 file.

---

### Post by nabilalk on 2010-02-13
> **Hagar de l'Est said:**
> I use the shortcuts from the Start menu and they open with the non dark theme once I've changed the openoffice.org3 file.

Which file are you referring to, the one in /usr/bin? Also where is the .bash_profile located and how can I modify it as the OP suggested at the OOo forum? Thx for your help.

---

### Post by Hagar Delest on 2010-02-13
Yes, the only change I've made is the openoffice.org3 file in the /usr/bin folder.

---

### Post by nabilalk on 2010-02-13
> **Hagar de l'Est said:**
> Yes, the only change I've made is the openoffice.org3 file in the /usr/bin folder.
Really? Would you mind posting the contents of your openoffice.org3 /usr/bin entry?

---

### Post by Hagar Delest on 2010-02-13
Exactly what I've posted in the other thread:
```
#!/bin/sh
exec env SAL_USE_VCLPLUGIN=gen /opt/openoffice.org3/program/soffice "$@"

```

---

### Post by nabilalk on 2010-02-13
> **Hagar de l'Est said:**
> Exactly what I've posted in the other thread:
```
#!/bin/sh
exec env SAL_USE_VCLPLUGIN=gen /opt/openoffice.org3/program/soffice "$@"

```

I used that in my /usr/bin however, the desired theme only showed up if I opened OO from the openoffice.org3 gallery. If I want to open oowriter directly via swriter cmd (/opt/openoffice.org3/program/swriter), the original theme and not the desired theme is loaded. How do you execute OO?

---

### Post by Ronin_301 on 2010-02-13
> **nabilalk said:**
> I used that in my /usr/bin however, the desired theme only showed up if I opened OO from the openoffice.org3 gallery. If I want to open oowriter directly via swriter cmd (/opt/openoffice.org3/program/swriter), the original theme and not the desired theme is loaded. How do you execute OO?

I open it by either going to Applications -> Office, or by opening an OO file in the file browser and the fix above worked.

---

### Post by nabilalk on 2010-02-13
> **Ronin_301 said:**
> I open it by either going to Applications -> Office, or by opening an OO file in the file browser and the fix above worked.
Yes, but the fix above only works (at least for me) if you launch OpenOffice in the gallery which allows you to select text, spreadsheet etc...If you want to skip that and say launch oowriter, then the fix above does not work. I don't want to have to go to the gallery each time I want to launch OpenOffice.

---

### Post by Hagar Delest on 2010-02-14
Then use the [FONT="Courier New"]openoffice.org3 -writer[/FONT] command line to launch it directly. 

Or go the /.bash_profile way, it should have a more general influence.

---

### Post by nabilalk on 2010-02-14
> **Hagar de l'Est said:**
> Then use the [FONT="Courier New"]openoffice.org3 -writer[/FONT] command line to launch it directly. 

Or go the /.bash_profile way, it should have a more general influence.

I see. Where is /.bash_profile located on the Ubuntu install?

---

### Post by Hagar Delest on 2010-02-14
I think it's not created by default, you'll have to do it.

---

### Post by nabilalk on 2010-02-14
> **Hagar de l'Est said:**
> I think it's not created by default, you'll have to do it.
Im inexperienced in this area. Where should I create the file and do you have any info to help get me started?

---

### Post by Hagar Delest on 2010-02-15
No idea. Never done that. Ask in the OOo forum topic where the other poster has replied.

---

### Post by nabilalk on 2010-02-15
> **Hagar de l'Est said:**
> No idea. Never done that. Ask in the OOo forum topic where the other poster has replied.I got the answer finally:

Create the following line at the bottom of your ".profile" file located in your home directory (/home/username)
```
export SAL_USE_VCLPLUGIN=gen
```
then logout or reboot. *Note: this option will be maintained during an OpenOffice upgrade because it involves your user profile and not /usr/bin or /usr/share/applications which are modified during an OpenOffice update.

---

