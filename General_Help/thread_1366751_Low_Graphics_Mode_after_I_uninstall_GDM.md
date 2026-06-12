---
title: "Low Graphics Mode after I uninstall GDM"
date: 2009-12-28
forum: General Help
---

### Post by CynicalPsycho on 2009-12-28
I recently decided I was gonna cut some of the crap out of my Ubuntu 9.10 installation.
So one of the first things I decided I was gonna do was remove GDM.
The only problem is once I did that Ubuntu throws up this ugly prompt asking if I wanted to go to low graphics mode, terminal, or 2 other options.

I was wondering if anyone knows how to make this ugly box go away, and instead boot directly into the terminal.

---

### Post by synapsys on 2009-12-28
I believe you want to 

```
sudo update-rc.d -f gdm remove
```

That's how I used to do it, somebody correct me if I'm wrong....

---

### Post by CynicalPsycho on 2009-12-28
> **synapsys said:**
> I believe you want to 

```
sudo update-rc.d -f gdm remove
```

That's how I used to do it, somebody correct me if I'm wrong....
Yeah, I saw this command when I searched for a solution earlier... but this one doesn't seem to do jack for me... think it could be because i'm using a newer version maybe?

---

### Post by synapsys on 2009-12-28
> **CynicalPsycho said:**
> Yeah, I saw this command when I searched for a solution earlier... but this one doesn't seem to do jack for me... think it could be because i'm using a newer version maybe?

Must be.... Try this tutorial I found....

[http://ubuntuguide.net/boot-into-consolecommand-line-when-startup-ubuntu-9-10](http://ubuntuguide.net/boot-into-consolecommand-line-when-startup-ubuntu-9-10)

---

