---
title: "Manually configure a program to look for &quot;/dev/dsp1&quot; instead of &quot;/dev/dsp&quot;?"
date: 2010-01-02
forum: General Help
---

### Post by johncr13 on 2010-01-02
Hi, thanks for reading this.

I have a guitar tuning program called gtkGuitune that fails to launch because it's looking for /dev/dsp which doesn't exist. It also fails to launch using "aoss gtkguitune" and I have alsa-oss. I know it will work if I can have it look for /dev/dsp1 instead because it does exist. Is there an easy way to point the program to that file instead?

---

### Post by falconindy on 2010-01-02
Create a symlink /dev/dsp that points to /dev/dsp1. However, this will need to be done every time you boot, as the /dev directory is mounted in RAM. You'll want to look into writing a udev rule to create the symlink for you when /dev/dsp is created.

---

### Post by johncr13 on 2010-01-02
Seems like a good solution. Thank you very much!:)

---

### Post by johncr13 on 2010-01-02
So I created a symbolic link as you suggested and the program works perfectly.
In the terminal I typed the following:
sudo ln -s /dev/dsp1 /dev/dsp

---

