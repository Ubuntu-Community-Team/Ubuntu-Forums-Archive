---
title: "SCRIPT  send du --max-depth=1 to zenity"
date: 2010-06-14
forum: General Help
---

### Post by skooter1121 on 2010-06-14
I'm trying to send the results of a command line $du --max-depth=1 to a zenity message box.

I want to create a .sh script that I can run as a Nautilus script that will open a zenity message box with a listing of sub-folders/sizes.

$DU with options, will provide the results in a terminal window, but I can't seem to get it into a zenity message box. I've tried gxmessage also, but no go.

Getting frustrated. Can anyone help?

-Skooter

---

### Post by DaithiF on 2010-06-14
Hi,
```
zenity --info --text "$(du --max-depth=1 .)"

```

---

### Post by skooter1121 on 2010-06-14
THANX.

I must have typed the same command 50 times !! Your's worked, mine still does not. Oh, well!

Again THANX

-SK

---

