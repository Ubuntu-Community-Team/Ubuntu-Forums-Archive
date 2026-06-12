---
title: "Unable to log in Ubuntu 9.10"
date: 2009-10-30
forum: General Help
---

### Post by Richiegs on 2009-10-30
After I installed Ubuntu 9.10 into my PC with Windows XP, I was unable to log into Ubuntu. It failed to recognize my password and showed the same log-in page again. I appreciate anyone who can help me.

Richie

---

### Post by aredumascire on 2009-10-30
I have this same problem except that I can't log in by using LiveCD.

---

### Post by theozzlives on 2009-10-30
> **Richiegs said:**
> After I installed Ubuntu 9.10 into my PC with Windows XP, I was unable to log into Ubuntu. It failed to recognize my password and showed the same log-in page again. I appreciate anyone who can help me.

Richie

You sure you're typing the right password? If so, hold down the shift key during boot, choose recovery, then root prompt. Type:
```
passwd <username>
```
it'll prompt you for a new password, twice. You won't see anything as you enter it, but you're still entering it. Then type reboot. It'll reboot as normal.

---

### Post by P4man on 2009-10-30
perhaps you have the wrong keyboard layout or you had it wrong in the live cd. theozzlives's solution should help then though.

---

### Post by losi on 2009-10-30
....-Hi,
when you install you have to check well the user name and care about the password also. The login name you got sometimes automatic by the name you add. Even it give up automatically at the first enter can be that you not have control on it. 
(Check also caps lock may be)
good luck
losi

---

### Post by Richiegs on 2009-10-30
> **theozzlives said:**
> You sure you're typing the right password? If so, hold down the shift key during boot, choose recovery, then root prompt. Type:
```
passwd <username>
```
it'll prompt you for a new password, twice. You won't see anything as you enter it, but you're still entering it. Then type reboot. It'll reboot as normal.

I am sure I typed the correct password with correct U.S. keyboard layout because I installed Ubuntu 9.10 on my both desktop and laptop with the same PASSWORD. The laptop with Vista works fine, but the desktop with Windows XP I just can't log in. I will try to log in later with your advice and let you guys know . Thanks a lot.

---

### Post by Richiegs on 2009-10-30
> **theozzlives said:**
> You sure you're typing the right password? If so, hold down the shift key during boot, choose recovery, then root prompt. Type:
```
passwd <username>
```
it'll prompt you for a new password, twice. You won't see anything as you enter it, but you're still entering it. Then type reboot. It'll reboot as normal.

I changed to a new password and restart the PC, but I was still unable to log in. It is frustrating because it works in the recovery mode, not the regular mode.

---

### Post by M567 on 2009-10-31
I have the same problem but if I log into KDE from the menu at the bottom rather than use Gnome I can login

---

### Post by Richiegs on 2009-11-01
[quote=M567;8206416]I have the same problem but if I log into KDE from the menu at the bottom rather than use Gnome I can login[/quote 
 
I reinstalled Ubuntu 9.10 several times but I still could not log in. I know it is not the password, but Ubuntu itself. 
What is KDE? Were you able to go back to a more user friendly interface of Ubuntu?

---

### Post by Richiegs on 2009-11-04
> **P4man said:**
> perhaps you have the wrong keyboard layout or you had it wrong in the live cd. theozzlives's solution should help then though.

I have the right keyboard (U.S.) and I installed Ubuntu 9.10 via Wubi. I have no problem logging into Ubuntu from my notebook computer using Vista, but I just can't log into Ubuntu from my desktop computer using Windows XP.

---

### Post by M567 on 2009-11-06
KDE is another Desktop enviroment which is used if you installed Kubuntu but for reason I got Gnome (the default desktop) as well as KDE when I installed Ubuntu 9.10. I find if I login using KDE and log off staight after and go back to Gnome I'm able to log in again. If your installation was the same you may see a drop down list at the bottom of the login screen after you click your user name but before you enter your password. I know this is a pain but it's the only thing that works for me.

---

### Post by stmcc on 2010-01-03
Check your screen resolution.
System/preference/display.
change to the default: 1280X960
MAC

---

