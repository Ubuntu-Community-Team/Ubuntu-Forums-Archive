---
title: "Chrome keeps closing immediately after opening"
date: 2012-04-03
forum: General Help
---

### Post by joeccash on 2012-04-03
So everytime I open Chrome, it immediately closes again and if it doesn't, the second I click something it closes. I've tried uninstalling and reinstalling although I'm not sure if I did it right.

Here's what I get when I try to run it from the terminal:

--2012-04-03 08:56:12--  [https://clients2.google.com/cr/report](https://clients2.google.com/cr/report)
Resolving clients2.google.com... 209.85.143.101, 209.85.143.100
Connecting to clients2.google.com|209.85.143.101|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `/dev/fd/3'

    [<=>                                    ] 0           --.-K/s              
Crash dump id: 017dd99bb01a09a4
    [ <=>                                   ] 16          --.-K/s   in 0s      

2012-04-03 08:56:14 (220 KB/s) - `/dev/fd/3' saved [16]

Segmentation fault

---

### Post by Ptitphysik on 2012-04-03
Same for me with :

[2:2:1916342481:ERROR:zygote_main_linux.cc(520)] write: Broken pipe
Erreur de segmentation

---

### Post by chubbtech on 2012-04-03
Same here, since last night after update

--2012-04-03 07:15:10--  [https://clients2.google.com/cr/report](https://clients2.google.com/cr/report)
Resolving clients2.google.com... 72.14.204.113, 72.14.204.138, 72.14.204.102, ...
Connecting to clients2.google.com|72.14.204.113|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: `/dev/fd/3'

    [<=>                                    ] 0           --.-K/s              
526e4705ac6be125    [ <=>                                   ] 16          --.-K/s   in 0s      


2012-04-03 07:15:12 (481 KB/s) - `/dev/fd/3' saved [16]

Segmentation fault

---

### Post by codemaniac on 2012-04-03
seems like the bug has already been reported .
[http://code.google.com/p/chromium/issues/detail?id=120310#c1](http://code.google.com/p/chromium/issues/detail?id=120310#c1)

---

### Post by rlhawk1 on 2012-04-03
I'm having the same problem. Started happening right after updating to the 3.0.0-18 kernel. Or maybe it was caused by something else in the updates this morning. I'm not sure.

I'm running Google Chrome 18.0.1025.142 beta

Edit:  Tried updating to Google Chrome 19.0.1084.1 dev and it made no difference.  Makes me suspect it's something besides chrome itself.

---

### Post by rlhawk1 on 2012-04-03
For me, this turned out not to be a problem with Chrome, but rather the 3.0.0-18 kernel that I got updated to this morning.  I rolled back to 3.0.0-17 and now Chrome and other programs that were crashing are doing just fine.

---

### Post by chubbtech on 2012-04-04
How easy is it to roll back?

---

### Post by lolwhites on 2012-04-04
Install Startup Manager, and choose the kernel you want to boot into from the drop down menu.

---

### Post by chubbtech on 2012-04-04
Thx for the help.  Comments on Startup manager say that it doesn't work with 11.04 and up....but then I noticed an option in grub menu to boot with previous ubuntu versions.  Now everything's back to normal until they fix the bug in that kernel version.  :)

---

### Post by kohoutek1 on 2012-04-05
A user has posted a kernel patch to address this problem, which is affecting many applications, not just Chrome/-ium:

[http://people.canonical.com/~herton/fpu_bug/]("http://people.canonical.com/~herton/fpu_bug/")

---

### Post by chubbtech on 2012-04-11
last build .....19 has same bug!  How do I use the patch...do I need to be running the ...18 build?  and is the patch executable or do I need a command line?

thx

---

### Post by bananas1927 on 2012-10-03
Same thing happening to me! No idea what to do. Just found this thread doing a search.

---

### Post by PC_load_letter on 2012-10-29
This is really annoying. It's happening to me on Chromium (the open-source version of Chrome) version 20.0.1132.47 Ubuntu 12.04 (144678).
It's very frequent and erratic. I run Ubuntu 12.04 64bit, nvidia GPU, kernel 3.2.0-32. Here is what I got from the terminal, last few lines are the ones relevant to crash.```
$ chromium-browser 
[4577:4592:1215750690:ERROR:phonenumberutil.cc(1615)] Invalid or unknown region code (ZZ) provided.
[4577:4592:1217601433:ERROR:phonenumberutil.cc(1615)] Invalid or unknown region code (ZZ) provided.
[4577:4592:1217603918:ERROR:phonenumberutil.cc(1615)] Invalid or unknown region code (ZZ) provided.
[4577:4592:1217672475:ERROR:phonenumberutil.cc(1615)] Invalid or unknown region code (ZZ) provided.

(exe:4741): Gdk-WARNING **: XID collision, trouble ahead

(exe:4741): Gdk-WARNING **: XID collision, trouble ahead

(exe:4741): Gdk-WARNING **: XID collision, trouble ahead

(exe:4741): Gdk-WARNING **: XID collision, trouble ahead

(exe:4741): Gdk-WARNING **: XID collision, trouble ahead

(exe:4741): Gdk-WARNING **: XID collision, trouble ahead

(exe:4741): Gdk-WARNING **: XID collision, trouble ahead

(exe:4741): Gdk-WARNING **: XID collision, trouble ahead
[4577:4690:2646723704:ERROR:phonenumberutil.cc(1615)] Invalid or unknown region code (ZZ) provided.
[4577:4690:2646726843:ERROR:phonenumberutil.cc(1615)] Invalid or unknown region code (ZZ) provided.
[4577:4690:2646731063:ERROR:phonenumberutil.cc(1615)] Invalid or unknown region code (ZZ) provided.
Segmentation fault (core dumped)

```

---

