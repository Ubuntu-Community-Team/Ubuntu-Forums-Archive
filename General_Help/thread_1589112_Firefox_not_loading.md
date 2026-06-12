---
title: "Firefox not loading?"
date: 2010-10-05
forum: General Help
---

### Post by felinoel on 2010-10-05
I click the startup file for it to run and it starts up but then disapeers?
I tried the Ubuntu Software Center to remove then reinstall it but still the same problem? I would rather keep the bookmarks too if that could happen... any thoughts?

---

### Post by mikewhatever on 2010-10-05
What startup file are you talking about? Is is the Firefox icon in the panel? What's the output of the following command:
```
ps -A | grep firefox
```

---

### Post by felinoel on 2010-10-05
> **mikewhatever said:**
> What startup file are you talking about? Is is the Firefox icon in the panel? What's the output of the following command:
```
ps -A | grep firefox
```

It is the icon in the panel, the one in the menu, and I was planning on looking for the direct one, the one the shortcuts are shortcuts from but I don't know Ubuntu well enough I guess.

Speaking of not know Ubuntu too well... I assume I was to put that in the Terminal, upon doing so it just went to the next line and said nothing?

---

### Post by mikewhatever on 2010-10-05
OK, that means firefox is not already running, which is good. Try launching it from a Terminal window with the **firefox** command. That may provide a clue of what's wrong.

---

### Post by felinoel on 2010-10-05
> **mikewhatever said:**
> OK, that means firefox is not already running, which is good. Try launching it from a Terminal window with the **firefox** command. That may provide a clue of what's wrong.

(firefox-bin:6231): GLib-WARNING **: g_set_prgname() called multiple times

---

### Post by felinoel on 2010-10-05
This was probably caused by using the force quit button when it froze up

---

### Post by felinoel on 2010-10-06
.

---

### Post by felinoel on 2010-10-07
> **felinoel said:**
> .

.

---

### Post by lovinglinux on 2010-10-07
See Firefox [[COLOR="Sienna"]**General Troubleshooting Steps**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html) tutorial.

---

### Post by felinoel on 2010-10-09
The recent update fixed it

---

### Post by jakerz0 on 2010-11-08
I have the same problem here. Ive just upgraded to Karmic from 9.04 and now I can't launch Firefox from shortcut or the App menu. I still can launch it from command line just typing firefox with no extra arguments.
I have the last firefox version 3.6.12.

---

### Post by lovinglinux on 2010-11-08
> **jakerz0 said:**
> I have the same problem here. Ive just upgraded to Karmic from 9.04 and now I can't launch Firefox from shortcut or the App menu. I still can launch it from command line just typing firefox with no extra arguments.
I have the last firefox version 3.6.12.

Check if you have libmoon installed and remove it.

If that doesn't help, try to delete compatibility.ini and secmod.db files from your Firefox profiles.

---

### Post by jakerz0 on 2010-11-08
First, Synaptic tells me that I dont have libmoon intalled so I supoose I don't.
I removed these 2 files form my ~/firefox folder but it did not solve it. I see the same thing, it appears at the windows bar and says starting firefox... but suddenly it closes. 
When I launched by line command it started ok even with the last pages opened. And these 2 files were automatically recreated.

I should add that Firefox is ok in the guest account.

---

### Post by lovinglinux on 2010-11-08
> **jakerz0 said:**
> First, Synaptic tells me that I dont have libmoon intalled so I supoose I don't.
I removed these 2 files form my ~/firefox folder but it did not solve it. I see the same thing, it appears at the windows bar and says starting firefox... but suddenly it closes. 
When I launched by line command it started ok even with the last pages opened. And these 2 files were automatically recreated.

I should add that Firefox is ok in the guest account.

Start Firefox in safe-mode

```
firefox -safe-mode
```

If it works, then disable extensions trough the safe mode dialog and try to find which one is causing the problem.

---

### Post by jakerz0 on 2010-11-08
Solved!
I started in safe-mode and disabled only the add-ons for a test but nothing changed.

So I took other approach, I looked into the shortcut properties and the command field was: 
env LD_PRELOAD=/usr/lib/libGL.so.1 firefox %u

So I checked the guest account which is working and copied from there to just 'firefox %u' and it worked.
Now I just have to enable my add-ons back again. Thanks for the help.

---

### Post by lovinglinux on 2010-11-08
> **jakerz0 said:**
> Solved!
I started in safe-mode and disabled only the add-ons for a test but nothing changed.

So I took other approach, I looked into the shortcut properties and the command field was: 
env LD_PRELOAD=/usr/lib/libGL.so.1 firefox %u

So I checked the guest account which is working and copied from there to just 'firefox %u' and it worked.
Now I just have to enable my add-ons back again. Thanks for the help.

Good to know. Looks like you have used a workaround in the command that is not needed anymore.

---

