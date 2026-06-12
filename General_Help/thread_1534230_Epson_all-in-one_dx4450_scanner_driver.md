---
title: "Epson all-in-one dx4450 scanner driver"
date: 2010-07-19
forum: General Help
---

### Post by J V on 2010-07-19
Epson stylus dx4450 - Printer works, scanner doesn't

Any ideas?

---

### Post by sisco311 on 2010-07-19
Download and install iscan: [http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do](http://www.avasys.jp/lx-bin2/linux_e/spc/DL1.do)

---

### Post by J V on 2010-07-20
Great, thanks

---

### Post by balta on 2011-02-03
Hi there!
Sorry to bring this up after a long time, but I'm the very same situation.
> Epson stylus dx4450 - Printer works, scanner doesn't
[S]What drivers did you get for your 4450?
I'd assume the 4000 but I'd rather not risk with drivers (gosh I'm even using a x64 version of ubuntu, really hope this works!)
The true problem is the site looks quite confused to me .... :(
Thanks for your time.[/S]

EDIT:
So, after scrolling till the very end I selected: *Epson Stylus CX4300/CX4400/CX4450/CX5500/CX5600/DX4400/DX4450* and filled the drop downs with (surprise surprise!) Ubuntu 10.10.
Next I download the *deb 64bit package [libltdl7] (for Ubuntu 8.10 or later)*, I download both offered files.

When running the *iscan_2.26.1-3.ltdl7_amd64.deb* it pops out the ubuntu software center and says 
```
Dependency is not satisfiable: iscan-data 
```
If I try to run the other packet (*iscan-plugin-cx4400_2.1.0-1_amd64.deb*) I get this error ```
Dependency is not satisfiable: iscan (>= 2.23.0) 
```

I tryed looking in the synaptic for iscan but had no results... any clue, hint or help would really greatly appreciated as scanning is one of the few things that still bounds me to windoze

Thanks for your time.

---

### Post by sisco311 on 2011-02-03
> **balta said:**
> Hi there!
Sorry to bring this up after a long time, but I'm the very same situation.

What drivers did you get for your 4450?
I'd assume the 4000 but I'd rather not risk with drivers (gosh I'm even using a x64 version of ubuntu, really hope this works!)
The true problem is the site looks quite confused to me .... :(
Thanks for your time.

Scroll down the page to where it says:

[center]Please select the model and the distribution that you are using.

***Model*- Image Scan! for Linux & Photo Image Print System**[/center]

The dx4450 is listed in the first column of the second row. Select it, then scroll to the bottom of the page, select the distribution & version and click next.

Scroll down the page to the **Scanner Driver** driver section and download:
**iscan-data_1.6.0-0_all.deb** 
**iscan_2.26.1-3.ltdl7_amd64.deb**
and
**iscan-plugin-cx4400_2.1.0-1_amd64.deb**

Double click the .deb files to install them...

---

### Post by balta on 2011-02-04
Thanks! I was totally missing the *iscan-data_1.6.0-0_all.deb *
As soon as I can try it at home I'll write something.
Thanks a lot! I really appreciate your help!

Edit: Thanks, that definitely worked just perfectly fine!
I just can't see why those packages are not default installed or implemented in cups or at least available from the synaptic!
Thanks also for the explanations :D
I owe you one!

---

### Post by kalaharix on 2011-02-12
ditto thanks. works a treat.

---

### Post by tedd.aiwa on 2013-01-12
Hi sisco311, I'm a new linux user and I have the same problem as [balta]("http://ubuntuforums.org/member.php?u=592764"). I followed all the instructions you gave him and nothing happened. I have the same answers as him:

Dependency is not satisfiable: iscan-data


Dependency is not satisfiable: iscan (>= 2.23.0)

I installed **iscan-data_1.6.0-0_all.deb** first and then the others: **iscan_2.26.1-3.ltdl7_amd64.deb & ****iscan-plugin-cx4400_2.1.0-1_amd64.deb **Is the right installation order an issue?
Any suggestions for me?  (I have the Epson all-in-one dx4400 scanner) on Kubuntu 12.10
Thanx in advance

---

### Post by pdc on 2013-01-14
an all-seeing, all-knowing forum administrator is likely to tell you to start a new thread .......

........they hover high above......in the stratosphere........

............go on .............you deserve it..........

.........the issue is important enough for you ...............

...........start a new thread .................

---

