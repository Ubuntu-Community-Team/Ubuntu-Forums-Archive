---
title: "Conky Setup For Jaunty 9.04"
date: 2009-07-10
forum: General Help
---

### Post by 22x on 2009-07-10
Hi, i installed conky from synaptic manager and type conky in terminal and it shows until i close out terminal. how can i set it up to run in the background and look some what fancy like some screen shots ive seen of it. thanks alot for any help :p

---

### Post by Sub101 on 2009-07-10
You need to edit your .conkyrc. Im reasonably sure it is the top section. Mine looks like:

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
on_window_transparent yes
own_window_hints skip_taskbar,sticky,skip_pager
background yes
```

But I havent edited my conky in a long time as I have it working just as I like.

Alternately you can run conky using Alt+F2.

---

### Post by owenll on 2009-07-10
There is a lot of advice on this forum:

[http://ubuntuforums.org/showthread.php?t=1010741](http://ubuntuforums.org/showthread.php?t=1010741)
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

To get you started:
```
$ gedit /home/(yourname)/.conkyrc 
```


and cut and paste the content of one of the .conkyrc files in this thread, save and exit
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

You can add conky at startup through system->preferences

---

### Post by 22x on 2009-07-10
Thanks for that, how would i edit that exactly ? im real real new to this linux thing and im trying to learn at a medium pace ;) i hope i can understand this stuff and not ask to many stupid questions :p thank you

---

### Post by Sub101 on 2009-07-10
The file .conkyrc is what controls conky. It is located in your home directory, ie /home/"your_username"/.conkyrc

Edit it using a text editor, like gedit. But double clicking should open it for you.

---

### Post by 22x on 2009-07-10
Thank you both for the helping with this, i will look at those threads and post back. if there is anymore information someone might think can help me please post it. thank you

---

### Post by 22x on 2009-07-10
Well it was not to hard at all :p thanks for helping out. i"ll post my results in a screen shot

---

### Post by owenll on 2009-07-11
Looks good. Remember you can change things like colour in your .conkyrc file. ```
$ gedit /home/(yourname)/.conkyrc
```

---

### Post by 22x on 2009-07-11
Im puting ubuntu on all my computers and im on computer #2 :p the thing i would love to know is how do i keep conky there for good even after reboot instead of alt f2 every time. thanks

---

### Post by owenll on 2009-07-13
> **22x said:**
> Im puting ubuntu on all my computers and im on computer #2 :p the thing i would love to know is how do i keep conky there for good even after reboot instead of alt f2 every time. thanks
If you go to system - preferences - startup applicatons and click th plus sign you can add it there with the command **conky** in the second box down (command)

---

