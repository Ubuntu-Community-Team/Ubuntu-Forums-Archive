---
title: "Making hdparm settings permanent."
date: 2010-03-02
forum: General Help
---

### Post by Linuxperiment on 2010-03-02
Hi, I've searched about this and I'm trying to make sure I don't screw anything up. When I type in the following into the terminal:

sudo hdparm -M 128 /dev/sda

Are the changes permanent, even if I restart? If not, how can I make sure it is permanent? I've read of going into the /etc/hdparm.conf file and editing it, but what exactly do I type and where should it be put in the file? Thanks in advance for help!

---

### Post by jdong on 2010-03-02
It depends on your hard disk firmware, BIOS, and what any other OS'es that you boot decide to do. So it may or may not be permanent, but the best way to make sure it stays permanent is to set it on every bootup using hdparm.conf.


What you want is on the lines of

```

/dev/sda {
acoustic_management = 128
}

```

or another equivalent expression is

```

command_line {
hdparm -M 128 /dev/sda
}

```


The configuration file is well documented with how to add options to it with comments explaining examples and listing all available options, in case you want to add other options as well.


Note that annoyingly, some laptop BIOSes even twiddle disk settings when changing from AC to battery power, coming in and out of suspend, etc -- hdparm only runs once at bootup via hdparm.conf; it may be a good idea to check the settings after doing some power-related actions to see if your system is affected by this.

---

### Post by Linuxperiment on 2010-03-02
> **jdong said:**
> It depends on your hard disk firmware, BIOS, and what any other OS'es that you boot decide to do. So it may or may not be permanent, but the best way to make sure it stays permanent is to set it on every bootup using hdparm.conf.


What you want is on the lines of

```

/dev/sda {
acoustic_management = 128
}

```

or another equivalent expression is

```

command_line {
hdparm -M 128 /dev/sda
}

```


The configuration file is well documented with how to add options to it with comments explaining examples and listing all available options, in case you want to add other options as well.


Note that annoyingly, some laptop BIOSes even twiddle disk settings when changing from AC to battery power, coming in and out of suspend, etc -- hdparm only runs once at bootup via hdparm.conf; it may be a good idea to check the settings after doing some power-related actions to see if your system is affected by this.

Alright I'll check that later but for now, I'm wondering why in the hdparm.conf a lot of the code looks like this:

#command_line {
#hdparm -M 128 /dev/sda
#}

and not this:

command_line {
hdparm -M 128 /dev/sda
}

Are the #'s required in any way? (I'm not on my laptop with Linux right now and I can't read the conf file until I'm out of class)

EDIT: A few other things I think might help with answering my question. The laptop only has Ubuntu 9.10, and nothing else. Also is there a way I can find out what the current Acoustic Management Value is? I only know how to set it, but I'm not sure how to check it. I ask this because you told me to check if it changes after suspend, a/c power and battery power, etc.

Sorry for the questions and all. Just trying to make the hard drive run cooler.

---

### Post by jdong on 2010-03-02
Those are commented lines. They are in there as documentation -- examples of how to write configuration commands.

---

