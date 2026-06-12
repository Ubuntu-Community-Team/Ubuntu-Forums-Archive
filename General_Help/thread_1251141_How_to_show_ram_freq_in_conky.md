---
title: "How to show ram freq in conky?"
date: 2009-08-27
forum: General Help
---

### Post by GoldenSun on 2009-08-27
I would like to know if there is a way to monitor ram frequencies in a conky script.

Or if there is a simple app I could dl, but I really want it in my conky.

This might be asking too much, but maybe add northbridge frequencies and HT link speed to conky also.  

Thanks

---

### Post by karlmp on 2009-08-27
[http://ubuntuforums.org/showthread.php?t=1010741](http://ubuntuforums.org/showthread.php?t=1010741)

---

### Post by GoldenSun on 2009-08-27
> **karlmp said:**
> [http://ubuntuforums.org/showthread.php?t=1010741](http://ubuntuforums.org/showthread.php?t=1010741)

So that was unhelpful.  
I know how to configure and edit conky.  I just don't know how to add ram frequencies, and no one in that massive post says anything about it.

---

### Post by bear24rw on 2009-08-27
lshw can show you your memory freq but you need to run it as root, so youd need to run your whole conky as root, which im sure is fine i've done it numerous times before for a samba monitor, heres how i can get my mem freqs in conky

```
sudo lshw -c memory
```

this gives me

```
user@user-server:~$ sudo lshw -c memory
  *-firmware              
       description: BIOS
       vendor: Phoenix Technologies, LTD
       physical id: 0
       version: 6.00 PG (06/02/2009)
       size: 128KiB
       capacity: 960KiB
       capabilities: isa pci pnp apm upgrade shadowing cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
  *-cache:0
       description: L1 cache
       physical id: c
       slot: Cache 1
       size: 32KiB
       capacity: 32KiB
       clock: 1GHz (1.0ns)
       capabilities: synchronous internal write-back data
  *-cache:1
       description: L2 cache
       physical id: d
       slot: Cache 2
       size: 32KiB
       capacity: 32KiB
       clock: 1GHz (1.0ns)
       capabilities: synchronous internal write-back data
  *-cache:2
       description: L3 cache
       physical id: e
       slot: Cache 3
       size: 1MiB
       capacity: 1MiB
       clock: 1GHz (1.0ns)
       capabilities: synchronous internal write-back data
  *-memory
       description: System Memory
       physical id: 23
       slot: System board or motherboard
       size: 6GiB
     *-bank:0
          description: DIMM DDR2 Synchronous 1033 MHz (1.0 ns)
          product: None
          vendor: None
          physical id: 0
          serial: None
          slot: A0
          size: 2GiB
          width: 1 bits
          clock: 1033MHz (1.0ns)
     *-bank:1
          description: DIMM [empty]
          product: None
          vendor: None
          physical id: 1
          serial: None
          slot: A1
     *-bank:2
          description: DIMM DDR2 Synchronous 1033 MHz (1.0 ns)
          product: None
          vendor: None
          physical id: 2
          serial: None
          slot: A2
          size: 2GiB
          width: 1 bits
          clock: 1033MHz (1.0ns)
     *-bank:3
          description: DIMM [empty]
          product: None
          vendor: None
          physical id: 3
          serial: None
          slot: A3
     *-bank:4
          description: DIMM DDR2 Synchronous 1033 MHz (1.0 ns)
          product: None
          vendor: None
          physical id: 4
          serial: None
          slot: A4
          size: 2GiB
          width: 1 bits
          clock: 1033MHz (1.0ns)
     *-bank:5
          description: DIMM [empty]
          product: None
          vendor: None
          physical id: 5
          serial: None
          slot: A5

```

now we only want the clock: so

```
sudo lshw -c memory | grep clock:
```

and we get this

```
user@user-server:~$ sudo lshw -c memory | grep clock:
       clock: 1GHz (1.0ns)
       clock: 1GHz (1.0ns)
       clock: 1GHz (1.0ns)
          clock: 1033MHz (1.0ns)
          clock: 1033MHz (1.0ns)
          clock: 1033MHz (1.0ns)

```

the last three are the RAM freqs so we can do

```
user@user-server:~$ sudo lshw -c memory | grep clock: | tail -n 3
          clock: 1033MHz (1.0ns)
          clock: 1033MHz (1.0ns)
          clock: 1033MHz (1.0ns)

```

so you can use that whole block in your conky or you can tail again to get each one indivdually, this command kinda takes a second to run so idk if id put it in a conky since your ram freqs are not going to change while running but you can just add the lshw line in your ocnky with a execi and you should be good to go

---

### Post by GoldenSun on 2009-08-27
does lshw show the current freq of ram?  
I thought it only read the id of the hardware.  Like if my cpu is OC'd from 2.5 -> 3, it would show that it was running at 2.5.  

And you should oc your DDR3.  Either lower timings, or increase speed.  Would work well with your i7.

Other than that, that's a manly post you added.

---

### Post by karlmp on 2009-08-27
> **GoldenSun said:**
> So that was unhelpful.  
I know how to configure and edit conky.  I just don't know how to add ram frequencies, and no one in that massive post says anything about it.

but at least i bumped your post;)

---

### Post by bear24rw on 2009-08-27
my ram is rated for 1600 and lshw says 1033 so im pretty sure that its reading the real clock not what spec sheet says

---

