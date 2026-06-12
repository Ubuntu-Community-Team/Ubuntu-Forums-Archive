---
title: "Cannot install any packages -- &quot;Requested packages are already installed&quot;"
date: 2009-10-29
forum: General Help
---

### Post by bakaeigo on 2009-10-29
I cannot install any new packages in my fresh Kubuntu 9.10 install. The KDE Firefox installer brings up a message that says "Requested packages are already installed." Attempting to install anything from the terminal results in a "E: Package _________ has no installation candidate" error.

What's going on?

---

### Post by bakaeigo on 2009-10-30
*bump*

---

### Post by srbaldomero on 2009-10-30
I'm having the same problem.

PS: I din't understand last answer

---

### Post by drumkitcat on 2009-10-30
I just installed Kubuntu 9.10 last night on my Toshiba Satellite A40 laptop.  did a clean install reformatting the drive, etc.

Everything worked great right away - even wireless connection!

I did get that same problem though trying to install Firefox - it said the requested packages are already installed - but I couldn't find it anywhere else.

I haven't used Kubuntu before - last time I was using Linux was Ubuntu's Edgy Eft.  So, I'm still trying to get used to the new environment.  So far I really like it, but need to learn more about how to use everything.

---

### Post by WarmonkeyUK on 2009-10-30
This happened to me also. It's because the package lists need to be updated before you can successfully run the installer. Bring up Konsole, and type ```
sudo apt-get update
```, followed by your password to run the update. Then the Firefox installer should work fine.

---

### Post by andrewharvey on 2009-11-20
i had to remove the kubuntu-firefox-installer package. maybe this is because I had already run firefox in GNOME prior to starting it up in KDE, i'm not sure.

---

### Post by kpedrox on 2009-11-27
> **WarmonkeyUK said:**
> This happened to me also. It's because the package lists need to be updated before you can successfully run the installer. Bring up Konsole, and type ```
sudo apt-get update
```, followed by your password to run the update. Then the Firefox installer should work fine.


Tried this. Seemed to go ok but no joy. Still says already installed... but doesn't appear to be. I'm new to (K)ubuntu too, so maybe I'm missing something simple...

---

### Post by wojox on 2009-11-27
So what is it your trying to install, that's already installed?

---

### Post by kpedrox on 2009-11-27
just firefox...
...have installed kubuntu today (via wubi via win xp). 
Firefox appears in the K>Applications>Internet menu, but only as "Mozilla Firefox Browser Installer". So I go with this, enter the password as requested... get back "requested packages are already installed"

---

### Post by snowpine on 2009-11-27
What happens when you open a terminal and type

```
firefox
```

?

---

### Post by kpedrox on 2009-11-27
typing "firefox" in a command window:

i get:-

the program 'firefox' can be found in the following packages:
 | firefox-3.5
 | firefox-3.0
Try: sudo apt get install <selected package>
firefox: command not found


so based on the above, i've tried entering:
sudo apt-get install firefox-3.5

I get back:

reading package lists...Done
building dependency tree
reading state info...Done
E: Couldn't find package firefox-3.5

---

### Post by kpedrox on 2009-11-27
any ideas? or am i stuck with windows?

---

### Post by mkvnmtr on 2009-11-27
You might try to use your package manager to do the install. If Firefox does not show you will need to enable the repositories that it is in.


Just had a thought. Do you have internet  to reach the repositories?

---

### Post by oldos2er on 2009-11-27
> **kpedrox said:**
> any ideas? or am i stuck with windows?

 Have you run **sudo apt-get update** lately?

---

### Post by kajman on 2010-01-06
Had the same problem as above, but in my case ```
sudo apt-get update
``` was good solution. After that installer worked just fine.

---

### Post by naptime on 2010-02-11
I had the same problem, ran sudo apt-get update and that seemed to fix it.

---

