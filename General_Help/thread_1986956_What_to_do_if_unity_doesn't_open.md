---
title: "What to do if unity doesn't open?"
date: 2012-05-25
forum: General Help
---

### Post by hg088 on 2012-05-25
Last night i rebooted my system and it didnt show the unity interface, it was showing the terminal asking for my login and pass.

I just reinstalled ubuntu cause there was nothing really important in my system and seemed like the faster option.

The thing is that in the future i'd like to be able to tweak this problem, because i might want to save my current system instead of doing a full reinstall.

So i was hoping someone would point my to a guide or tell me what to do if something similar happens in the future, like how to repair or reinstall unity from terminal, or repair x.org.

Thanks!

---

### Post by Erik1984 on 2012-05-25
If you are dropped into the command line from boot you could try

```
startx
```to start the graphical desktop.

---

### Post by wilee-nilee on 2012-05-25
> **hg088 said:**
> Last night i rebooted my system and it didnt show the unity interface, it was showing the terminal asking for my login and pass.

I just reinstalled ubuntu cause there was nothing really important in my system and seemed like the faster option.

The thing is that in the future i'd like to be able to tweak this problem, because i might want to save my current system instead of doing a full reinstall.

So i was hoping someone would point my to a guide or tell me what to do if something similar happens in the future, like how to repair or reinstall unity from terminal, or repair x.org.

Thanks!

Next to the login is a gear it is a drop down, look for Ubuntu 2d.

---

### Post by hg088 on 2012-05-25
I tryed writing "unity" on the terminal (oh newbie me xD) and it said there was somo problem and couldn't open unity. I had it set up to auto login into unity. How can i reinstall unity and x from terminal in case unity is faulty and wont open. And how can i log into unity 2d from terminal.

---

### Post by wilee-nilee on 2012-05-25
> **hg088 said:**
> I tryed writing "unity" on the terminal (oh newbie me xD) and it said there was somo problem and couldn't open unity. I had it set up to auto login into unity. How can i reinstall unity and x from terminal in case unity is faulty and wont open. And how can i log into unity 2d from terminal.

Hold on, don't just try and install stuff, I forget the command to just logout, nor can I find it efficiently, some one will post that or another method to getting to the login window, to see if the 2d is running.

It would not hurt to try unity --reset in the terminal or with alt-f2 to show a command area.

Did you perchance mess with compiz?

---

### Post by hg088 on 2012-05-25
Hmm all i did was reinstalll the catalyst driver. The weird thing is that i rebooted my system a few times before this happened. The other thing i did was install handbrake which is a video transcoding software. I hope someone one eventually post how to lo into unity 2d from terminal or how to fix or reinstall unity from terminal.

---

### Post by wilee-nilee on 2012-05-25
> **hg088 said:**
> Hmm all i did was reinstalll the catalyst driver. The weird thing is that i rebooted my system a few times before this happened. The other thing i did was install handbrake which is a video transcoding software. I hope someone one eventually post how to lo into unity 2d from terminal or how to fix or reinstall unity from terminal.

This should bring up the logout dialogue.

```
gnome-session-quit
```

---

### Post by hg088 on 2012-05-25
Thanks a lot for the info wilee-nilee ill try that if the pronlem comes up again

---

### Post by grahammechanical on 2012-05-25
The screen you are getting is Linux in command line mode. This is why Euroman advised you to run the startx command.

We need the X server to run to provide windowing functions to what follows. And if I understand things correctly in a normal boot they should be LightDM (log-in), Gnome desktop environment, Compiz and then Unity or Metacity instead of Compiz followed by Unity 2D.

If you ever get to a desktop but without the launcher, Dash and top panel but only the wallpaper, then Unity has failed to load for some reason.

Something has failed to load and dumped you at Linux in command line mode. Also remember, that the Grub menu should offer a rescue mode that gives you options, one of which is Resume Normal boot which sometimes over comes the problem.

Regards.

---

### Post by hg088 on 2012-05-26
I tryed the fail safe graphic mode but it gave some error.

Hmm interesting, so the stack is something like:
1. X server
2. LightDm
3. Compiz
4. Unity || Unity 2D

So if the problem was faulty compiz or unity, what i had to do was try to load into Gnome (i didn't have it installed).

If Gnome didn't work either, the problem had to be related to the X server, maybe a bad x.org file caused by the Catalyst driver I installed for my card.

---

