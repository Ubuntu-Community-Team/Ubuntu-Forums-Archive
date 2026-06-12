---
title: "sudo/gksudo can't move file?"
date: 2009-12-13
forum: General Help
---

### Post by tesseract420 on 2009-12-13
Hi, I'm trying to install a font by copying it into the /usr/share/fonts folder.

When I tried to do this under a normal login, I got an error message saying "Permission Denied."

So I tried, "sudo Nautilus" in a text terminal, again, Permission denied.

I looked on the forums and found, "gksudo Nautilus" (since Nautilus is not a command line app) but again, permission denied.

So if I have root access under Nautilus, why can't I move a file? I know that Ubuntu disables root by default, but really...

---

### Post by Primefalcon on 2009-12-13
> **tesseract420 said:**
> Hi, I'm trying to install a font by copying it into the /usr/share/fonts folder.

When I tried to do this under a normal login, I got an error message saying "Permission Denied."

So I tried, "sudo Nautilus" in a text terminal, again, Permission denied.

I looked on the forums and found, "gksudo Nautilus" (since Nautilus is not a command line app) but again, permission denied.

So if I have root access under Nautilus, why can't I move a file? I know that Ubuntu disables root by default, but really...
open both directories using gksudo nautilus not just the one

---

### Post by NoaHall on 2009-12-13
```
gksudo nautilus
```

Try moving it using
```
sudo mv /home/USER/FILE /usr/share/fonts/
```

---

### Post by howefield on 2009-12-13
Open a terminal and navigate to where your font is, and type..

```
sudo cp tahoma.ttf /usr/share/fonts
``` 

where tahoma.ttf is the file name of the font you are trying to copy.

---

### Post by pbrane on 2009-12-13
You can also install fonts to your local ~/.fonts directory if you don't need them system wide.

---

