---
title: "nomodeset ???"
date: 2012-07-03
forum: General Help
---

### Post by VVAW on 2012-07-03
i have a dell e6410 and had to set the grb "nosplash nomodeset"

For it to boot up.

After this my compiz settings are locked and do not work.

Does this disable these features or should I do something to fix this thanks

---

### Post by matt_symes on 2012-07-03
Hi

> **VVAW said:**
> i have a dell e6410 and had to set the grb "nosplash nomodeset"

For it to boot up.

The nomodeset kernel boot parameter should just disable kernel mode setting for your graphics card so the card will use the old style user mode setting.

This should not effect Compiz as far as i am aware.

> After this my compiz settings are locked and do not work.

Does this disable these features or should I do something to fix this thanks

Did you test Unity from the LiveCD/USB before you installed it ? Unity does not run very well on some older cards.

Does it boot into Unity2D (aka Unity fallback) ?

Have you tried to run the Unity test ? From a terminal, the command below will shed some light on this.

```
/usr/lib/nux/unity_support_test -p
```

What graphics card do you have ? 

From the terminal

```
lspci -nnk | grep -A2 VGA
```

Case is important in the above command. Post the results back here. It may just be a case of updating your graphics driver.

Kind regards

---

### Post by VVAW on 2012-07-03
I am back to classic 2d running 11.04

00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
	Subsystem: Dell Device [1028:040a]
	Kernel modules: i915
=========================================================
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

note
I used to link for my install problems
[http://askubuntu.com/questions/78714/problem-installing-10-04-on-dell-e6410](http://askubuntu.com/questions/78714/problem-installing-10-04-on-dell-e6410)

---

### Post by bogan on 2012-07-03
Hi!, **matt_symes,**

You Posted:
> ```
lspci -nnk | grep -A2 VGA
``` Case is important in the above command. FYI: the grep option '-i' or '--ignore-case' makes case unimportant, so it is easier to use:
```
lspci -nnk | grep -[COLOR=Red]i[/COLOR]A2 VGA
``` Case is[COLOR=Red] un[/COLOR]important in the above command, [except for the [COLOR=Red]'i'[/COLOR] !! ]

Chao! **bogan**.

---

### Post by matt_symes on 2012-07-03
Hi

> **bogan said:**
> Hi!, **matt_symes,**

You Posted:
 FYI: the grep option '-i' or '--ignore-case' makes case unimportant, so it is easier to use:
```
lspci -nnk | grep -[COLOR=Red]i[/COLOR]A2 VGA
``` Case is[COLOR=Red] un[/COLOR]important in the above command, [except for the [COLOR=Red]'i'[/COLOR] !! ]

Chao! **bogan**.

Thanks bogan. I have come accross the -i switch before though. 

My point is to educate users that the command line is case sensitive. 

There are many commands that do not have an ignore case switch so it is better to highlight case sensitivity when using the command line. 

Most switches are case sensitive as well.

> Case is[COLOR=Red] [COLOR=Black]un[/COLOR][/COLOR][COLOR=Black]important[/COLOR] *in* *the* *above* *command*My emphasis would have been on the words "in the above command".

But you are quite right. In this case i could have used the -i switch, so thanks for pointing that out.

@VVAW.

> Unity supported:          noI think this may indicate your problem but i will look for you.

You may have to use Unity2D.

Kind regards

---

