---
title: "How to install tpctl?"
date: 2011-05-04
forum: General Help
---

### Post by unagimiyagi on 2011-05-04
Hi,

I am trying to get an ultranav to work with a thinkpad.  I see this tool called tpctl, and I have downloaded it.  I do not understand how to install it, however.  Could someone point me to a tutorial?  I have extracted the files, but I am not sure what to do from here.  I could not understand the readme file very well.

Thanks!

---

### Post by Lateralis on 2011-05-04
Firstly, what does this tpctl tool do?  

Secondly, installing programs from a "tarball" - assuming that you downloaded a compressed file in something like a .tar.gz format - can be troublesome and are generally not recommended for the newer Linux user.  There are a few general steps, documented in [this link]("http://www.cyberciti.biz/faq/install-tarballs/") to help get you started.  The basic idea though is to:

1) Uncompress the tarball
2) Configure the installation (usually using ./configure, if that file exists in the directory)
3) Build the executable (using "make")
4) "Install" the executable to a directory in your $PATH environment variable, e.g. /usr/local/bin or ~/bin (using "make install")

The only way to know what to do for sure is to read the README file which will have specific instructions for that particular program. 


To help you out, I've just downloaded the program and had a look at the README.  Very simply, you can install the program by going:

```

sudo make install <OPTIONS>

```

where <OPTIONS> is to be replaced by one of the possible options mentioned in the README file, e.g. HDAPS=1.  These options are driver and system specific so unfortunately I cannot help you with that.

---

### Post by Lars Noodén on 2011-05-04
If you can, try to get tpctl from the [Ubuntu repositories](http://packages.ubuntu.com/).  

If you have to install from source, look at the files that were included.  There should be either a file called README or INSTALL or both.  One of those will give you a list of steps to follow.

---

### Post by Lateralis on 2011-05-04
> **Lars Noodén said:**
> If you can, try to get tpctl from the [Ubuntu repositories](http://packages.ubuntu.com/).  

If you have to install from source, look at the files that were included.  There should be either a file called README or INSTALL or both.  One of those will give you a list of steps to follow.

I actually searched for the package myself and I couldn't find it in the repos.  

The OP also says that he read the README but couldn't make head nor tail of it.  I read it and it makes sense to me but there are driver specific options that can/need to be specified with [I}make[/I].  It is difficult to provide any more advice without more specific knowledge of the laptop and kernel modules.

---

### Post by unagimiyagi on 2011-05-04
Lateralis,
Thanks alot for your help.  I now understand I think how to build the program, however I must not understand what all the options mean.  tpctl is a thinkpad configuration tool.  Basically, I was hoping that this tool would provide a way to get the touchpad and trackpoint to work smoothly, the fan to stop running all the time, and power optimizations.  

I am under the impression that without too much trouble, thinkpads were very ubuntu-compatible and would have equal battery life to a windows machine.  This is for a new laptop, the x220, using the latest ubuntu 11.04.

---

### Post by unagimiyagi on 2011-05-04
> **Lateralis said:**
> I actually searched for the package myself and I couldn't find it in the repos.  

The OP also says that he read the README but couldn't make head nor tail of it.  I read it and it makes sense to me but there are driver specific options that can/need to be specified with [I}make[/I].  It is difficult to provide any more advice without more specific knowledge of the laptop and kernel modules.

Yup, tpctl also is not in the repos as far as I can tell.  I'm not even quite sure that I need tpctl with ubuntu natty.

---

### Post by Lateralis on 2011-05-04
> **unagimiyagi said:**
> Yup, tpctl also is not in the repos as far as I can tell.  I'm not even quite sure that I need tpctl with ubuntu natty.

OK, well, my general philosophy is if it doesn't need fixing, don't fix it!  

But, if you want the tools, I think there is one thing to check first.  Type the following into the command line:

```

lsmod | grep hdaps

```

This will **l**i**s**t the loaded kernel **mod**ules before filtering them through grep which will try to match the string "hdaps".  If "hdaps" is found it will give you some output. By means of an example

```

$ lsmod | grep intel
snd_hda_intel          25805  4 

```

shows one of the kernel modules loaded for my Intel sound card.  

If you get some output, then you could try compiling tpctl using:

```

sudo make install HDAPS=1

```

As the README says, this will replace your current module version with the patched one you have downloaded.  

If you don't get any output from lsmod | grep hdaps, then omit, HDAPS=1,

```

sudo make install

```

All being well, everything will work fine.  If not, it might be because of this: 

> 

With some recent ThinkPad models, the "thinkpad_ec" will refuse to load due to
reserved ports. You can force loading by passing the "force_io=1" parameter
to the "thinkpad_ec" module using /etc/modules.conf (or your distribution's
equivalent).




Just one final comment.  I would like to draw your attention to his comment in the README file:

> 

WARNING: 
This driver uses undocumented features and direct hardware access.
It thus cannot be guaranteed to work, and may cause arbitrary damage
(especially on models it wasn't tested on).


Whilst I do not believe anything I have said will lead to your hardware breaking, in light of this, any actions you make are done at your own risk.  If you are unsure about loading this kernel module then seek advice either from other people that use Linux on your Thinkpad model, from the manufacturer's technical support, or consult these websites: [Website one]("http://www.thinkwiki.org/wiki/HDAPS") and [website two]("http://www.thinkwiki.org/wiki/Tp_smapi").

---

### Post by unagimiyagi on 2011-05-04
Thanks again.  Very useful stuff.

---

