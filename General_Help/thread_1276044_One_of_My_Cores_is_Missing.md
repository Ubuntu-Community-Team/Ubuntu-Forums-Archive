---
title: "One of My Cores is Missing"
date: 2009-09-26
forum: General Help
---

### Post by jamesisin on 2009-09-26
I used to see two cores in System Monitor.  Now there is only one.  Not sure when this happened, but it's really a drag--and I think I'm seeing negative performance.  Any ideas?

Dell Dimension 8300 (4gb ram) running 8.10

---

### Post by jerrrys on 2009-09-26
in terminal enter **lshw**...how many do you see?

---

### Post by jamesisin on 2009-09-26
Is this the section in question?

```
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.9
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0

```

---

### Post by jerrrys on 2009-09-26
no, just below that.  if you have two cpu's running it will say cpu0 and cpu1

---

### Post by jerrrys on 2009-09-26
your running a pentium; turn hyperthreading back on...

---

### Post by jamesisin on 2009-09-26
Not seeing it...

```
     *-cpu
          product: Intel(R) Pentium(R) 4 CPU 2.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 15.2.9
          size: 18EHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up pebs bts cid xtpr
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 8KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-pci

```

---

### Post by jerrrys on 2009-09-26
what about hyperthreading?

---

### Post by jamesisin on 2009-09-26
A little help?  I'm guessing that on a recent kernal update hyperthreading was turned off (as part of the update)--because I sure as hell didn't do it.  How do I go about turning it back on?

---

### Post by jerrrys on 2009-09-26
need to reboot; enter bios and turn on hyper option....if you need more instruction, please to let me know...

---

### Post by jamesisin on 2009-09-26
I'll look at the BIOS.  I'll check back with you.

---

### Post by jamesisin on 2009-09-26
Shockingly, hyperthreading was disabled in the BIOS.  Any idea how that would have happened?

---

### Post by jerrrys on 2009-09-26
act of God :)

---

### Post by jamesisin on 2009-09-26
Great.  Let's get that ****** into the confessional...

Thanks for your help.

---

### Post by dcstar on 2009-09-26
> **jamesisin said:**
> Shockingly, hyperthreading was disabled in the BIOS.  Any idea how that would have happened?

Your MB battery may be dying and resetting the BIOS settings to default after long periods of power off.

---

### Post by jerrrys on 2009-09-27
two good points.  mb battery and please to mark your thread as solved...

---

### Post by jamesisin on 2009-09-27
Ah, yes.  I remember seeing a warning about the battery being low when I took the machine out for the weekend.  I suppose I should look into replacing it then?

---

