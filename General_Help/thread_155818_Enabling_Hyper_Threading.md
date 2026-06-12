---
title: "Enabling Hyper Threading"
date: 2006-04-05
forum: General Help
---

### Post by nw15062 on 2006-04-05
[CENTER][CENTER][FONT="Arial Black"][SIZE="3"]**How To: Enable Hyper Threading**[/SIZE][/FONT][/CENTER]
[SIZE="1"][COLOR="DarkRed"][CENTER]
Hyper Threading by Default is disabled in Ubuntu Linux the ability is in the kernel but is not turned, The reason for this is due to a potential vulnerablity that would allow one thread to veiw another and access cyrptographic data such as passwords.

By enabling ti you do so at your own risk.[/CENTER][/COLOR][/SIZE]

The first step is to make sure you have the best kernel suited for your system, I suggest installing the 686 kernel and make sure you have all the headers.

The second step require you to drop to a command prompt and type 
[CENTER]"*sudo gedit /boot/grub/menu.lst*"[/CENTER]

Look for the line that says 
[CENTER]"*# kopt=root=/dev/hdb2 ro*"[/CENTER]
Leaving everything intact includign the pound symbol simply add
[CENTER] "**ht=on**"[/CENTER]
You should now have this
[CENTER] "*# kopt=root=/dev/hdb2 ro ht=on*"[/CENTER]

Save then file and run the command
[CENTER] "* sudo update-grub*"[/CENTER]

When you restart the system you should see a noticable diffrence in performance.[/CENTER]

---

### Post by dcstar on 2006-04-05
[QUOTE=nw15062][CENTER][CENTER][FONT="Arial Black"][SIZE="3"]**How To: Enable Hyper Threading**[/SIZE][/FONT][/CENTER]
.......[/QUOTE]
Please post any HOWTOs in the appropriate "Tips and Tricks" forum, and if you feel it is necessary, post a notice and link to it in a forum such as this.

People look in specific places for information, placing things in inappropriate forums may be well-intentioned but it generally means that the all the people who may benefit from them will have less chance of seeing them.

---

### Post by jeffrash on 2008-01-16
I have a dual processor box with HyperThreading enabled.  Should I see two or four processors in system monitor?

My "kopt=root" line doesn't look like yours.  Here's what mind looks like.

"# kopt=root=UUID=409480b7-8233-4eb9-84d3-20f54695bc79 ro"

If I add the "ht=on" at the end and rebuild should that enable HT and give me four processors?  

I tried and it doesn't.  

Please help and thanks.

---

### Post by jeffrash on 2008-01-17
Nevermind, I just remembered that this system is only a single processor.  So, HyperThreading is working as it should.  I see two.

Thanks.

---

### Post by prashant2400 on 2008-06-16
Well, i have a core2 Duo intel cpu running at 2.33Ghz. i want to enable hyperthrading on this cpu. when we cat /proc/cpuinfo, it shoes us ht flag. it means that this cpu supports HT. but when i performed all steps listed above,  still i am able to see only 2 cpu.

Is it possible to enable hyperthrading on core2 duo intel cpu and have 4 logical cpu?

Thanks in advance.

Prashant keshvani :confused:

---

