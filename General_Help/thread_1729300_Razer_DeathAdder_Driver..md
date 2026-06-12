---
title: "Razer DeathAdder Driver."
date: 2011-04-14
forum: General Help
---

### Post by myralfa on 2011-04-14
Are there any drivers for this mouse that actually work?
I've tried downloading some third-party drivers from the net but I couldn't managed to install any of them.
What I really want to, is the GUI or anything that let me assign special keys to the side buttons of the mouse.

---

### Post by WorMzy on 2011-04-14
There's the [razercfg tool]("http://bu3sch.de/cms/index.php/razer-nextgen-config-tool").

Works for my Lachesis.

Edit: works as in recognises my device and lets me modify the DPI/LEDs. I can't assign functions to buttons (yet). Apparently it works for DeathAdders.

---

### Post by myralfa on 2011-04-15
Can't install it.
I'm getting this error:
```

CMake Error at CMakeLists.txt:18 (message):
  Could not find library "libusb-1.0" with header libusb.h
Call Stack (most recent call first):
  CMakeLists.txt:23 (check_lib)


CMake Error: The following variables are used in this project, but they are set to NOTFOUND.
Please set them or make sure they are set and tested correctly in the CMake files:
LIBUSB_INCLUDE_PATH
   used as include directory in directory /home/adrian/Downloads/razercfg-0.14

-- Configuring incomplete, errors occurred!

```

---

### Post by WorMzy on 2011-04-15
Try installing the libusb-1.0-0-dev package, then try again. Also, check on Launchpad to see if there's any debs available.

---

### Post by myralfa on 2011-04-15
After installing the libusb-1.0-0-dev package, the error changed:
```

CMake Error at CMakeLists.txt:18 (message):
  Could not find library "libusb-1.0" with header libusb.h
Call Stack (most recent call first):
  CMakeLists.txt:23 (check_lib)


-- Configuring incomplete, errors occurred!

```

---

### Post by WorMzy on 2011-04-16
Strange, that package should contain libusb.h, and should put it in /usr/include/libusb-1.0, which is where cmake should be looking for it.

does
```
sudo updatedb && locate libusb.h
```

return "/usr/include/libusb-1.0/libusb.h"?

If not, make sure you definitely installed the libusb-1.0-0-dev package, and not libusb-1.0-0 (which you shouldn't need, but you could try installing it anyway).

---

### Post by myralfa on 2011-04-18
Indeed, it returns that.
What's failing then?

---

### Post by WorMzy on 2011-04-18
No idea.

You can check that '/home/adrian/Downloads/razercfg-0.14/scripts/cmake.global' has the right path set for libusb.h, but unless you manually modified it, it should do. Look on line 20, it should read

```
	PATHS "/usr/include/libusb" "/usr/include/libusb-1.0"
```

---

### Post by myralfa on 2011-04-18
It does says that.
It seems easier to ask Razer to make drivers for Ubuntu :(

---

### Post by WorMzy on 2011-04-18
You'll be lucky if they listen. :P

I think I've discovered the problem. When CMake failed the first time, it wrote a CMakeCache.txt file which is stopping CMake from trying to find the libusb.h file. Remove this text file (and optionally the CMakeFiles directory), then run CMake again.

---

### Post by myralfa on 2011-04-18
Love you bro, problem solved.
Is there a +rep button on this forum or something? :P

---

### Post by WorMzy on 2011-04-18
Haha, no, but the thought is appreciated. :)

Hopefully this app will do everything you need.

---

### Post by myralfa on 2011-04-19
Luckily a I've encountered a new problem.
After successfully entering:
```

cmake .
make

```
The readme tells me to insert:
```

sudo -i
make install

```
But when I do this, the following error appears:
```

root@Adrian:~# make install
make: *** No rule to make target `install'.  Stop.

```

---

### Post by WorMzy on 2011-04-19
That's because sudo -i gives you a root shell, which starts in /root, you'll need to cd back to the right directory.

```
cd /home/adrian/Downloads/razercfg-0.14
```

alternatively, instead of using sudo -i, just use

```
sudo make install
```

---

### Post by myralfa on 2011-04-19
Great! Thanks.
The file is now installed.
Sadly there side buttons can't be configured.

---

### Post by WorMzy on 2011-04-20
Oh. I thought since it says that it says it's stable for DeathAdders, button mapping would work. Oh well, it still seems to be under active development; 0.14 was just released two weeks ago, so maybe the button configuration is coming and all that hassle compiling it won't be completely in vain.

For now I guess you're going to have to either live with it, or find another solution.

---

### Post by myralfa on 2011-04-20
Just going to wait, it really wasn't a matter of life or death.

---

