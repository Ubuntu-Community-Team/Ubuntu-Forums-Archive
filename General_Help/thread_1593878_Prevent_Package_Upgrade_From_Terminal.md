---
title: "Prevent Package Upgrade From Terminal"
date: 2010-10-11
forum: General Help
---

### Post by Shadow21 on 2010-10-11
I know you're able to lock packages in the Synaptic Package Manager so they will now upgrade but how would I lock a package using the terminal?

---

### Post by JustinR on 2010-10-11
> **Shadow21 said:**
> I know you're able to lock packages in the Synaptic Package Manager so they will now upgrade but how would I lock a package using the terminal?

Hi. You could try using DPKG with the -G argument.

Assuming it works like this:
```

sudo dpkg -G PACKAGENAME

```
If that doesn't work then read up on this:
[http://manpages.ubuntu.com/manpages/maverick/en/man1/dpkg.1.html](http://manpages.ubuntu.com/manpages/maverick/en/man1/dpkg.1.html)

> 
**-G**     Don't install a package if a newer version  of  the  same
              package  is  already  installed.


---

### Post by Shadow21 on 2010-10-11
I don't think that would work because I'm trying to stop the nVidia drivers from updating because when I updated them last time it caused me a lot of problems and I had to downgrade the drivers to fix it.

---

### Post by JustinR on 2010-10-11
> **Shadow21 said:**
> I don't think that would work because I'm trying to stop the nVidia drivers from updating because when I updated them last time it caused me a lot of problems and I had to downgrade the drivers to fix it.

I think the command I posted above should 'blacklist' the nVidia package from upating.

---

### Post by Shadow21 on 2010-10-11
> **JustinR said:**
> I think the command I posted above should 'blacklist' the nVidia package from upating.

Ok, I'll try it.

I type in

```
sudo dpkg -G nvidia-driver
```

and I get

```
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

```

---

### Post by MohanAleatbi on 2011-10-26
for example, i want to prevent "moserial" from upgrade 

echo moserial hold | sudo dpkg --set-selections 

this works for me.

---

