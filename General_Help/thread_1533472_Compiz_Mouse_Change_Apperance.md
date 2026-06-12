---
title: "Compiz Mouse Change Apperance"
date: 2010-07-18
forum: General Help
---

### Post by abdusamed on 2010-07-18
I can't change the mouse appearance when compiz is on... does anyone know which Compiz prohibits mouse change? I'll turn it off.... :)

---

### Post by lidex on 2010-07-18
In 'General Options',  the 'General' tab, cursor theme is set to default? Also gconf editor: 'desktop>gnome>peripherals>mouse>cursor_theme' should be default.

---

### Post by abdusamed on 2010-07-18
Well in gconf editor the cursor theme is the one which I want to change too but the cursor is still the same. But i noticed that when the cursor is on the firefox, the cursor changes to one i want to but outside firefox window, it changes back to default which I don't want it to change to. In the "General" in Compiz, I don't see anything related to cursor. Only thing close is default icons. The icons change works but not cursor.

---

### Post by lidex on 2010-07-18
Try changing them both to 'default' then logout/in. See below.

---

### Post by abdusamed on 2010-07-21
this is all i have

---

### Post by lidex on 2010-07-21
Weird...do you have gconf backend enabled in preferences?

---

### Post by abdusamed on 2010-07-22
what do u mean? I before had few optoin but then I installed compiz extra. I then got more effects. I can't find anything more in the synaptic manager which will give me more effects. 

What do you mean by 'backend'?

---

### Post by lidex on 2010-07-22
First, in 'General' check to enable 'Gnome Compatability'. Still in 'General', the left pane , near the bottom, click preferences. Select the gconf backend and check to enable desktop integration.

---

### Post by abdusamed on 2010-07-23
> **lidex said:**
> First, in 'General' check to enable 'Gnome Compatability'. Still in 'General', the left pane , near the bottom, click preferences. Select the gconf backend and check to enable desktop integration.

It's already been set that way. My mouse just changing.. on the desktop it's default white and on certain windows, e.g. shutter but then it changes back to what I set on "Apperance" on different windows e.g. fixfox, link on xchat... pretty random if you ask me.. After recent update [Friday, July 23 2010] compiz performance has significantly improved but cursor problem remains the same

---

### Post by lidex on 2010-07-23
You have to be careful but you can try adding a link to ~/.themes to /root

---

### Post by abdusamed on 2010-07-24
> **lidex said:**
> You have to be careful but you can try adding a link to ~/.themes to /root


I don't want to do anything 'Risky' now cause from my past experience, I lost quite a much. I'll stick to the random mouse change until someone with a simple solution arrives.

---

### Post by trusktr on 2010-08-08
I have this problem too in Arch Linux. It's pretty annoying! The problem persists whether i use gtk decorator or emerald decorator in compiz.

I have no ideas yet... I'll be back if i find something.

---

### Post by xdaedalus on 2010-08-16
Hi lidex,

I'm having the *exact* same problem as abdusamed, and I can't quite figure it out. The problem started when I installed KDE and XFCE. Perhaps one of the settings manager things from those desktops is interfering with my gnome settings?

If you don't mind, can you tell me how to add a link to ~/.themes to /root? Why might that help? Thanks a ton for your help so far.

---

### Post by abdusamed on 2010-08-16
I disabled compiz, crashed way to many times for me. Couldn't bare it anymore. Composite effect aren't that bad.

---

### Post by bug67 on 2010-08-16
This is a known issue.  Been around for awhile.  One of the things that's keeping me from upgrading to Lucid:

[https://launchpad.net/+search?field.text=Compiz+mouse+bug](https://launchpad.net/+search?field.text=Compiz+mouse+bug)

I even filed a bug report on it myself before I knew about it.;)

---

### Post by xdaedalus on 2010-08-18
Thanks Bug67! Here's a fix I found on that bug report that solved the problem for me. This courtesy of dRewsus on that bug report:

                 I found a workaround for this.
 in /usr/share/icons/default there is a syslink to /etc/alternatives/x-cursor-theme
 #make a backup
sudo cp /etc/alternatives/x-cursor-theme /etc/alternatives/x-cursor-theme_backup
 #open the file in question
gksu gedit /etc/alternatives/x-cursor-theme
 change Inherits=DMZ-White
to reflect the icon theme you are using (ie. "Inherits=pUbuntu-24")
restart X

        


The only problem is that you'll need to change the file every time you want to change your pointer. (I'm okay with it cause I just wanted to get rid of the stupid-looking oxygen pointer :)

---

