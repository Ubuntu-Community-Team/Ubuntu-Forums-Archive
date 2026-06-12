---
title: "Auto Run Script After Boot &amp; Loggin"
date: 2012-06-24
forum: General Help
---

### Post by garyzw on 2012-06-24
I have a simple script I would like to run after the computer is booted and logged in.

This is what I have in the script--
```
#!/bin/bash
verse-dialog

```
It needs to run in Terminal after boot and log in. How would I do it?

---

### Post by davidvandoren on 2012-06-24
I am not sure what you want to do but to run a command in terminal.

```
gnome-terminal -x bash -c "[COLOR=Red]here your command that executes in the termina[/COLOR]"
```

Go to system preferences **Start-up applications  **and add your command there.

---

### Post by garyzw on 2012-06-24
I want the script to run automatically after I log in

> **davidvandoren said:**
> I am not sure what you want to do but to run a command in terminal.

```
gnome-terminal -x bash -c "[COLOR=Red]here your command that executes in the termina[/COLOR]"
```

Go to system preferences **Start-up applications  **and add your command there.

---

### Post by garyzw on 2012-06-24
Thank you so much this worked!

> **davidvandoren said:**
> I am not sure what you want to do but to run a command in terminal.

```
gnome-terminal -x bash -c "[COLOR=Red]here your command that executes in the termina[/COLOR]"
```

Go to system preferences **Start-up applications  **and add your command there.

---

### Post by TVTrukChik on 2012-06-24
You should be able to go to System - Preferences - Startup Applications and add it there.  

Edit: Wow, I am slow!

---

### Post by garyzw on 2012-06-24
> **TVTrukChik said:**
> You should be able to go to System - Preferences - Startup Applications and add it there.

That is what I had but it did not run the script but opened the script in the text editor-- but adding 
```
gnome-terminal -x bash -c "here your command that executes in the terminal"
```
That caused it to open in the Terminal.

Thanks everyone for your help. ):P

---

