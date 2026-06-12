---
title: "Ubuntu does not start (sometimes)"
date: 2011-08-16
forum: General Help
---

### Post by spartacus80 on 2011-08-16
Hi,
Ubuntu does not start (sometimes). 
I only see the black screen. I have to force shutdown. Any ideas?
thank you very much

---

### Post by varunendra on 2011-08-16
Hi and welcome to the forums :)

Which version of ubuntu are you using? Is it installed or are you trying a live cd?

Assuming it is the latest one (11.04), and is installed on the hard drive, I'd like to have a look at your graphics card and the driver it is using. To get that info, open a terminal, enter the following command and post back the output here:
```
sudo lshw -C display
```

Just copy-paste the output in your new post, then select the pasted text (the output part only) and click on the **# **symbol at the top of the editing box. this creates 'code' tags around the selected text which makes it formatted and more readable.

We may need more outputs later depending upon the errors found.

---

### Post by Mark Phelps on 2011-08-16
> **spartacus80 said:**
> Hi,
Ubuntu does not start (sometimes). 
I only see the black screen. I have to force shutdown. Any ideas?
thank you very much

How long are you waiting before forcing the shutdown?  My experience with 11.04, on a new relatively FAST PC, is that it takes a terribly long time to actually get to a working desktop.  Reminds me of an older, much slower, PC that was running Vista!

As to the not starting, don't mean to be discouraging, but I had exactly the same problem using 10.10 -- and that stayed for the whole six months I was using it.  Sometimes it would make it to the login screen, sometimes it would just sit there -- with the disk activity light being dark.

While 11.04 takes a LOT longer, at least it FINALLY boots -- every time.

---

### Post by spartacus80 on 2011-08-16
I have the latest version.
Usually wait about 10 minutes before forcing

```
 *-display               
       description: VGA compatible controller
       product: NV17 [GeForce4 420 Go 32M]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a3
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=64 maxlatency=1 mingnt=5
       resources: irq:16 memory:ea000000-eaffffff memory:f8000000-fbffffff memory:fc000000-fc07ffff memory:fc080000-fc09ffff

```

---

### Post by spartacus80 on 2011-08-19
Little up!!!:popcorn:

---

