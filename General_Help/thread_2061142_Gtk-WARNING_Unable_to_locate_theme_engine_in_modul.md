---
title: "Gtk-WARNING: Unable to locate theme engine in module_path &quot;murrine&quot;"
date: 2012-09-21
forum: General Help
---

### Post by MartinMorrison on 2012-09-21
Hey guys,

Really need some help. I was using VMplayer and it was working fine, not sure what happened but I tried to run it today and it works but I get a ton of errors:

(vmware-unity-helper:3618): Gtk-WARNING **: Unable to loction theme engine in module_path:"murrine" 

When I try run my virtual image through vmplayer it doesn't load and I get the error:

GTK-Message" failing to load module "canberra-gtk-module": libcanberaa-gtk-module.s: cannot open shared obkect file: no such file or directory

Please help - I have no idea what to do !

---

### Post by MartinMorrison on 2012-09-21
Can anyone help? Really need to get this working for a project and i've exhausted all forum solutions I can find...

---

### Post by jwonch on 2012-10-01
I received a similar error when installing VMware player and the player installed okay (so far).

---

### Post by p0nman on 2012-10-16
I have the same issue with VMware workstation 9.0 when I attempt to connect to out vCenter.  

```
(vmware-netcfg:16192): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

```

however gtk2-engines gtk2-engines-murrine are both installed.

---

### Post by vitorjorge on 2013-01-24
Hi to solve the 

Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
define the path to the gtk modules

vi /etc/bash.bashrc

append to file

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/x86_64-linux-gnu/gtk-2.0/modules/

exist current shell and open a new one and check.

---

### Post by pcatalani on 2013-02-14
Several posts recommended installing gtk2-engines, which I already had. With Kubuntu quantal the gtk2-engines-murrine must not be included. The following resolved the 46 warnings each time launching a gtk app:

```
sudo apt-get install gtk2-engines-murrine
```

---

### Post by minwook on 2013-05-06
In case the message

    Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine"

persists, it could be because you need 32 bit version of gtk2-engines-murrine.


    sudo apt-get install --reinstall gtk2-engines-murrine:i386

can solve the issue

---

### Post by Corin-EU on 2013-05-26
> **vitorjorge said:**
> Hi to solve the 

Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory
define the path to the gtk modules

vi /etc/bash.bashrc

append to file

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/lib/x86_64-linux-gnu/gtk-2.0/modules/

exist current shell and open a new one and check.

No, this is incorrect.

The error is not coming from the linker **ld** viz "*error while loading shared libraries"*, but from **Gtk-Message** viz "*failed to load module*", so the environmental variable which needs to be set is **GTK_PATH**, not LD_LIBRARY_PATH.

From **<[https://developer.gnome.ORG/gtk3/3.9/gtk-running.html](https://developer.gnome.ORG/gtk3/3.9/gtk-running.html)>**

> 
Running GTK+ Applications

**GTK_PATH**. 
 Specifies a list of directories to search when GTK+ is looking for dynamically loaded objects such as the modules specified by **GTK_MODULES**, theme engines, input method modules, file system backends and print backends. If the path to the dynamically loaded object is given as an absolute path name, then GTK+ loads it directly. 

---

### Post by linden@kth.se on 2013-07-08
$ sudo apt-get install --reinstall gtk2-engines-murrine:i386
solved my problem (on a 64-bit Ubuntu 13.04).

---

### Post by ikem.krueger on 2013-07-11
I fixed it with:

```
sudo apt-get install gtk2-engines-murrine:i386
```

---

### Post by Trevor_Rose on 2013-09-06
I have the same issue.

Latest version of vmplayer 6.0 installed in ubuntu 13.04

Neither of these solutions (the installing of murrine:i386 nor the modification of adding the GTK_PATH to bash.bashrc) ... 


[LIST]
[*] when he said "append", does it matter where in the file that line goes?
[*]do I need to reboot afterwards or only exit the shell & run "sudo vmplayer" again?
[*]any other ideas?
[/LIST]

---

### Post by Trevor_Rose on 2013-09-06
could you please have a look at my post at the end of this thread & see if you have any suggestions?

Sorry that was directed to[SIZE=2][COLOR=#000000] Corin-EU, but I forgot to do the reply with quote[/COLOR][/SIZE]

---

### Post by Gui_Ambros on 2014-05-26
[COLOR=#000000][FONT=Arial]If none of the other answers solved your problem, you can also try[/FONT][/COLOR]

```
sudo apt-get install libgtkmm-2.4-1c2a libgtkmm-2.4-dev
```
[COLOR=#000000][FONT=Arial]
This worked for me (Ubuntu 14.04 x64, Gnome 3.12). I already had the gtk2-engines-murrine installed (both i386 and x64), and changing the GTK_MODULES didn't do anything for me.[/FONT][/COLOR]

---

### Post by Frogs Hair on 2014-05-26
Back to sleep ! old thread.

---

