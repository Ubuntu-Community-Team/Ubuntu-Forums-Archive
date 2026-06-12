---
title: "lsusb"
date: 2011-09-21
forum: General Help
---

### Post by salehahmed985 on 2011-09-21
in terminal, there is no result for lsusb. what can i do now?
i'm using zorin 5.

---

### Post by WorMzy on 2011-09-21
> **salehahmed985 said:**
> in terminal, there is no result for lsusb. what can i do now?
i'm using zorin 5.

No idea, what are your trying to do?

What is Zorin?

---

### Post by salehahmed985 on 2011-09-21
i'm using linux zorin 5. and in terminal when i enter lsusb command it shows nothing.. what can i do now?

---

### Post by WorMzy on 2011-09-21
Never heard of Zorin, and the website appears to be down. It's apparently built using Ubuntu though, so try running this is a terminal:

```
sudo apt-get install usbutils
```

Or else use whatever package manager Zorin has provided you to install the aforementioned package.

After it's installed, you should be able to use lsusb.

---

### Post by Loevborg on 2011-09-21
Try running `sudo lsusb` instead. On Ubuntu, as far as I know, `lsusb` should be enought, but maybe it's different on other systems.

---

### Post by salehahmed985 on 2011-09-21
usbuitls is installed...

---

### Post by salehahmed985 on 2011-09-21
sudo lsusb also failed!

---

### Post by WorMzy on 2011-09-21
> **salehahmed985 said:**
> usbuitls is installed...

So is your problem, not that you don't have the lsusb application, but that it doesn't generate any output?

---

### Post by patryk77 on 2011-09-21
sudo updatedb
locate lsusb

Maybe it's installed but not in $PATH

If you find it, run
echo $PATH

---

### Post by salehahmed985 on 2011-09-21
> **WorMzy said:**
> So is your problem, not that you don't have the lsusb application, but that it doesn't generate any output?

no output...

---

### Post by decoherence on 2011-09-21
Perhaps for some reason lsusb doesn't think you have a usb bus? What kind of hardware is it? Does lshw work, because that output may be useful.

---

