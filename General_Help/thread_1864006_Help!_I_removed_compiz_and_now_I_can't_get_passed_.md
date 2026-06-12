---
title: "Help! I removed compiz and now I can't get passed the login screen!"
date: 2011-10-18
forum: General Help
---

### Post by GoodHumperdink on 2011-10-18
Good evening all,

As the title states I was silly enough to totally remove Compiz from my Ubuntu x86_64 10.04.3 LTS system. I'm using the LiveCD that I used to install the system to type this.

Is there a way to reinstall Compiz with the LiveCD?

Any help is much appreciated.

---

### Post by decoherence on 2011-10-18
there might be but it might be easier to do it from the command line on the installed system.

once you're at the login screen, type CTRL ALT F1 to get a console and log in there.

From the console you can reinstall compiz (i'm guessing this is just 'apt-get install compiz' but don't know for sure)

Once that is done, either restart GDM or switch back to the login screen (CTRL F7) and reboot.

---

### Post by GoodHumperdink on 2011-10-18
> **decoherence said:**
> there might be but it might be easier to do it from the command line on the installed system.

once you're at the login screen, type CTRL ALT F1 to get a console and log in there.

From the console you can reinstall compiz (i'm guessing this is just 'apt-get install compiz' but don't know for sure)

Once that is done, either restart GDM or switch back to the login screen (CTRL F7) and reboot.

Thanks man, I'll try it now.

---

### Post by GoodHumperdink on 2011-10-18
I didn't work, but I think that's because I uninstalled a couple of other things that had "compiz" in their name.

---

### Post by ubu_dynamite on 2011-10-18
Probably not compiz thats causing the login problem should work without it.

```
sudo apt-get install ubuntu-desktop
```
Should install all default packages again.

---

### Post by GoodHumperdink on 2011-10-18
> **ubu_dynamite said:**
> Probably not compiz thats causing the login problem should work without it.

```
sudo apt-get install ubuntu-desktop
```Should install all default packages again.

I'd say you're right. I just checked and I have all the other compiz packages. I'll try that out now and get back to you.

---

### Post by GoodHumperdink on 2011-10-18
> **ubu_dynamite said:**
> Probably not compiz thats causing the login problem should work without it.

```
sudo apt-get install ubuntu-desktop
```
Should install all default packages again.

Thank you so much bro :) Everything's back online. I owe you one.

---

