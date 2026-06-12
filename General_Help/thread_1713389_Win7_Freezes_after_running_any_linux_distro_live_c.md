---
title: "Win7 Freezes after running any linux distro live cd/usb"
date: 2011-03-24
forum: General Help
---

### Post by punk45rock on 2011-03-24
No matter what distro I have used, when I run a live cd/usb installer... even without installing the OS or accessing the OS hard drive, Windows 7 freezes after logging in.
Running this on an Asus G73-JH, I've seen similar problems from other people with Asus notebooks, but they have actually installed the linux OS.
Running Windows home premium x64

---

### Post by punk45rock on 2011-03-27
bump

---

### Post by Ryupower on 2012-05-26
I've been having the same problem (also an ASUS ironically), except that windows 7 always freezes after using an installed linux. I've searched the internet to no avail (always get back to this unanswered thread).

---

### Post by wilee-nilee on 2012-05-26
> **Ryupower said:**
> I've been having the same problem (also an ASUS ironically), except that windows 7 always freezes after using an installed linux. I've searched the internet to no avail (always get back to this unanswered thread).

Run a [IMG]http://ubuntuforums.org/data:image/png;base64,PCFET0NUWVBFIEhUTUwgUFVCTElDICItLy9XM0MvL0RURCBIVE1MIDQuMCBUcmFuc2l0aW9uYWwvL0VOIj4KPEhUTUw+CjxIRUFEPgoJPE1FVEEgSFRUUC1FUVVJVj0iQ09OVEVOVC1UWVBFIiBDT05URU5UPSJ0ZXh0L2h0bWw7IGNoYXJzZXQ9dXRmLTgiPgoJPFRJVExFPjwvVElUTEU+Cgk8TUVUQSBOQU1FPSJHRU5FUkFUT1IiIENPTlRFTlQ9IkxpYnJlT2ZmaWNlIDMuNSAgKExpbnV4KSI+Cgk8U1RZTEUgVFlQRT0idGV4dC9jc3MiPgoJPCEtLQoJCUBwYWdlIHsgbWFyZ2luOiAwLjc5aW4gfQoJCVAgeyBtYXJnaW4tYm90dG9tOiAwLjA4aW4gfQoJLS0+Cgk8L1NUWUxFPgo8L0hFQUQ+CjxCT0RZIExBTkc9ImVuLVVTIiBESVI9IkxUUiI+CjxQIFNUWUxFPSJtYXJnaW4tYm90dG9tOiAwaW47IGxpbmUtaGVpZ2h0OiAxNTAlIj48Rk9OVCBGQUNFPSJWZXJkYW5hLCBzYW5zLXNlcmlmIj48Rk9OVCBTSVpFPTEgU1RZTEU9ImZvbnQtc2l6ZTogOHB0Ij5jaGtkc2sKL3IgPC9GT05UPjwvRk9OVD4KPC9QPgo8L0JPRFk+CjwvSFRNTD4A[/IMG] [FONT=Verdana, sans-serif][SIZE=1]chkdsk /r [/SIZE][/FONT]on your windows and start your own thread.

---

### Post by oklokl on 2012-05-26
Bios (Reset )Kink
 Reset HDD (Remove the data cable)
To build a new -> mbr

Or hardware conflicts.
cd booting Options

have a choice

acpi=off        
nolapic          
noapic          
nodmraid    
nomodeset   (Graphics)
boot edd=on

---

### Post by Ryupower on 2012-05-28
deleted, sorry tech error.
Made a thread regarding this. Thanks!

---

