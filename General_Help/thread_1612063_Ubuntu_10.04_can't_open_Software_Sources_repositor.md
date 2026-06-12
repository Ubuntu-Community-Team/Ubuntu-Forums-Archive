---
title: "Ubuntu 10.04 can't open Software Sources repositories manager"
date: 2010-11-02
forum: General Help
---

### Post by lightningfox on 2010-11-02
Hi

I am running Ubuntu 10.04 GNOME.

Today I wanted to add a new repository.


I tried to open the repositories manager (Software Sources) through Synaptic, but nothing happened.

Then I tried to open it directly by directly clicking on the Software Sources program in the system menu, but still it wouldn't open.


I could open it without any problems yesterday so I am not sure why this is happening.

Please help me fix this.

---

### Post by garvinrick4 on 2010-11-02
What happens with:
```
gksudo gedit /etc/apt/sources.list
```
Can add there until get this figured out.

---

### Post by lightningfox on 2010-11-03
Thank you. I'll try that and post what happens.

---

### Post by Jetro on 2010-11-04
I'm posting everywhere I find similar topics, since none have led to a solution yet.
I have exactly the same problem, and this happens when I type that into the terminal:
Nothing. Or, more precisely, I see a window (not really a window, but on the task bar) an icon of sorts and that says "Starting Administrative..." for a few seconds. Then it disappears, and nothing happens.

lightningfox, does Ubuntu Software Center not open, too? It doesn't for me, and I think it's related.

---

### Post by sikander3786 on 2010-11-04
Try to start Software Sources from terminal by using the following command and post back any error messages as they might give an idea about what is going on under the hood.

```
gksu /usr/bin/software-properties-gtk
```

---

### Post by lightningfox on 2010-11-04
Hi

Ubuntu Software Centre opens.


I did the first terminal command and it worked.

Here is the output: 

```
/home/lm/.themes/MurrinaChrome/gtk-2.0/gtkrc:83: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lm/.themes/MurrinaChrome/gtk-2.0/gtkrc:83: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/lm/.themes/MurrinaChrome/gtk-2.0/gtkrc:84: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
```



I did the second terminal command but it didn't work.

Here is the output:

```
/home/lm/.themes/MurrinaChrome/gtk-2.0/gtkrc:83: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lm/.themes/MurrinaChrome/gtk-2.0/gtkrc:83: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/home/lm/.themes/MurrinaChrome/gtk-2.0/gtkrc:84: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
  File "/usr/lib/python2.6/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 87, in __init__
    SoftwareProperties.__init__(self, options=options, datadir=datadir)
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 90, in __init__
    self.reload_sourceslist()
  File "/usr/lib/python2.6/dist-packages/softwareproperties/SoftwareProperties.py", line 538, in reload_sourceslist
    self.distro.get_sources(self.sourceslist)    
  File "/usr/lib/python2.6/dist-packages/aptsources/distro.py", line 90, in get_sources
    raise NoDistroTemplateException("Error: could not find a "
aptsources.distro.NoDistroTemplateException: Error: could not find a distribution template

```

---

### Post by sikander3786 on 2010-11-05
Most probably, it is being caused by a distribution identification failure. There might be some other causes but first of all we will try this one.

Try this from terminal,

```
lsb_release -a
```

It should look like this for 10.04.

```
Distributor ID:    Ubuntu
Description:    Ubuntu 10.04.1 LTS
Release:    10.04
Codename:    lucid

```

If it doesn't look like that, edit the lsb_release file by

```
gksudo gedit /etc/lsb-release
```

And replace the text with this one.

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"
```

---

### Post by lightningfox on 2010-11-05
Thank you for your help but I just upgraded to Ubuntu 10.10.
I appreciate the help you gave me.

Btw I'm from Pakistan also (Karachi), but living in Australia.

---

