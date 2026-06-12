---
title: "how to gksudo a program at startup?"
date: 2011-01-24
forum: General Help
---

### Post by graham73may on 2011-01-24
It is my first week using Linux, so sorry if this is a really stupid question.

I am having problems with Gnome Power Manager, the way I have got it to work currently is I have changed the startup command to gksudo gnome-power-manager in the startup applications menu.

The only problem with this is it asks me for my admin password everytime I login. What is the best way to run this program as the root user at startup? 

note: I have to run it as root as it is the only way to get the battery tab to appear in the power manager

---

### Post by davidmohammed on 2011-01-24
suggest run it as root as you have found.  Then choose the "make default" button - close and reopen as normal.  This should make your battery tab visible by default.

---

### Post by earthmeLon on 2011-01-24
> **graham73may said:**
> The only problem with this is it asks me for my admin password everytime I login. What is the best way to run this program as the root user at startup? 

I am not familiar with the program you are trying to fix specifically but..

Many programs and daemons (such as http and ssh servers) are called to run during 'init'.  They reside in '/etc/init.d/'.  Within that directory are many scripts that the system loads at different run levels.

You can check which run levels each of the scripts are running at, as well as if they are even running by using **chkconfig**.  Most of the time, these scripts are run as root and is the normal way of doing things.

Sorry if this information does not help you. >_<

---

### Post by graham73may on 2011-01-24
> **davidmohammed said:**
> suggest run it as root as you have found.  Then choose the "make default" button - close and reopen as normal.  This should make your battery tab visible by default.

How do I find where it is? I have no idea where the linux "my program files" folder would be!

---

### Post by davidmohammed on 2011-01-24
> **graham73may said:**
> How do I find where it is? I have no idea where the linux "my program files" folder would be!

eh?  I never mentioned "my program files"...!

---

### Post by graham73may on 2011-01-24
> **davidmohammed said:**
> eh?  I never mentioned "my program files"...!

I know, i'm asking what the linux equivalent is.

basically, where do I click on the app? the right click menu in system - prefences doesn't have any useful options



> **earthmeLon said:**
> I am not familiar with the program you are trying to fix specifically but..

Many programs and daemons (such as http and ssh servers) are called to run during 'init'.  They reside in '/etc/init.d/'.  Within that directory are many scripts that the system loads at different run levels.

You can check which run levels each of the scripts are running at, as well as if they are even running by using **chkconfig**.  Most of the time, these scripts are run as root and is the normal way of doing things.

Sorry if this information does not help you. >_<

I'm not really sure how to use this tool to help me :S


EDIT:

I have sent the link from system to the desktop, from there, the properties show that it is in the group root. BUT, if I click it, It doesn't work properly, If I left it load at startup, it doesn't work properly. 

but if I "sudo gnome-power-manager" it works fine... hm :-/

---

