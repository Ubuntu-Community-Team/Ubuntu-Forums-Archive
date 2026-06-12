---
title: "How to disable auto-login or change DE from terminal"
date: 2011-12-09
forum: General Help
---

### Post by KFwLsKvVAs on 2011-12-09
Greetings,

I was messing around with different desktop environments, and I tried scrotwm.  Clicking did nothing, the keyboard did nothing, but I knew the system was up and running and not frozen because the clock continued to do it's thing.  Anyhow, unhappy with that I wanted to try a different WM so I dropped to a command line and rebooted.  Unfortunately though, I have my system set up to auto-login, and so it just booted back into Scrotwm again, with no way to restart or log out than to ctrl alt f-whatever and type it into the terminal.  

So I'm wondering if there's a way to change the true/false value of the auto login part of the boot process from the command line, or if there's just a command I can type in to switch the window manager.  

As I type I'm downloading fedora 16, and since I backed up all my data if nobody answers by tomorrow afternoon central time I'm going to give that a spin, but I'm almost positive that there is a way, I just don't know what it is.  

So if any one would be so kind as to help me out, it would be very much appreciated.  

Regards,

- Bonezzzzzzzzzzzz

---

### Post by BC59 on 2011-12-09
I found this, I don't know if could help you

> Enabling AutoLogin from command line
In ubuntu 10.04: sudo nano /etc/gdm/custom.conf

In Ubuntu 11.10, this has changed to ¨sudo nano /etc/lightdm/lightdm.conf" - sandy(d)

It's in here:
[https://help.ubuntu.com/community/AutoLogin](https://help.ubuntu.com/community/AutoLogin)

ps I don't know what text editor you have. Instead of Nano you can use the Gedit which is default.

---

### Post by KFwLsKvVAs on 2011-12-09
Thank you so much, I'm trying it right now and...

IT WORKED!  Thankyouthankyouthankyou!

---

### Post by BC59 on 2011-12-10
Please mark the thread as solved, from the thread tools close to the top of the page.

---

