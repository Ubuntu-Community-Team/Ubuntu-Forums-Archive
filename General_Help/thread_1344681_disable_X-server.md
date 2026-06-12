---
title: "disable X-server"
date: 2009-12-03
forum: General Help
---

### Post by Telhma on 2009-12-03
Hello all

I try to install my NVIDIA driver. (i did it before with success, but for some reason the trick don't work annymore)

Okej, i need to disable my x server. what i do is this:

1- Logout from ubuntu to the login-screen
2- Press CTRL+ALT+F1
3- Type in User-name and password to login
4- Go to the directory with the drivers
5- type: sudo sh NVIDIA-............. .run
6- Password again

But then it still say i am running the X-server

So, where i forgot something??

Thanks in advance.

---

### Post by jegerjensen on 2009-12-03
I don't have any experience with nvidia drivers, so I just assume that you know what you are doing.  To stop the X-server you can issue the command
```
[...]$sudo /etc/init.d/gdm stop
```

Start it again with 
```
[...]$sudo /etc/init.d/gdm start
```

---

### Post by Telhma on 2009-12-03
True, thanks, i remember that command, i think it will work now.

thanks

---

### Post by 3rdalbum on 2009-12-03
Firstly:

Nvidia drivers for all but the absolute newest models are available in the Hardware Drivers program. If they are not listed there, then you may need to refresh your package list.

Secondly: If you have a very new card that's not supported with the stock Nvidia driver (for instance, the GT210) and that's why you're installing the latest Nvidia driver, then you need to kill X.

When you switch to the virtual terminal with Control-Alt-F1, X is still running in the background. You can kill it by typing:

```
sudo killall gdm
```

This might have changed in Karmic; you might need to use this instead:

```
sudo service gdm stop
```

NOTE: I highly suggest finding a good recent HOWTO for this, because if you install the driver manually you will need to reinstall it every time you upgrade the kernel. If you don't want to have to do this, then use the version in the Hardware Drivers program, or follow a HOWTO that shows you how to register the driver with the DKMS system. DKMS will recompile all kernel modules when you upgrade the kernel.

---

