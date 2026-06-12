---
title: "Customizing 9.04 Kernel"
date: 2009-09-12
forum: General Help
---

### Post by Zeratul021 on 2009-09-12
Hi,

I would like to ask about customizing the default Ubuntu/Kubuntu kernel.
What I want is the basic kernel from ditro but i want to put XFS and some other things right inside it. What's the best way to do it during installation process like in debian?

And if not when installing, how to run make config so that all options from current system will be checked so I accidentally won't miss out something.

Thanks & regards,

Marek

---

### Post by TheExplorer on 2009-09-12
First you should install linux-source package like this:
```
sudo apt-get install linux-source
```
Install it:
```
cd /usr/src
sudo tar xvpf linux-source-2.6.2x.tar.bz2
cd linux-source-2.6.2x
```
Copy the old config */boot/config-2.6.2x-19-generic* here */usr/src/linux-source-2.6.2x/.config*
After that you can **make menuconfig**. But you should have all the necessary packages installed:
```
sudo apt-get install build-essential ncurses-dev fakeroot
```
After configuring you need the kernel package for the compilation:
```
sudo apt-get install kernel-package
```
Then compile it.

But please DO NOT use these. I mentioned only the general process as I've never done it actually. PLEASE USE Google for this. ('*oldconfig*' or something is the keyword).

Good luck!

---

### Post by hal10000 on 2009-09-12
1.)
```

sudo apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev wget libncurses5 libncurses5-dev

```
2.)```

cd /usr/src
sudo -s
tar xvpf linux-source-2.6.2x.tar.bz2
rm -rf linux && sudo ln -s linux-source-2.6.2x linux
cd /usr/src/linux
mv .config .config.orig
cp /boot/config-$(uname -r) /usr/src/linux/.config
make oldconfig

```
3.)
run [COLOR="Red"]make xconfig[/COLOR] and do the changes you need (use the search to find your things) but read carefully the help hints
Save the file when you are ready.

4.)
```

make-kpkg clean
CONCURRENCY_LEVEL=3 make-kpkg --initrd --append-to-version=-mykernel kernel_image kernel_headers modules_image

```
Now go to the cinema or brew some cups of coffee, because you'll have to wait until it's compiled, this may last some hours (1-3 hours depending on your machine's power)

5.)
After compiling ends with no errors:
```

cd /usr/src
dpkg -i linux*2.6.30*.deb

```
IMPORTANT: IF YOU HAVE AN NVIDIA OR ATI GRAPHICS CARD, YOU MAY HAVE TO REINSTALL THE DRIVERS FOR IT.

6.)
reboot

7.)
have fun


This is a short description of The Master Kernel Thread: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158) with the exception that you install the current ubuntu source instead of the kernel sources from kernel.org

---

### Post by Zeratul021 on 2009-09-12
Thank you both,

I don't worry about the time i'll set the concurrency level to 8 or 9.

I'll report how it went.

Regards,

Marek

---

