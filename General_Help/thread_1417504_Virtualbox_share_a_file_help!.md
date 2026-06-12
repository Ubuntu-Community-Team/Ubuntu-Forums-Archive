---
title: "Virtualbox share a file help!"
date: 2010-02-27
forum: General Help
---

### Post by calinut1 on 2010-02-27
Hello,

I just installed virtualbox and installed windows xp on it. I need windows xp for compiling my Lazarus (Free Pascal Compiler) projects in it, so that something I program on ubuntu works on Windows too. Windows works correctly on the virtual machine, there is just one problem. How do i copy a file from ubuntu(for example from/home/user/downloads) into the C drive of windows(Windows is installed on the virtual machine) ?

Thank you!

---

### Post by Vaphell on 2010-02-27
if you are using virtualbox with guest addons, goto windows properties in virtual machine, there is a menu for shared folders. You add some ubuntu folder there, call it share and run in windows ```
net use x:\\vboxsvr\share
``` from now on it should be accesible from windows. If my instructions are inaccurate you can find better easily with google or even here.
there should be help text at the bottom as you hover your mouse over the added folder in shared folders properties (that command line magic is taken from there :) ).

---

### Post by s.fox on 2010-02-27
Hello,

[This]("http://ubuntuforums.org/showthread.php?t=809438") thread on sharing files in Virtualbox may be of use to you.

-Silver Fox

---

### Post by underquark on 2010-02-27
Yes, follow the above.  Give it a meaningful name (like "XP32Share").  Then create a link to your shared folder from within (virtual) Windows - I have assigned it to Drive letter Z.

---

### Post by calinut1 on 2010-02-27
wow, thanks all for the great tips!

but none of these worked, might it be because I use Virtualbox OSE ?

EDIT: Nevermind, I found out what the problem was :P I forgot to install the guest utils(i'm a complete newbie). Thanks to all for taking your time trying to help me! :)

Ubuntu rocks! :D

---

