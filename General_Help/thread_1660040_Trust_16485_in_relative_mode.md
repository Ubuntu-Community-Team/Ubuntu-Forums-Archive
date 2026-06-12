---
title: "Trust 16485 in relative mode?"
date: 2011-01-04
forum: General Help
---

### Post by pig_destroyer on 2011-01-04
Hi,
Hope you all had a good Christmas and new year.

Briefly: I have a trust/waltop 16485 widescreen mini tablet, that, due to personal preference, would like to run in relative mode. The tablet is detected, and works in absolute mode.
Using lsusb, the tablet appears as:

```
WALTOP International Corp. Slim Tablet      id=12    [slave  pointer  (2)] 
```
but trying to use 

```
xinput set-mode 12 relative 
```
doesn't give an output itself. Using 
```
xinput -list --long
```

shows that the tablet is set as relative, but no such behaviour can be observed with the tablet in use after I've done this.
I have seen the tablet behave in relative mode under linux before, using the latest version of knoppix, where it's configured as a mouse (not an issue, I don't need pressure sensitivity), so that may be one strategy.
If that's so, is it possible to force the tablet to be recognised as a mouse, and if so how?

Thanks for reading, and best wishes.

---

### Post by Favux on 2011-01-05
What release of Ubuntu are you using?  What driver is the Waltop using?

---

