---
title: "Dual Boot: Boot menu doesn't show up"
date: 2009-09-04
forum: General Help
---

### Post by Ampi on 2009-09-04
I have a dual boot with Windows 7 and Ubuntu 9.04. I've seen them both working fine. 

When I just finished installing both, the computer would only boot into Windows. Therefore I changed the menu.lst and now it only boots into Ubuntu.

The problem is I think the fact that the menu doesn't show up at all. 
Also the recovery modes of Ubuntu and such aren't visible. 
I guess Ubuntu is the default and just loads automatically. How do I change this so I can choose also for Windows every once in a while?

---

### Post by kiridude on 2009-09-04
Try [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") page.

---

### Post by Bucky Ball on 2009-09-04
Hit 'escape' after you boot the machine.

In Ubuntu, open a terminal and paste in:

```
sudo nano /boot/grub/menu.lst
```

In that file you will find a section like this:

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

```
Comment out the 'hiddenmenu' line, making it look like this:

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu
```

:)

---

### Post by Ampi on 2009-09-04
Thank you.

What I did: Put Windows above the Automagic Kernel-something.
What happended: I guess logically it now only boots into Windows, still no boot menu. So now Ubuntu disappeared, and  that's even worse! 

But most importantly, I still don't understand why I don't have a boot menu...


EDIT: hadn't seen the new reply... gonna give that a try first if I get into Ubuntu...

---

### Post by Bucky Ball on 2009-09-04
Try hitting escape right after booting the computer and the screen flashes to the windows boot. The grub menu goes in there and if it is hidden and Windows is first on the list ...

Hitting escape stops this process and should bring up your grub. If so, boot into Ubuntu and make the changes I suggested in the previous post. :)

---

### Post by Ampi on 2009-09-04
Thanks! Although it was a very very "duh!" moment, sorry for my stupidity :)

I took away the Windows' input before the Automagic Kernel and just kept it in the kernel list where I had it. 

Now I have a visible boot menu and I can actually choose, thanks again...

---

### Post by Bucky Ball on 2009-09-04
Don't forget to check:
```

sudo nano /boot/grub/menu.lst
```Check:

```
# hiddenmenu
```You can change the 'timeout' section above that to adjust how long it waits before booting first on the list or comment that out too and it will just sit there waiting. :)

At least you can choose now. Good work! ;-)

ps: just a tip and just in case. Before you go changing menu.lst, might be an idea to back it up with this command:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
```That will make a copy for you then you can tweak away with confidence and load the backup if you screw up.

---

### Post by Ampi on 2009-09-04
Thanks! I got it alright and I already had a backup :) I only wanted to ask about the time settings indeed, but you already answered that for me, you're quick! :D

---

### Post by Bucky Ball on 2009-09-04
haha, thought I might mention the time setting while we were in menu.lst

You can also get pretty colours:

```
# Pretty colours
color cyan/blue yellow/blue
```But you might already have them. If you want to go the whole way you can install startup-manager and that gives you a GUI to control all these things and more besides!

---

### Post by happirobot on 2010-03-24
Hi, sorry for my slowness, but i'm totally new to ubuntu. i just installed it last night. it works fine, except there is no system dual boot screen for me to switch back and forth to vista.

your solution was exactly what i was looking for. but i can't even get through the first step :(

what i did:
- restarted the system
- kept pressing "Esc" but the system just booted to the log in screen

another way i did:
- just logged in as usual
- opened a terminal
- opened the file but it was blank, except there was a list of options at the bottom, including read, write, exit etc..


please helpppp 

thanks :)






> **Bucky Ball said:**
> Hit 'escape' after you boot the machine.

In Ubuntu, open a terminal and paste in:

```
sudo nano /boot/grub/menu.lst
```In that file you will find a section like this:

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

```Comment out the 'hiddenmenu' line, making it look like this:

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu
```:)

---

### Post by bcbc on 2010-03-24
> **happirobot said:**
> Hi, sorry for my slowness, but i'm totally new to ubuntu. i just installed it last night. it works fine, except there is no system dual boot screen for me to switch back and forth to vista.

your solution was exactly what i was looking for. but i can't even get through the first step :(

what i did:
- restarted the system
- kept pressing "Esc" but the system just booted to the log in screen

another way i did:
- just logged in as usual
- opened a terminal
- opened the file but it was blank, except there was a list of options at the bottom, including read, write, exit etc..


please helpppp 

thanks :)

What version of Ubuntu did you install? If it's karmic koala v9.10 then you have grub2 - so you need to hold down the SHIFT key, not ESC, to get the menu. Also, there is no more menu.lst to edit. You can make changes if you require, but it should have automatically picked up vista when you installed and prompted you with the menu by default. So maybe something else is wrong.

But try the above first.

---

### Post by happirobot on 2010-03-25
ahh that made sense. no wonder i could never find menu.lst lol thank you!!! :D

---

