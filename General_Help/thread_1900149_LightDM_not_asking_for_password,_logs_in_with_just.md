---
title: "LightDM not asking for password, logs in with just one click"
date: 2011-12-25
forum: General Help
---

### Post by xyzzyman on 2011-12-25
I turned off auto-login, but now lightdm just shows a large 'login' button that when clicked logs me into my account with asking for a password... I changed my password and it didn't matter. Not finding anything about this on the forums. Anyone ever experienced something similiar?

I've looked at the conf files in /etc/lightdm/ and they are all set for not auto-logging in.

---

### Post by Bobhuber on 2011-12-25
Thats part of the users and groups program  included in gnome system tools package for gnome3.
user-admin and is one of the login options.

---

### Post by xyzzyman on 2011-12-26
> **Bobhuber said:**
> Thats part of the users and groups program  included in gnome system tools package for gnome3.
user-admin and is one of the login options.

I have no idea what you're talking about as I think you have no idea what I was talking about. lol. When auto-login is turned off, Ubuntu normally switches back to asking for a password. It wasn't recognizing it on my system, and didn't even ask for a password. Where it should have shown a password entry box was just a large login-button. 

Anyways I wound up reinstalling the OS so unfortunately I never did find the exactly failure. The lightdm configuration files look the same as before. It's possible I installed a custom DEB at some point that changed something. So dead thread.

---

### Post by Bobhuber on 2011-12-26
> **xyzzyman said:**
> I have no idea what you're talking about as I think you have no idea what I was talking about. lol. When auto-login is turned off, Ubuntu normally switches back to asking for a password. It wasn't recognizing it on my system, and didn't even ask for a password. Where it should have shown a password entry box was just a large login-button. 

Anyways I wound up reinstalling the OS so unfortunately I never did find the exactly failure. The lightdm configuration files look the same as before. It's possible I installed a custom DEB at some point that changed something. So dead thread.
FYI - Under Ubuntu running gnome3 you have the option with autologin turned off to have the Login Box with a large Login- Button that does not require a password. All you have to do is hit the enter key to login.
Thats what I was talking about and I believe what you were describing.
Have a nice day.

---

### Post by xyzzyman on 2011-12-26
So that may have been the problem. I had gnome-shell on here before but I'd removed it. I just had unity. Maybe something left over was over-riding me turning off auto-login in Unity's control panel (Which I thought was the same as gnome3's, go figure.) Now I wish I'd clonezilla's the install first so I could go back and troubleshoot it now so I could submit the bug.

---

### Post by danman33 on 2012-01-10
I have this same problem. I am using linux mint 12 with gnome 3 and I turned outo login on for my brothers friends and now that I turned it back off there is still a big login button instead of a password box. please help as I really dont want to reinstall.

---

### Post by Bobhuber on 2012-01-10
> **danman33 said:**
> I have this same problem. I am using linux mint 12 with gnome 3 and I turned outo login on for my brothers friends and now that I turned it back off there is still a big login button instead of a password box. please help as I really dont want to reinstall.
Under gnome3 open  users and groups from the applications menu (not from the system settings menu) and change it.

---

### Post by sisco311 on 2012-01-10
Or simply make sure that your user is not in the nopasswdlogin group:
```
sudo gpasswd -d **username** nopasswdlogin
```where **username** is your login name.

---

### Post by danman33 on 2012-01-10
Thank you so much, that did the trick!

---

### Post by vikxmc on 2012-10-18
> **sisco311 said:**
> Or simply make sure that your user is not in the nopasswdlogin group:
```
sudo gpasswd -d **username** nopasswdlogin
```where **username** is your login name.

Thanks a lot...:)

---

### Post by ab4rl1 on 2013-04-15
I had the exact same problem tonight under 12.04. The command line solution worked for me. I filed a bug report if anyone wants to confirm it.

[https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/1169054](https://bugs.launchpad.net/ubuntu/+source/accountsservice/+bug/1169054)

---

### Post by wildmanne39 on 2013-04-15
Thread closed. Please do not post in old threads.

---

