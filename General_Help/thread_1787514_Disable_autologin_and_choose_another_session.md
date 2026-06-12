---
title: "Disable autologin and choose another session"
date: 2011-06-21
forum: General Help
---

### Post by luisp on 2011-06-21
Hi,

I'm running Ubuntu 10.10. I just activated automatic login and selected XBMC session because I use it a lot. I assumed there was a way to disable this feature and get Ubuntu session back again as soon as I wanted. Unfortunately, being a Linux newbie isn't easy and I can't seem to find a way to reverse this situation. I want my Ubuntu Desktop again, please! Am I stuck with XBMC forever? All the help is appreciated. TIA

Regards
Luis

---

### Post by Jonher937 on 2011-06-21
Logout and change your session

---

### Post by nothingspecial on 2011-06-21
Disregard.

---

### Post by yetiman64 on 2011-06-21
Go to System > Administration > Login Screen to disable the automatic log in. Then log out and on the login screen select a user and go to the bottom window bar to select the session you want.

Edit: note I'm on 10.04, if it is not there, try out Users and groups as nothingspecial suggested.

---

### Post by luisp on 2011-06-21
> **yetiman64 said:**
> Go to System > Administration > Login Screen to disable the automatic log in. Then log out and on the login screen select a user and go to the bottom window bar to select the session you want.

Edit: note I'm on 10.04, if it is not there, try out Users and groups as nothingspecial suggested.

Thank you for your help yetiman64. The problem is even if I cancel autologin and choose a user (myself) I always end up within XBMC GUI. I don't have access to Ubuntu Desktop or the Login Screen window for that matter. When I get the autologin window I can cancel the process, choose a different user but unfortunately cannot change login settings. TIA

---

### Post by haqking on 2011-06-21
> **luisp said:**
> Thank you for your help yetiman64. The problem is even if I cancel autologin and choose a user (myself) I always end up within XBMC GUI. I don't have access to Ubuntu Desktop or the Login Screen window for that matter. When I get the autologin window I can cancel the process, choose a different user but unfortunately cannot change login settings. TIA

Dont you get the option to change at the bottom of the login screen ?

when you type you username in options should appear at the bottom of the screen ?

---

### Post by yetiman64 on 2011-06-21
> **luisp said:**
> Thank you for your help yetiman64. The problem is even if I cancel autologin and choose a user (myself) I always end up within XBMC GUI. I don't have access to Ubuntu Desktop or the Login Screen window for that matter. When I get the autologin window I can cancel the process, choose a different user but unfortunately cannot change login settings. TIA

I meant click on your user, **but don't login yet**, look at the bottom of the window and several selectors should become available on the bottom bar. 

One is for language selection, one for keyboard type and the last on the right of the three should be the one you want for session selection, click the arrow on the box and a popup will appear then highlight and select the session you want, and **then do the login **as you normally would. 

If you click login after selecting your user straight away you are missing the option to change the session (XBMC vs Ubuntu or Ubuntu Classic etc) Have another go and good luck. yetiman64.

---

### Post by luisp on 2011-06-21
> **yetiman64 said:**
> I meant click on your user, **but don't login yet**, look at the bottom of the window and several selectors should become available on the bottom bar.

Thanks again but my login window doesn't have those options. I've only two options: user(myself) and other...at the bottom of this window there are two buttons: "Cancel" and "Login". Surprisingly I can't change any login settings.

I'm running Ubuntu 10.10 on Xtreamer Ultra HTPC. I'm afraid this modified version is full of bugs, which is exactly what this seems to be. I'm stuck with an unwanted autologin. At the end I guess I can always re-install all the system :confused:

---

### Post by bodhi.zazen on 2011-06-21
> **luisp said:**
> Thanks again but my login window doesn't have those options. I've only two options: user(myself) and other...at the bottom of this window there are two buttons: "Cancel" and "Login". Surprisingly I can't change any login settings.

I'm running Ubuntu 10.10 on Xtreamer Ultra HTPC. I'm afraid this modified version is full of bugs, which is exactly what this seems to be. I'm stuck with an unwanted autologin. At the end I guess I can always re-install all the system :confused:

At the log in screen, you select your user, you will then be given additional options at the bottom of the screen, including which session you wish to use.

---

### Post by luisp on 2011-06-21
> **bodhi.zazen said:**
> At the log in screen, you select your user, you will then be given additional options at the bottom of the screen, including which session you wish to use.

I understand your advice, unfortunately, this Ubuntu version named Everest by Xtreamer doesn't show any additional options at the bottom of the screen after I select a user. At first I thought it had something to do with screen resolution, maybe those options were hidden, but no, after changing resolution I found nothing out there. Thanks anyway.

[Solved] A mysterious right click on the mouse was needed to show extra options. Go figure!

---

### Post by bodhi.zazen on 2011-06-21
> **luisp said:**
> I understand your advice, unfortunately, this Ubuntu version named Everest by Xtreamer doesn't show any additional options at the bottom of the screen after I select a user. At first I thought it had something to do with screen resolution, maybe those options were hidden, but no, after changing resolution I found nothing out there. Thanks anyway.

Well, do you have alternate window managers installed ?

I do not know of this "Ubuntu version named Everest by Xtreamer" , but perhaps you could ask the maintainer of such a distro.

---

### Post by el_koraco on 2011-06-21
Please enter the command 

```
less /etc/gdm/custom.conf

```
in the terminal. You'll get a selection of text. Copy it and post it here.

---

### Post by luisp on 2011-06-22
Hi everyone,

I just got help from Xtreamer community.

Problem solved! Simple answer. You have to be a magician LOL

A mysterious right click on the mouse at the bottom of an empty screen was needed to show the extra options you talked about. Go figure!

Thank you everyone.
Regards

---

