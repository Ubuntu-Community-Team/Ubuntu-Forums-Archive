---
title: "Stress testing installations for performance and stability"
date: 2011-02-13
forum: General Help
---

### Post by blaineclrk on 2011-02-13
Hello all, I'm going to be installing Vinux which is Linux for the Visually Impaired, based on Ubuntu, onto most any computers I can get my hands on to give to the VI community around my area. I'd like to know what would be a good method to stress test each computer to ensure that each one will operate at an adequate speed without freeze-ups. Sorry, I can't be specific about the computers. I'll be taking whatever gets donated from the public and from businesses, desktops and laptops, whatever comes my way. I don't want to send out any headaches to anyone by giving them a dog-tired slow or a freezing computer that won't even operate.

---

### Post by debd on 2011-02-13
U may try running the System Testing utility that comes with the Ubuntu 10.10 installation.

Administration>System Testing

---

### Post by Habitual on 2011-02-13
Description: A tool to impose load on and stress test a computer system
 'stress' is a tool that imposes a configurable amount of CPU, memory, I/O,
 or disk stress on a POSIX-compliant operating system and reports any errors
 it detects.
 .
 'stress' is not a benchmark.  It is a tool used by system administrators to
 evaluate how well their systems will scale, by kernel programmers to evaluate
 perceived performance characteristics, and by systems programmers to expose
 the classes of bugs which only or more frequently manifest themselves when
 the system is under heavy load.

```
sudo apt-get install -y stress
```

---

### Post by blaineclrk on 2011-02-13
Habitual, thanks. I did a bit of checking, found stress and stressapptest. Now, how to calculate the reasonable usage peak capacity of each version? There's a stable 2.* CLI version and a stable 3.* GUI and there will be more to come of course. I'll need some pointers on this too, or would I be better off checking with the developers?
Again, thanks.

---

### Post by Habitual on 2011-02-14
You're very welcome, Blaine.

---

