---
title: "Force install Brother DCP7040 32-bit Driver on 10.10"
date: 2011-02-21
forum: General Help
---

### Post by wadedesk on 2011-02-21
I just installed Maverick 64-bit on my new Satellite AMD 4-core laptop.  I've run into an issue with the fact that Brother does not have a 64-bit driver for my Multi-Function Laser printer.  They recommend force installing the 32-bit driver.  I have made sure that all the 32-bit library and all the folders exist per Brothers instructions.  However, I'm confused on what command I need to type in the terminal window to actually do the install.  Can someone recommend the proper command to force install the 32-bit driver?  Or should I download the source code and compile?  I don't know the proper method for compiling a 64-bit driver either.  Thanks in advance for any help you can offer (I need very specific instructions).

---

### Post by 3Miro on 2011-02-21
> **wadedesk said:**
> I just installed Maverick 64-bit on my new Satellite AMD 4-core laptop.  I've run into an issue with the fact that Brother does not have a 64-bit driver for my Multi-Function Laser printer.  They recommend force installing the 32-bit driver.  I have made sure that all the 32-bit library and all the folders exist per Brothers instructions.  However, I'm confused on what command I need to type in the terminal window to actually do the install.  Can someone recommend the proper command to force install the 32-bit driver?  Or should I download the source code and compile?  I don't know the proper method for compiling a 64-bit driver either.  Thanks in advance for any help you can offer (I need very specific instructions).

What kind of file do you have? If it is a .deb file, then you have to open the terminal (Apps -> Access -> Terminal), go into the folder where the file is (for example "cd Downloads") and then use the command:

```
sudo dpkg -i --force-architecture filename.deb
```

---

### Post by wadedesk on 2011-02-21
That is exactly what I needed to know.  The driver is installed and working great!  Thanks so much.

---

### Post by 3Miro on 2011-02-21
> **wadedesk said:**
> That is exactly what I needed to know.  The driver is installed and working great!  Thanks so much.

Good news. If you have no more questions, please mark the thread as "solved".

---

