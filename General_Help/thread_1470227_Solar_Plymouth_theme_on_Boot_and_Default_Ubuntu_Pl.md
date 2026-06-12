---
title: "Solar Plymouth theme on Boot and Default Ubuntu Plymouth on shutdown"
date: 2010-05-02
forum: General Help
---

### Post by sonicroxs on 2010-05-02
Hey,
As my title says, when I boot my PC the Solar Plymouth theme shows, and when I shut down the PC, I get the default Ubuntu Plymouth theme. I am using Lucid Lynx. Any help?

---

### Post by sonicroxs on 2010-05-03
Epic fail bump.

---

### Post by GSF1200S on 2010-05-03
You can go into Synaptic and remove the theme you dont want. So, assuming you dont want the default theme, you would remove the package named:
```
plymouth-theme-ubuntu-logo
```

Alternatively, you can do this from the command line:
```
sudo apt-get remove plymouth-theme-ubuntu-logo
```

---

### Post by Elfy on 2010-05-03
If you change plymouth themes I have run this as well

```
sudo update-alternatives --config default.plymouth
```

---

### Post by abumaia on 2010-05-06
I am interested in this topic, only for the opposite reason of the OP.  I have installed a new Plymouth theme, but I only want it on boot, and nothing on shutdown.  Is this possible?

---

### Post by prams on 2010-05-06
> **sonicroxs said:**
> Hey,
As my title says, when I boot my PC the Solar Plymouth theme shows, and when I shut down the PC, I get the default Ubuntu Plymouth theme. I am using Lucid Lynx. Any help?
the reverse happens to me

---

### Post by drymnfr on 2010-09-09
For different themes on Boot and Shutdown, I did the following:

For Boot - Step One) 
Selected one of the available themes.
```
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u

```

For Shutdown - Step Two) 
Selected a different theme.
```
sudo update-alternatives --config default.plymouth
```

---

