---
title: "Genome boot problem"
date: 2010-07-27
forum: General Help
---

### Post by gearsin on 2010-07-27
Hi,
 I installed ubuntu 10.04 a month ago. It was working fine till i was looking for some good C++ IDE (typical window user) and found **Ajunta** and it ask for some missing library. I downloaded the latest version of **glib** and did as per the Install instruction. Now my linux doest boot into GUI interface ( it remain on the ubuntu logo and show dot animation). But if i press CTRL + ALT + F1 (F6) then i can login to terminal. I try too fix using recovery mode but it doesnt help much. Out of curiosity i try to run firefiox and got error

**Symbol look up error /usr/lib/libgtk-x11-2.0.so.0 : undefined symbol : g_strcmp0**

Did i miss something while installing glib? I am fairly new linux system and dont know if i had miss anything.

Thanks

---

### Post by xykivo on 2010-07-27
How did u install Ajunta?
How did u install glib?

Did u install from synaptic, SW store?

---

### Post by gearsin on 2010-07-27
> **xykivo said:**
> How did u install Ajunta?
How did u install glib?

Did u install from synaptic, SW store?
Ajuna i downloaded from this link and follow the install instruction

[http://projects.gnome.org/anjuta/](http://projects.gnome.org/anjuta/)

I dont have the download path for glib but i downloaded the .tar.gz file extracted it and followed the same install instruction.

(i didnt try ubuntu software package)

---

### Post by xykivo on 2010-07-28
Hi

It's always better in Ubuntu to install from the repositories.
There is a 99% chance the app you want (or one that does the same thing) is available there, and installing with apt also resolves any dependencies.
Use synaptic or the SW store/app center.

What probably happened is that you downloaded an a glib version that doesn't export a symbol required by gnome.

I'm at work now (= windows system) so I'll try to do this from memory.

Use ctl+alt+F1 to login to console
Then do
$ ls -l /usr/lib/libglib*

Tell us what is the output.
(Hopefully the glib install didn't remove the old glib).

If there is no output from the command above, try 
$ ls -l /usr/slib/libglib*

---

### Post by corncob on 2010-07-28
> **gearsin said:**
> Hi,
 I installed ubuntu 10.04 a month ago. It was working fine till i was looking for some good C++ IDE (typical window user) and found **Ajunta** and it ask for some missing library. I downloaded the latest version of **glib** and did as per the Install instruction. Now my linux doest boot into GUI interface ( it remain on the ubuntu logo and show dot animation). But if i press CTRL + ALT + F1 (F6) then i can login to terminal. I try too fix using recovery mode but it doesnt help much. Out of curiosity i try to run firefiox and got error
Thanks

Do you get the GUI if you press CTRL + ALT + F7?

---

### Post by xykivo on 2010-07-28
Hey

Finally got back to my home machine.

Previous post contained an error, glib is located in /lib

To find which glib you have installed now run
$ ls -l /lib/libglib*

your output should look something like 

lrwxrwxrwx 1 root root     23 2010-06-01 20:23 /lib/libglib-2.0.so.0 -> libglib-2.0.so.0.2400.1
-rw-r--r-- 1 root root 905480 2010-05-09 07:23 /lib/libglib-2.0.so.0.2400.1

The first entry detailed above is a link that points to the real glib used.
In the list above that is the 2nd entry.

Note that this is for lucid lynx (ubuntu 10.04).

I guess that when you installed glib manually from the tar.gz you overrode the link.
Hopefully you only overrode the link, and not the previously installed glib.

(Again this is just a guess)

---

### Post by gearsin on 2010-08-14
Hi Guys thanks for help . i did the same installed the latest glib and it solved problem.

---

