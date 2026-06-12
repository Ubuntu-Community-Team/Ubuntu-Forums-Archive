---
title: "Alien Help"
date: 2009-11-16
forum: General Help
---

### Post by mtate5000 on 2009-11-16
I installed alien from synaptic (karmic) and even alien gui from somewhere else, but I can't tell whether or not the gui or command line is converting. I have no idea where the destination of the new (deb) pkg is. Nor do i have any idea on how to specify. Ive never used alien before and the man pages ive found only give me the commands to exe the conversion. I love to just down load the deb but cant find it. Can anyone help?

---

### Post by blazemore on 2009-11-16
just run
```
sudo alien -d foo.rpm
```
that will give you foo.deb in the same directory, which you can install in the usual way.

---

### Post by wojox on 2009-11-16
Or install directly:

```
sudo alien -i package_file.rpm
```

---

### Post by mtate5000 on 2009-11-16
Thanks guys. I had the proper command, but it wasn't working for some reason. Im not sure what the problem was (is), but I extracted the rpm, then compressed it to .tar.gz, then I used alien to generate the deb. The package was for the compiz unsupported plugins (0.8.4), that was not included in the repos for karmic. My options were to compile the source or convert rpm. Im not comfortable compiling yet, as I'm still quite new to life beyond the micro$oft regime, so I opted to install alien and give it a whirl. Thanks for responding.

---

