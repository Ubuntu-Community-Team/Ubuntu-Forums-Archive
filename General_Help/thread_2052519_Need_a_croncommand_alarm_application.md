---
title: "Need a cron/command alarm application"
date: 2012-09-03
forum: General Help
---

### Post by Phoenix_Swelter on 2012-09-03
I am searching for a cron or command alarm application. 

I currently use KDE's kalarm over cron because of its time zone savvy. But now I wish my Python scripts to have the option of user interaction for user-initiated sessions or fall back to defaults when the script is started by the alarm. Unfortunately, kalarm uses a terminal to initiate the commands it starts so everything appears to Python as a tty session.

I read that fcron might do the trick, but when I attempted to install it through the Synaptic Package Manager, it attempted to remove anacron and my entire kubuntu-desktop packages! Does anyone have any knowledge of an app that would have both advanced time zone capability and would not run its sessions through a terminal?

---

### Post by Phoenix_Swelter on 2012-09-04
I discovered that I had erred in my testing. Python can identify Kalarm's Command alarms as being non-tty.

---

### Post by sienile on 2012-09-04
I know it's solved already, but Kalarm can be configured to use different terminals, such as ipython, which would run your python scripts easily.

---

### Post by Phoenix_Swelter on 2012-09-04
> **sienile said:**
> I know it's solved already, but Kalarm can be configured to use different terminals, such as ipython, which would run your python scripts easily.

Interesting. I know that I can configure Kalarm to use various terminals, but it hadn't occurred to me to use any of the Python shells as its terminal. But while I'm enjoying Python, I'm not prepared to totally throw out Bash. And since the terminal selection can only be one or the other, and Bash can run Python scripts much more easily than iPython can run Bash scripts....I think I'll stick with Konsole, thanks. ;)

---

