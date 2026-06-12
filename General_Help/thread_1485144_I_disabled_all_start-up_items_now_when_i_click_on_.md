---
title: "I disabled all start-up items now when i click on login it doesn't do anything."
date: 2010-05-16
forum: General Help
---

### Post by cokeh21 on 2010-05-16
Hi guys, i was enjoying 9.10 and then i switched to 10.04, getting it configured properly i was removing stuff from startup preferences.
 
now when i click on my login name, enter my password into the prompt, it plays a noise and i see an x for a split second and it goes back to the same user select main login screen.
 
Not being familiar with console, I did try the following
 
pressed ctrl + alt + f1
 
it took me to terminal on login, i logged in with my credentials
 
i made a new user, hoping that the start up items have been resetted.
 
it did not work, the new user does the same thing
 
my question is the following
 
how can i reset the startup items to defaults using terminal?
 
thanks in advance.

---

### Post by ranch hand on 2010-05-16
I would try doing that by booting to recovery mode and working from the CLI there.  A new user should do the job.

You really do need things like your key ring to start.

---

### Post by cokeh21 on 2010-05-17
It was my window manager that disappeared, maximize minimize funcations and such were missing. Also couldn't use the show desktop button. I created a new user and problem was fine. but with my own account it was the same.. that's when i went ahead and disabled all startup items..
 
booting to recovery mode, i am assuming i boot up from the live CD? i will research how to boot into recovery mode, if anyone can point me in the right direction i would appreciate it.

CLI i am assuming stands for command line interface which is the terminal?
 
 
desktop technician but very new to ubuntu:(

---

### Post by ranch hand on 2010-05-17
No, you have the option of booting to recovery mode from your regular menu, or should.  It should be the next entry after menu entry you are using now.

If you do not, when you get the menu up, highlight the regular menu entry and hit  e  .

That will allow you to edit the entry.

You want to change this line;
```

linux    /boot/vmlinuz-2.6.34-2-generic root=UUID=9e1065f7-6ec2-4dde-9f15-13a5b304e318 ro   quiet splash

```
to read this way;
```

linux    /boot/vmlinuz-2.6.34-2-generic root=UUID=9e1065f7-6ec2-4dde-9f15-13a5b304e318 ro single

```
Note that what you are doing is removing the "quiet splash" and replacing it with "single".

After that hit Ctrl+x to boot.

---

