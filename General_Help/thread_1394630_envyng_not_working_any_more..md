---
title: "envyng not working any more."
date: 2010-01-30
forum: General Help
---

### Post by markp1989 on 2010-01-30
i was testing power savings i could use by using onboard gpu on my htpc, so i uninstalled the nvidia driver, and removed the card.

used the pc with out the card, but some programs i needed couldnt deal with the punyness of the intergrated gpu, so i put it back in. 

no trying to instll the nvidia driver, i get an error:

>  +-----------------------------------------------------------+
 |    EnvyNG Menu                                            |
 |                                                           |
 |    1 - Install the NVIDIA driver                          |
 |                                                           |
 |    2 - Uninstall the NVIDIA driver                        |
 |                                                           |
 |    3 - Install the ATI driver                             |
 |                                                           |
 |    4 - Uninstall the ATI driver                           |
 |                                                           |
 |    5 - Restart the Xserver                                |
 |                                                           |
 |    6 - Restart your computer                              |
 |                                                           |
 |    7 - Exit                                               |
 |                                                           |
 |    NOTE: IF THE SCREEN TURNS BLACK, PLEASE TYPE ALT+F1    |
 +-----------------------------------------------------------+
Please select one of the activities displayed above and press ENTER:

1
 +----------------------------------------------------------------------------------------------------+
 | Number | Candidate Version                          | Installed Version | Compatible | Recommended |
 |----------------------------------------------------------------------------------------------------|
 | 0      | 195.30-0ubuntu1~karmic~nvidiavdpauppa5     | -                 | +          | +           |
 |----------------------------------------------------------------------------------------------------|
 | 1      | 190.53-0ubuntu1~karmic~nvidiavdpauppa8     | -                 | +          | -           |
 |----------------------------------------------------------------------------------------------------|
 | 2      | 185.18.36-0ubuntu10~karmic~nvidiavdpauppa4 | -                 | +          | -           |
 |----------------------------------------------------------------------------------------------------|
 | 3      | 173.14.20-0ubuntu5                         | -                 | +          | -           |
 |----------------------------------------------------------------------------------------------------|
 | 4      | 96.43.13-0ubuntu6                          | -                 | -          | -           |
 +----------------------------------------------------------------------------------------------------+
Please select the number corresponding to the desired driver and press ENTER 
(or type another number and press Enter to go back to the previous menu): 
0

Downloading the packages...
dpkg-exec: Running dpkg

Selecting previously deselected package nvidia-195-kernel-source.
(Reading database ... 96953 files and directories currently installed.)
Unpacking nvidia-195-kernel-source (from .../nvidia-195-kernel-source_195.30-0ubuntu1~karmic~nvidiavdpauppa5_amd64.deb) ...
nvidia-195-kernel-source: Installing nvidia-195-kernel-source

nvidia-195-kernel-source: Preparing nvidia-195-kernel-source

nvidia-195-kernel-source: Unpacking nvidia-195-kernel-source

Unpacking nvidia-glx-195 (from .../nvidia-glx-195_195.30-0ubuntu1~karmic~nvidiavdpauppa5_amd64.deb) ...
nvidia-195-kernel-source: Preparing to configure nvidia-195-kernel-source

dpkg: warning: obsolete option '--print-installation-architecture', please use '--print-architecture' instead.
nvidia-glx-195: Installing nvidia-glx-195

nvidia-glx-195: Preparing nvidia-glx-195

dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-195' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-185'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-195_195.30-0ubuntu1~karmic~nvidiavdpauppa5_amd64.deb (--unpack):
 subprocess new pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-195_195.30-0ubuntu1~karmic~nvidiavdpauppa5_amd64.deb
Traceback (most recent call last):
  File "interface.py", line 432, in <module>
    a.mainMenu()
  File "interface.py", line 295, in mainMenu
    a.driverMenu('nvidia')
  File "interface.py", line 333, in driverMenu
    self.process(self.abstract.install, package)
  File "interface.py", line 391, in process
    myFunction(myArgs)
  File "/usr/lib/python2.6/dist-packages/Envy/abstraction.py", line 155, in install
    self.pkg.install(packages, self.widget)
  File "/usr/lib/python2.6/dist-packages/Envy/packagemanager.py", line 164, in install
    self.cache.commit(UiFetchProgress(widget, self.isText), UiInstallProgress(widget, self.isText)) 
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 318, in commit
    raise SystemError("installArchives() failed")
SystemError: installArchives() failed
mark@torrentslave:~$ 

thanks in advanced for any help :)

---

### Post by markp1989 on 2010-01-31
i hate to do this so soon , but bump:

if i try using the restricted driver progra (jockey-gtk) i get an error saying :

"SystemError: installArchives () Failed"

thanks for any help markp1989

---

### Post by markp1989 on 2010-01-31
I have got the driver installed now, i had to go back 1 version (im sure i tried that yesterday with no luck *shrug* ) 

i also had to install the old version of nvidia settings as the new version would segfault randomly with the old driver

---

### Post by gilson585 on 2010-02-05
I too have this issue and nothing I have done seems to help. Now my mythtv is in a unusable state. Surely someone has an answer. Obviously some files from the old driver are clashing with the new one. Why isn't this handled automatically. I can't make sense of it all.

---

### Post by AdrianVeidt on 2010-02-05
```
dpkg-divert: `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-195' clashes with `diversion of /usr/lib/libGL.so.1 to /usr/lib/nvidia/libGL.so.1.xlibmesa by nvidia-glx-185'
```

That is why the install failed in this case. Look for error messages similar to this in the future. The packaging scripts are supposed to remove the diversions from the old driver before the new driver goes in. However, if you want to run the commands to remove the diversions manually, here they are:

```
$sudo dpkg-divert --remove --rename --package nvidia-glx-185 --divert /usr/lib/nvidia/libGL.so.1.xlibmesa /usr/lib/libGL.so.1
$sudo dpkg-divert --remove --rename --package nvidia-glx-185 --divert /usr/lib/nvidia/libGL.so.1.2.xlibmesa /usr/lib/libGL.so.1.2
$sudo dpkg-divert --remove --rename --package nvidia-glx-185 --divert /usr/lib/nvidia/libGLcore.so.xlibmesa /usr/lib/xorg/modules/extensions/libGLcore.so
$sudo dpkg-divert --remove --rename --package nvidia-glx-185 --divert /usr/lib/nvidia/libglx.so.xserver-xorg-core /usr/lib/xorg/modules/extensions/libglx.so
$sudo dpkg-divert --remove --rename --package nvidia-glx-185 --divert  /usr/lib32/nvidia/libGL.so.xlibmesa /usr/lib32/libGL.so
$sudo dpkg-divert --remove --rename --package nvidia-glx-185 --divert  /usr/lib32/nvidia/libGL.so.1.2.xlibmesa /usr/lib32/libGL.so.1.2
$sudo rm -f /usr/lib/xorg/modules/extensions/libglx.so.185.18.36
$sudo rmdir --ignore-fail-on-non-empty /usr/lib32/nvidia
$sudo rm -f /usr/lib32/libGL.so.1.2
$sudo rm -f /usr/lib32/libGL.so.1
$sudo rm -f /usr/lib32/libGL.so
```

You should remove the driver with *sudo apt-get purge nvidia-glx-185 nvidia-185-kernel-source* first. Some or all of the above commands may then fail (due to the files and diversions already being gone).

---

### Post by kulight on 2010-02-05
Thank you
that actually worked (I've tried many other solutions before)

---

### Post by gilson585 on 2010-02-07
Thanks for the help AdrianVeidt for I have finally fixed my issue with your help. Now initially I tried  your instructions and it had still failed to install but I wasn't ready to give up yet so I tried envyng-gtk and used the textual interface by executing envyng -t . Now this provided more output which I needed and quickly figured out I had to remove one more diversion. I knew that with a little help I would get it much thanks again. Heres my last diversion.
sudo dpkg-divert --remove --rename --package nvidia-glx-185 --divert  /usr/lib32/nvidia/libGL.so.1.xlibmesa /usr/lib32/libGL.so.1

---

### Post by rleggett on 2010-03-15
Thanks AdrianVeidt! This worked for me too.

---

