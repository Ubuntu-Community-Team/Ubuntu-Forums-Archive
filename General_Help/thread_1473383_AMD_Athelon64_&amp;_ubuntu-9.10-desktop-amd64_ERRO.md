---
title: "AMD Athelon64 &amp; ubuntu-9.10-desktop-amd64 ERROR"
date: 2010-05-05
forum: General Help
---

### Post by mayapower on 2010-05-05
I am using windows xp 64bit professional edition and virtualbox 3.1.6. The processor details as per "System Information":
```

System Type : x64-based PC
Processor      : AMD64, Family 15 Model 31 Stepping 0 AuthenticAMD ~2010 MHz

```

When I trying to install ubuntu-9.10-desktop-amd64 using virtualbox, I am getting an error:
```

This kernel requires an x86-64 CPU, but only detected an i686CPU.

```

What's wrong here?

Prashant

---

### Post by plucky on 2010-05-05
> **mayapower said:**
> I am using windows xp 64bit professional edition and virtualbox 3.1.6. The processor details as per "System Information":
```

System Type : x64-based PC
Processor      : AMD64, Family 15 Model 31 Stepping 0 AuthenticAMD ~2010 MHz

```

When I trying to install ubuntu-9.10-desktop-amd64 using virtualbox, I am getting an error:
```

This kernel requires an x86-64 CPU, but only detected an i686CPU.

```

What's wrong here?

Prashant

Did you download the correct virtualbox deb file for amd64 not for i386?

---

### Post by 3rdalbum on 2010-05-05
> **mayapower said:**
> I am using windows xp 64bit professional edition and virtualbox 3.1.6. The processor details as per "System Information":
```

System Type : x64-based PC
Processor      : AMD64, Family 15 Model 31 Stepping 0 AuthenticAMD ~2010 MHz

```

When I trying to install ubuntu-9.10-desktop-amd64 using virtualbox, I am getting an error:
```

This kernel requires an x86-64 CPU, but only detected an i686CPU.

```

What's wrong here?

Prashant

There's a setting in Virtualbox that you need to turn on, in order to have a 64-bit guest OS on a 64-bit CPU. It only works if your CPU has hardware virtualisation capabilities, which some older ones (and some cheaper new CPUs) don't have.

When you go to the settings for the virtual machine, it's under "System" and "Acceleration". You need the "Enable VT-x and AMD-V" and the "Enable Nested Paging" checkboxes ticked.

If they cannot be ticked, then your CPU doesn't support hardware virtualisation features, and you're limited to running 32-bit guest OSes.

---

### Post by mayapower on 2010-05-05
Hi,

I don't see options "Enable VT-x and AMD-V" and the "Enable Nested Paging". I am using
virtualbox 3.1.6. am I out of luck on my processor and architecture?

Prashant

---

