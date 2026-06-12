---
title: "sudo: @sed: command not found"
date: 2011-08-16
forum: General Help
---

### Post by miivers on 2011-08-16
Hello
New Ubuntu user here. I am having some problems getting "sed" to work when i run "make install" (for openni driver). The error I get is shown below:

```

sudo: @sed: command not found

```The strange part is if I type "sed" and hit enter i get the help message to sed. So my question is. Why does it not find sed when i run make install?

Michael

---

### Post by nothingspecial on 2011-08-16
Post a link to the instructions you are following.

---

### Post by AlphaLexman on 2011-08-16
Please post the complete command that produces the error.

---

### Post by miivers on 2011-08-16
I am following this guide:
[http://www.ros.org/wiki/openni_kinect](http://www.ros.org/wiki/openni_kinect)

Here is a dump from the terminal:

```

* Creating tar......
* Redist OpenNi Ended.   !!
/opt/ros/diamondback/stacks/openni_kinect/openni/drivers/openni
touch installed
make[1]: Leaving directory `/opt/ros/diamondback/stacks/openni_kinect/openni/drivers/openni'
sudo mkdir -p /usr/include/openni \
                                /etc/openni \
                                /usr/share/openni/doc \
                                /usr/share/openni/samples \
                                /usr/lib/pkgconfig
sudo cp -f ./openni/build/openni/Platform/Linux-x86/Redist/Samples/Config/* /etc/openni/
sudo cp -f ./openni/build/openni/Platform/Linux-x86/Redist/Lib/*.so /usr/lib/
sudo cp -r ./openni/build/openni/Platform/Linux-x86/Redist/Include/* /usr/include/openni/
sudo cp -f ./openni/build/openni/Platform/Linux-x86/Redist/Bin/* /usr/bin/
sudo cp -f ./openni/build/openni/Platform/Linux-x86/Redist/Documentation/html/* /usr/share/openni/doc/
sudo cp -f ./openni/build/openni/Platform/Linux-x86/Redist/Samples/Bin/Release/Sample-* /usr/share/openni/samples/
sudo cp -f ./openni/build/openni/Platform/Linux-x86/Redist/Samples/Bin/Release/NiViewer /usr/share/openni/samples/
sudo @sed s/__VERSION__/1.3.2.1~maverick/ ./CONTROL/openni.pc > /usr/lib/pkgconfig/openni-dev.pc
sudo: @sed: command not found
make: *** [install_openni] Error 1


```

---

### Post by miivers on 2011-08-16
> **AlphaLexman said:**
> Please post the complete command that produces the error.

The command i am running is:
```

miivers@ubuntu:/opt/ros/diamondback/stacks/openni_kinect/openni/drivers$ sudo make install

```

---

### Post by nothingspecial on 2011-08-16
Follow the ubuntu installation link


[http://www.ros.org/wiki/diamondback/Installation/Ubuntu](http://www.ros.org/wiki/diamondback/Installation/Ubuntu)

```
sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu natty main" > /etc/apt/sources.list.d/ros-latest.list'
wget http://packages.ros.org/ros.key -O - | sudo apt-key add -
sudo apt-get update
sudo apt-get install ros-diamondback-desktop-full
```

[SIZE="2"][COLOR="Red"]Copy and paste[/COLOR][/SIZE] one line at a time. If you get the first one wrong you'll mess things up.

---

### Post by WorMzy on 2011-08-16
@sed =/= sed

Remove the @.

---

