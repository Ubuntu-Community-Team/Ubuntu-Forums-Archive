---
title: "View hard drive sectors / package or command"
date: 2012-02-08
forum: General Help
---

### Post by ade234uk on 2012-02-08
I am in the process of wiping about 5 hard drives using shred. Is there a package / software available or a command I can use in the terminal that can give me some sort of graphical representation of the hard drive sectors on screen, and will show me if it has been cleaned properly.

---

### Post by Herman on 2012-02-08
:) Well you could try running the dd command on the entire disk and not giving it any output file to write to. 
That will cause the raw data to be read off the disk and the output to be shown in your terminal screen. 
It's rather an interesting/entertaining trick the first time you see it. I don't think it can do any harm, I have tested it myself a few times. I'm not really sure if it will be exactly what you're looking for though. Let me know how you get along.
```
sudo dd if=/dev/sdx
```Where: x is to be replaced with the letter representing the disc number for the disk you want to have a look at.

It will take some time to complete, I don't have the patience to wait that long and normally just close the terminal window on it, ignoring the usual warnings about a program still running.

---

### Post by Paqman on 2012-02-08
> **ade234uk said:**
> and will show me if it has been cleaned properly.

Best way to ascertain that would be to run photorec on the drive and see if any files are recovered. I think you'll find that a single pass over the entire drive will render nothing recoverable. Don't waste your time doing 36-pass Gutmann wipes or similar. If you're super-paranoid do two passes, but one will do the job perfectly well if you're zeroing the whole drive.

---

### Post by ade234uk on 2012-02-08
Ok will look in to photorec many thanks Paqnan. And many thanks to Herman for the original info.

---

