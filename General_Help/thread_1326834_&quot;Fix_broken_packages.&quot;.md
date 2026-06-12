---
title: "&quot;Fix broken packages.&quot;"
date: 2009-11-14
forum: General Help
---

### Post by iEthan on 2009-11-14
I go to install the MP3 plugin and I get an error message saying I need to "Fix broken packages" before installing. How do I get by this?

---

### Post by williejones on 2009-11-14
I have had this happen to me, and I reloaded the operating system.  There is probably a way to fix your problem, but I has no data to have to restore.  If you do, wait for some more advice.

---

### Post by iEthan on 2009-11-15
You mean reinstall the operating system? I don't want to do that...

---

### Post by Soul-Sing on 2009-11-15
> **iEthan said:**
> You mean reinstall the operating system? I don't want to do that...

could you please copy-paste the [COLOR="Red"]exact[/COLOR] error?

---

### Post by emigrant on 2009-11-15
Go to synaptic>filters>fix broken packages

---

### Post by mr clark25 on 2009-11-15
reinstalling the operating system is what e means...

if you just got done with installing Ubuntu not to long ago, and havent customized it much, then i would reinstall it, like williejones said.

---

### Post by MaxIBoy on 2009-11-15
> **emigrant said:**
> Go to synaptic>filters>fix broken packages
Yes, do this.



All who suggest reinstalling: shame on you! Seriously, this is NOT a big deal problem, you ought not to give up and have him reinstall for something so minor!

Also, if you dont actually know how to solve his problem, don't answer the thread!

---

### Post by nexes128 on 2009-11-15
If fix broken packages doesn't work, when you do apt-get it should tell you what packages are broken then just do 
```

dpkg deinstall *packagename*

```

You can then try and reinstall the packages via apt-get

---

### Post by iEthan on 2009-11-15
@leoquant: See attachment.
@emigrant: I did that: did absolutely nothing.
@nexes128: The problem is, I don't know which packages it is. I can install packages--I just can't install media plugins.

Thanks for all your help, guys.

---

### Post by emigrant on 2009-11-15
@iEthan,
what does your this screen shows?

//see the attachement

---

### Post by iEthan on 2009-11-16
@emigrant: Yes, but I don't have any content (no packages listed).

---

### Post by mc4man on 2009-11-16
Try installing one from the terminal, it may produce some clue as to what's preventing the install
```

sudo apt-get install gstreamer0.10-ffmpeg
```

---

### Post by iEthan on 2009-11-16
> **mc4man said:**
> Try installing one from the terminal, it may produce some clue as to what's preventing the install
```

sudo apt-get install gstreamer0.10-ffmpeg
```

That worked. Don't ask me how, but it did.

Thanks everyone!

---

### Post by emigrant on 2009-11-16
plz go to **thread tools** and mark the thread as **[SOLVED]**

---

