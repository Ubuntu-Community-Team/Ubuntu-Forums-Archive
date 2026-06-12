---
title: "What window manager do I need?"
date: 2010-06-17
forum: General Help
---

### Post by mooserider2 on 2010-06-17
I am trying to build a linux distro based on xubuntu that I will install in my car. I need a window manager thats fast and dosen't have to have the minimize, maximize, and close buttons at the top. I also have somewhat of an idea on how to change from xfwm4 but not 100% if you could help me out with that, that would be grand. Thank you

---

### Post by wojox on 2010-06-17
Have you had a look here? [Window Managers for X]("http://xwinman.org/")

---

### Post by Simian Man on 2010-06-17
Xfwm doesn't have to have any buttons at all.  Open up the window manager preferences and you can configure which buttons show up where.

---

### Post by sisco311 on 2010-06-17
> **mooserider2 said:**
> I am trying to build a linux distro based on xubuntu that I will install in my car. I need a window manager thats fast and dosen't have to have the minimize, maximize, and close buttons at the top. I also have somewhat of an idea on how to change from xfwm4 but not 100% if you could help me out with that, that would be grand. Thank you

tiling window managers are awesome :)

---

### Post by mooserider2 on 2010-06-17
Ok i think i decided on matchbox, and i looked at the xfce button hiding and that will work but i want to see if i can get matchbox to work the way i want it (I cant get rid of the title bar and matchbox is smaller.) Any ways I tested matchbox with:

killall xfwm4; matchbox-window-manager &

Thats good for a test but i need to make it a default anyone got ideas?

---

### Post by sisco311 on 2010-06-17
> **mooserider2 said:**
> Ok i think i decided on matchbox, and i looked at the xfce button hiding and that will work but i want to see if i can get matchbox to work the way i want it (I cant get rid of the title bar and matchbox is smaller.) Any ways I tested matchbox with:

killall xfwm4; matchbox-window-manager &

Thats good for a test but i need to make it a default anyone got ideas?

I don't use Xubuntu anymore, but check out the comments from this guide:
[http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/](http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/)

Of course you will have to replace compiz by matchbox


HTH

---

### Post by mooserider2 on 2010-06-17
Is there a "how to" for matchbox im having troubles. If anyone cares im trying to get all my windows to open maximum size with no titlebar or buttons. I have a grey box at the top of my screen that says the title of the program and i dislike that.. help! 

sorry if this seems like im bumping but i didn't think the contents fit the previous post

---

### Post by mooserider2 on 2010-06-17
> **sisco311 said:**
> I don't use Xubuntu anymore, but check out the comments from this guide:
[http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/](http://xubuntublog.wordpress.com/2007/12/09/xubuntu-compiz-pretty-pretty-xubuntu/)

Of course you will have to replace compiz by matchbox


HTH

nope didn't work i tried the --replace method and it didn't work

---

### Post by sisco311 on 2010-06-18
> **mooserider2 said:**
> nope didn't work i tried the --replace method and it didn't work

At the login screen you should be able to choose between Xubuntu and xfce4-session.

To change the default window manager for the Xubuntu session you have to edit the  /etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml file and replace xfwm4 by matchbox-window-manager:
```
 
<channel name="xfce4-session" version="1.0">
  <property name="general" type="empty">
    <property name="FailsafeSessionName" type="string" value="Failsafe"/>
    <property name="SaveOnExit" type="bool" value="false"/>
  </property>
  <property name="sessions" type="empty">
    <property name="Failsafe" type="empty">
      <property name="IsFailsafe" type="bool" value="true"/>
      <property name="Count" type="int" value="5"/>
      <property name="Client0_Command" type="array">
        <value type="string" value="**matchbox-window-manager**"/>
      </property>
      <property name="Client0_PerScreen" type="bool" value="false"/>
      <property name="Client1_Command" type="array">
        <value type="string" value="xfce4-panel"/>
      </property>
...

```

The xfce4-sessions default settings are stored in /etc/xdg/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml

---

### Post by mooserider2 on 2010-06-20
ok that worked well but i dosent load the xfce panel like it dose when i do killall. can i fix this?

---

### Post by mooserider2 on 2010-06-20
ok i solved that i just moved the panel before the window manager
```
 
<channel name="xfce4-session" version="1.0">
  <property name="general" type="empty">
    <property name="FailsafeSessionName" type="string" value="Failsafe"/>
    <property name="SaveOnExit" type="bool" value="false"/>
 [B]</property>
      <property name="Client0_PerScreen" type="bool"  value="false"/>
      <property name="Client1_Command" type="array">
        <value type="string" value="xfce4-panel"/>[/B]
  </property>
  <property name="sessions" type="empty">
    <property name="Failsafe" type="empty">
      <property name="IsFailsafe" type="bool" value="true"/>
      <property name="Count" type="int" value="5"/>
      <property name="Client0_Command" type="array">
        <value type="string" value="**matchbox-window-manager**"/>
     
      </property>
...

```

I still have the grey box that matchbox has below the xfce-panel could i remove this by changing the matchbox theme? if so how would i do that? if you need  a screen shot tell me ill add one

---

### Post by mooserider2 on 2010-06-20
Ok I'm sorry this is my third post in a row but i figured everything out the grey box was set to the default theme so i made my own theme that didn't have any window decoration and replaced the default theme with that. Thank you guys for all your help if you want to see my carputer when its done pm me or send a friend request ill make sure i get some pics maybe put up the iso if you want to test it out for your selves.

---

