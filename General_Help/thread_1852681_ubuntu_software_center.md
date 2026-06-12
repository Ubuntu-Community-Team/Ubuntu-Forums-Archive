---
title: "ubuntu software center"
date: 2011-09-30
forum: General Help
---

### Post by Oinkzter on 2011-09-30
hello everyone, when i try to download compiz, from ubuntu software center
it gives me this message: The following packages have unmet dependencies:

simple-ccsm: 


do you know what to do? 
i hope you guys can help me.

-Oinkzter

---

### Post by papibe on 2011-09-30
Welcome to the forums!

Try updating your system first:
[LIST]
[*]Close the Software Center.
[*]Open Update Manager.
[*]Apply any pending updates.
[*]You can check for more updates by pressing 'check'
[/LIST]

Now Open the Software Center and try again. If that doesn't work, try this commands on the terminal:

To update your sources:
```
$ sudo apt-get update
```
To receive the latest upgrades, of what you have installed:
```
$ sudo apt-get upgrade
```
Did any of those commands give you any error? If not, try installing the package on the terminal to see more details:
```
$ sudo apt-get install simple-ccsm
```
Hope it helps, and tell us how it goes.
Regards.

---

### Post by seawolf167 on 2011-09-30
Try opening a terminal and typing in this command and see if it works for you

```
sudo apt-get install compiz compizconfig-settings-manager
```

or for the simple version

```
sudo apt-get install simple-ccsm
```

---

### Post by Oinkzter on 2011-09-30
sorry but none of this worked, i've follow the exact order that you gave, but none of it worked. any other suggestions? :(

---

### Post by garvinrick4 on 2011-09-30
Do you have your repositories open? software sources.
Like the screenshot click on it make sure yours are checked also then:
Open a terminal and copy and paste:
```
sudo apt-get update; sudo apt-get upgrade
``````
sudo apt-get install python
```
```
sudo apt-get install simple-ccsm
```

---

### Post by garvinrick4 on 2011-09-30
This is just info on packages of simple-ccsm and compizconfig-settings-manager
```
Package: simple-ccsm                     
State: not installed
Version: 0.8.2-0ubuntu1
Priority: extra
Section: universe/x11
Maintainer: Michael Vogt <mvo@ubuntu.com>
Uncompressed Size: 635 k
[COLOR=Red]Depends: python, python-central (>= 0.6.11), python-gtk2, python-compizconfig
         (>= 0.8.2), compizconfig-settings-manager (>= 0.8.2)[/COLOR]
Description: Simple Compizconfig settings manager
 The OpenCompositing Project brings 3D desktop visual effects that improve
 usability of the X Window System and provide increased productivity. 
``````
Package: compizconfig-settings-manager   
State: installed
Automatically installed: no
Version: 0.9.4-0ubuntu2
Priority: extra
Section: universe/x11
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 5,894 k
Depends: python, python-central (>= 0.6.11), python-compizconfig (>= 0.9.0),
         python-gtk2
Description: Compiz configuration settings manager
 The OpenCompositing Project brings 3D desktop visual effects that improve
 usability of the X Window System and provide increased productivity. 
 
 This package contains the compizconfig settings manager.
 
 This package contains a simple compizconfig settings manager application.
```

---

### Post by Oinkzter on 2011-09-30
that didn't work either. other suggestions?:P

---

### Post by Oinkzter on 2011-09-30
when i tipe in "sudo apt-get install simple-ccsm" in teminal it says:
oinkzter@Oinkzter:~$ sudo apt-get install simple-ccsm
[sudo] password for oinkzter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 simple-ccsm : Depends: python-compizconfig (>= 0.8.2) but it is not going to be installed
               Depends: compizconfig-settings-manager (>= 0.8.2) but it is not going to be installed
E: Broken packages
oinkzter@Oinkzter:~$

---

### Post by garvinrick4 on 2011-09-30
```
/usr/lib/nux/unity_support_test -p
```
What does this say?
Here is mine below.
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20100330 DEVELOPMENT 
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

Here is screen shot of simple-ccsm in Ubuntu Software center

---

### Post by garvinrick4 on 2011-09-30
> E: Broken packages
```
sudo dpkg --configure -a
```
```
sudo apt-get -f install
```
```
sudo apt-get install simple-ccsm
```

---

### Post by Copper Bezel on 2011-09-30
> ```
E: Broken packages
```
What happens if you run 

```
 sudo apt-get install -f
```

and try again?

Edit: garvinrick4 beat me to it. = )

---

### Post by Oinkzter on 2011-09-30
oinkzter@Oinkzter:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM GEM 20100330 DEVELOPMENT x86/MMX/SSE2
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes

---

### Post by garvinrick4 on 2011-09-30
Last post was good, now the next post to fix broken packages?

---

### Post by Oinkzter on 2011-09-30
it still says E:broken package

---

### Post by garvinrick4 on 2011-09-30
Under edit in synaptic go to fix broken packages and use that function.

---

### Post by Oinkzter on 2011-09-30
oinkzter@Oinkzter:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM GEM 20100330 DEVELOPMENT x86/MMX/SSE2
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes


is that good or bad??? and do you have any more ideas?

---

### Post by garvinrick4 on 2011-09-30
> **Oinkzter said:**
> oinkzter@Oinkzter:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) 965GM GEM 20100330 DEVELOPMENT x86/MMX/SSE2
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          yes


is that good or bad??? and do you have any more ideas?
It means your machine will support 3D, that is a good thing. Did you do the previous
post with opening synaptic, if you cannot find it. I presumed you were not in 11.10 oneiric. If you are then install.
```
sudo apt-get install synaptic
```##Or did previous post fix your problem and you just wanted to know what above meant?

---

### Post by Oinkzter on 2011-10-01
i think i'm running 10.10, because that the the best (in my opinion)
so i didn't find  the broken package thing under edit.
should i upgrade my Ubuntu to the newest?
i still can't install it.
more suggestions?

---

### Post by garvinrick4 on 2011-10-01
Should have a fix packages in synaptic, let me look in 10.10 I have one installed. Be back. Always been
there as far as I can remember synaptic.

##synaptic has under drop down in menu in upper left of window a "repair broken packages" that you can run.

```
lsb_release -a
```To see version you are running.

You do what you are comfortable with if you cannot install in the Desktop Download of Ubuntu the best is the alternate download.
Take a more focus because no installer GUI (ubiquity) have to use enter key and arrows. 
[http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)
> i still can't install it.Or did you mean synaptic it is already installed in 10.10 but not in 11.10 that is still in beta and what you should not be using at all.
Will get dependency problems and breakage if use partial upgrades in upgrade manager. Comes with the territory with Alpha's and Beta's is not a stable version.
Run the:
```
lsb_release -a
```for me please.

Open synaptic and give a try though just to see if it fixes the broken packages problem if running any but 11.10 and did partial upgrades.

---

