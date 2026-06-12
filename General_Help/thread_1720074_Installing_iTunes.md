---
title: "Installing iTunes"
date: 2011-04-02
forum: General Help
---

### Post by laugh1 on 2011-04-02
I have it installed and use this to run it:
wine ~/.wine/drive_c/Program\ Files/iTunes/iTunes.exe

and get this:
```
fixme:htmlhelp:HtmlHelpW HH case HH_INITIALIZE not handled.
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x163920,0x163820): stub
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000001 not handled
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  1042
  Current serial number in output stream:  1042

```

Help?

---

### Post by matt_symes on 2011-04-02
Hi

iTunes is notoriously difficult to install under wine. 

If you get it working there are still issues with it such as USB support for iPod's and window refresh. 

At least, that was the state of play at Christmas which was the last time i looked.

Run it under a VM or use a Linux native app. That would be my advice.

If the state of play has changed that i am not aware of, someone will speak up.

Kind regards

---

### Post by d3v1150m471c on 2011-04-02
I highly recommend gtkpod instead:
```

sudo apt-get install gtkpod

```

If you need something to convert videos for iPods or iPhones i have an ffmpeg frontend on my site in the link below.

---

### Post by laugh1 on 2011-04-02
I can use those with an ipod?

---

### Post by scouser73 on 2011-04-03
> **laugh1 said:**
> I have it installed and use this to run it:
wine ~/.wine/drive_c/Program\ Files/iTunes/iTunes.exe

and get this:
```
fixme:htmlhelp:HtmlHelpW HH case HH_INITIALIZE not handled.
fixme:dsalsa:IDsDriverBufferImpl_SetVolumePan (0x163920,0x163820): stub
fixme:ddraw:DirectDrawEnumerateExA flags 0x00000001 not handled
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  158 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  1042
  Current serial number in output stream:  1042

```

Help?

iTunes will never work on Ubuntu even if you try to run it using WINE, sorry but there's no way around it.

---

### Post by d3v1150m471c on 2011-04-03
> **laugh1 said:**
> I can use those with an ipod?
they work like a charm. i use both.

---

### Post by steveneddy on 2011-04-03
We run iTunes in a VM (VirtualBox) with Windows 7.

It is a little slow - and you need to set permissions and perform a few tweaks - but it does work well.

Also you probably want your Ubuntu box to have about 4 Gig of RAM to accommodate the VM and Windows.

---

