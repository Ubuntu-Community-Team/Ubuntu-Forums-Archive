---
title: "&quot;Restoring previously installed packages... 86%&quot;"
date: 2011-06-25
forum: General Help
---

### Post by skyclaw on 2011-06-25
In the midst of an epic, hours-long saga of attempting to reinstall Kubuntu 11.04 and get my GRUB menu back in order to dual boot with Windows 7 (I accidentally lost the rambling thread I previously typed, so I'm not going to even tell the back story unless prompted), my installation progress bar seems to be sitting at a solid 86%, reading "Restoring previously installed packages...", something I've never seen before. It's sat there for two hours, not moving a pixel. Is there anything I can do at this point? I've been up for hours trying to do this, and I'm about ready to give up on Kubuntu and even seeing my Windows system again... help?

---

### Post by skyclaw on 2011-06-26
OK, wonderful, it seems to have finished installing, but my GRUB menu is still gone, and I get this error:

```
error: unknown file system
grub rescue>
```
 
Now what?

---

### Post by iclestu on 2011-06-26
> **skyclaw said:**
> OK, wonderful, it seems to have finished installing, but my GRUB menu is still gone, and I get this error:

```
error: unknown file system
grub rescue>
```Now what?

have a look at th troubleshooting guide here:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

what happens if you do 

```
ls
```

at that grub prompt?

---

### Post by skyclaw on 2011-06-26
It gives me the following:
 
```
(hd0) (hd0,msdos5) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)
```
 
I get the feeling that this may be bad...

---

### Post by skyclaw on 2011-07-03
Excuse me for not posting earlier, but I did solve the problem. My problem was that I kept trying to reinstall GRUB to the Kubuntu partition like an idiot, as opposed to just installing it to the HDD as a whole. I think perhaps a separate boot partition might do me a lot of good, but I'm not about to monkey with that. I've already had enough trouble with that.

---

