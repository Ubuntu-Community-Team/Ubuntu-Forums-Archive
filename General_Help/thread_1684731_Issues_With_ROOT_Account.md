---
title: "Issues With ROOT Account"
date: 2011-02-09
forum: General Help
---

### Post by SleepyD on 2011-02-09
Hi.

Have just installed Ubuntu 10.10 (it was an online install as my CD/DVD drive is inoperable) and I am so pleased with it - absolutely great!!!):P

However, I appear to have a problem with the ROOT (superuser) account as, responding to package upgrade notification, I attempted to upgrade the system and had no authentication detail for root (this option had not presented itself in the online install.:confused:

I checked the /etc/passwd file and found the root account listed with 'x' in the password field - as expected.

Tried to log in as root in the console (ALT-F2) but the password I used for my normal account would not log me in.

I then tried to enter the command 'root' in the terminal window and was informed that the root system was not installed and to enter the command "***sudo apt-get install root-system-bin***" to install it.

Having executed said command, all I get now is a cint c/c++ interpreter application - useful but not what I immediately require which is access to the ROOT account.

Please help as I am out of ideas and need the root account to administrate this otherwise excellent system.

SD

---

### Post by coffeecat on 2011-02-09
Use sudo with your own account password to obtain administrative privileges. Full explanation here:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

And welcome to the forum!

---

### Post by sisco311 on 2011-02-09
Hi and welcome to the forums!

The root account password is locked by default. You have to use sudo. Take a look at the community documentation:
[uhelp]community/RootSudo[/uhelp]

---

### Post by SleepyD on 2011-02-10
Greetings Coffeecat and sisco311,

Thank you both for your responses.

The info was 100% useful, so I will be marking this thread as SOLVED.
 
Thank you both for your help in this matter.

:D

SD

---

