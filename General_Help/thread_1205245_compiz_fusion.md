---
title: "compiz fusion"
date: 2009-07-05
forum: General Help
---

### Post by shaullx on 2009-07-05
Why do i need to enable compiz fusion each time i start ubuntu?
any solution?

---

### Post by izizzle on 2009-07-05
make sure it is enabled in autostarted applications.

---

### Post by shaullx on 2009-07-05
> **izizzle said:**
> make sure it is enabled in autostarted applications.

how do i do that?

---

### Post by shaullx on 2009-07-05
ok i looked into it and it's not on the startup apps list
how to add it there?

---

### Post by aesis05401 on 2009-07-05
> **shaullx said:**
> ok i looked into it and it's not on the startup apps list
how to add it there?

Hold up a minute.. what do you mean you have to start it every time?  Can you tell me the steps you need to go through?  There are compiz applets that dock on your system tray when started to access settings and such...

When you open System/Preferences/Appearance there should be an 'Appearance Preferences' window that opens with some tabs across the top.  Go to the 'Visual Effects' tab and click 'Preferences' button.

A new window should pop up with the name of your effects package along the top title bar - mine says 'Simple CompizConfig Settings Manager.'

What happens on yours?

---

### Post by shaullx on 2009-07-05
> **aesis05401 said:**
> Hold up a minute.. what do you mean you have to start it every time?  Can you tell me the steps you need to go through?  There are compiz applets that dock on your system tray when started to access settings and such...

When you open System/Preferences/Appearance there should be an 'Appearance Preferences' window that opens with some tabs across the top.  Go to the 'Visual Effects' tab and click 'Preferences' button.

A new window should pop up with the name of your effects package along the top title bar - mine says 'Simple CompizConfig Settings Manager.'

What happens on yours?

dont have "Preferences" button there
and i can't enable dekstop effects there only in compiz settings manager
each time i start ubuntu i need to start "Compiz fusion icon" 
and right click it and click on "Reload window manager"

---

### Post by shaullx on 2009-07-05
bump?

---

### Post by aesis05401 on 2009-07-05
> **shaullx said:**
> bump?

After installation did you run: 
```

compiz --replace

```

You may need to do the same with gtk-window-decorator.

Edit: the '--replace' part is different then reloading the window manager, and should inform metacity that compiz is taking over.  The window decorator you choose will also need to be done the same way - either gtk-window-decorator or emerald I think.

---

### Post by sdowney717 on 2009-07-05
when I did this I ran 
"fusion-icon" in startup.
I can no longer do compiz because I have been abandoned by ATI on my x1300

---

### Post by aesis05401 on 2009-07-05
> **sdowney717 said:**
> when I did this I ran 
"fusion-icon" in startup.
I can no longer do compiz because I have been abandoned by ATI on my x1300

After hearing the other suggestion about startup I checked my list.. I run compiz and have no entry in startup applications.  It just runs.

---

