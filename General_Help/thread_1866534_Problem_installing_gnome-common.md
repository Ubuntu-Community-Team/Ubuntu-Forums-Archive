---
title: "Problem installing gnome-common"
date: 2011-10-21
forum: General Help
---

### Post by Jumper11550 on 2011-10-21
So I'm getting an error and I haven't been able to find a readily understandable explanation of how to fix it.

~/gnome-common$ ./autogen.sh
checking for autoconf >= 2.53...
  testing autoconf2.50... not found.
  testing autoconf... found 2.68
checking for automake >= 1.9...
  testing automake-1.11... found 1.11.1
Checking for forbidden M4 macros...
**Warning**: I am going to run `configure' with no arguments.
If you wish to pass any to it, please specify them on the
`./autogen.sh' command line.

Processing ./autoconf-2.68/configure.ac
Running aclocal-1.11...
Running autoconf...
Running automake-1.11...
Makefile.am:40: MAKE_CASE_SENSITIVE does not appear in AM_CONDITIONAL

I have no idea what AM_CONDITIONAL is. my ultimate goal is to install jhbuild, but want to get the gnome-common installed first.

I am using Ubuntu 11.10

Can any responses please not only include what I need to do to fix it, but also how to do it.  I'm still new to Linux and learning as I go.

Thanks much

---

### Post by satanselbow on 2011-10-21
> **Jumper11550 said:**
> I'm still new to Linux and learning as I go.


Building your own Gnome Shell is a pretty big ask if you are new to linux. I've not been that brave myself :D

You do know Gnome Shell is in the official repos now?

---

### Post by Jumper11550 on 2011-10-21
> **satanselbow said:**
> 
You do know Gnome Shell is in the official repos now?

So how do I install it that way?

---

### Post by Jumper11550 on 2011-10-21
Ultimately I want to install jhbuild and this is the error I get with that so if this can be solved some other way I'd much appreciate that:

~/jhbuild$ ./autogen.sh
gnome-autogen.sh not available
gnome-doc-tools not available
Configuring jhbuild without autotools
Unable to create file ./Makefile.inc

---

### Post by crdlb on 2011-10-21
The files you need to build gnome-common from git are in gnome-common. Install the [gnome-common](apt:gnome-common) package in the Ubuntu repositories.

That said, why do you want jhbuild? That is for developers and testers of the very latest GNOME code. If you just want to use gnome-shell, install the [gnome-shell](apt:gnome-shell) package.

---

### Post by Jumper11550 on 2011-10-21
> **crdlb said:**
> 
That said, why do you want jhbuild? That is for developers and testers of the very latest GNOME code. If you just want to use gnome-shell, install the [gnome-shell]("apt:gnome-shell") package.


Okay so the real problem stems from trying to install gtkmm-3.0.0, I get this error after running ./configure:

No package 'giomm-2.4' found
No package 'pangomm-1.4' found
No package 'gtk+-3.0' found
No package 'cairomm-1.0' found
No package 'gdk-pixbuf-2.0' found

So when trying to install gtk+-3.0 I get this error when running ./configure:

No package 'glib-2.0' found
No package 'atk' found
No package 'pango' found
No package 'cairo' found
No package 'cairo-gobject' found
No package 'gdk-pixbuf-2.0' found

which lead me to this forum:
[http://ubuntuforums.org/archive/index.php/t-1790017.html](http://ubuntuforums.org/archive/index.php/t-1790017.html)

so that's why jhbuild.  if you can help me get gtkmm-3.0.0 installed instead that would be awesome!!!

---

### Post by crdlb on 2011-10-21
```
sudo-apt-get install libgtkmm-3.0-1
```

Or if you're compiling something against gtkmm, you'll also need:
```
sudo apt-get install libgtkmm-3.0-dev
```

What is the actual thing you are trying to install? I assume you're installing gtkmm because it is required by something else.

---

### Post by Jumper11550 on 2011-10-21
First and foremost a very big thank you!!

> **crdlb said:**
> What is the actual thing you are trying to install? I assume you're installing gtkmm because it is required by something else.

Not really, nothing specific anyways.  I wanted to experiment with writing a gui with c++ and gktmm seemed as good a place as any to start.  I suppose I would be open to another suggestion if you think something else would be better

---

### Post by crdlb on 2011-10-21
> **Jumper11550 said:**
> I wanted to experiment with writing a gui with c++ and gktmm seemed as good a place as any to start. That's a very reasonable choice if you're comfortable with C++. There is a [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") forum if you need further help.

---

### Post by Jumper11550 on 2011-10-21
Thank you and I will make sure to check it out

---

