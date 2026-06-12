---
title: "Ubuntu 12.04 rebuilding xorg.conf doesn't work and stoppping x server doesn't either"
date: 2012-09-08
forum: General Help
---

### Post by Cavsfan on 2012-09-08
First of all I have an Nvidia geforce 9800 gt and here is my /etc/X11/xorg.conf file:
```


Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection

```I feel there should be a lot more to it and found that if I booted into recovery and selected root shell
and entered **Xorg -configure** that a new file would be built named xorg.conf.new which I could then rename xorg.conf.
However when I tried to do that it said it is in read only mode and that was that.

In 12.04 it appears when you login to recovery that everything is read only.

Any one have a clue how to fix this?

Also, when I boot into recovery mode and enter **sudo service lightdm stop** it does not stop the X server but, instead appears to restart it as I am looking at the regular login screen.

My primary goal is the stop the X server to be able to manually install the latest Nvidia driver and **sudo service lightdm stop** does not do the job.

I have already tried the xswat ppa which was a complete disaster resulting in the necessity to do a clean install.

Any advice on fixing this would be greatly appreciated. :)

---

### Post by Cavsfan on 2012-09-10
Can anyone shed any light on this?
Thanks.

---

### Post by steeldriver on 2012-09-10
I don't know why service lightdm stop doesn't work for you - however you can always remount the filesystem read-write in recovery mode

```
mount -o remount,rw /
```The way I understand it, the new way of configuring Xorg is to probe everything at runtime so in most cases a traditional xorg.conf file is unnecessary

---

### Post by Cavsfan on 2012-09-11
> **steeldriver said:**
> I don't know why service lightdm stop doesn't work for you - however you can always remount the filesystem read-write in recovery mode

```
mount -o remount,rw /
```The way I understand it, the new way of configuring Xorg is to probe everything at runtime so in most cases a traditional xorg.conf file is unnecessary

I just tried that command and it still gave an error about read only file system.
It seemed to understood **sudo service lightdm start** I believe because the screen went dark but on **sudo service lightdm stop** it said it didn't understand "stop".

I was just trying to update the Nvidia driver like I could with Lucid but, I guess too much has changed. I guess I'll just leave it alone as the driver does not have any problems.

Thanks!

---

### Post by Cavsfan on 2012-10-13
Would installing Xephyr enable me to stop my xserver lightdm?

As I mentioned in the first post **sudo service lightdm stop** bring me to the login screen and does not stop the x server.

```
lightdm --help
Usage:
  lightdm [OPTION...] - Display Manager

Help Options:
  -h, --help                    Show help options

Application Options:
  -c, --config=FILE             Use configuration file
  -d, --debug                   Print debugging messages
  [COLOR="Red"]--test-mode                   Run as unprivileged user, skipping things that require root access[/COLOR]
  --pid-file=FILE               File to write PID into
  --xsessions-dir=DIRECTORY     Directory to load X sessions from
  --xgreeters-dir=DIRECTORY     Directory to load X greeters from
  --log-dir=DIRECTORY           Directory to write logs to
  --run-dir=DIRECTORY           Directory to store running state
  --cache-dir=DIRECTORY         Directory to cache information
  -v, --version                 Show release version

```

```
lightdm --test-mode
Running inside an X server requires [COLOR="Red"]Xephyr[/COLOR] to be installed but it cannot be found.  Please install it or update your PATH environment variable.

```

Or would this just enable me to run "inside the x server". :confused:
Just curious as to why everyone else can issue the command **sudo service lightdm stop** and it works to stop the x server.
When my system does not.

I would seriously like to be able to manually install the latest Nvidia driver like I can in Lucid. But, it cannot be done without stopping the x server.
Thanks for any input.

---

### Post by bogan on 2012-10-13
Hi!, Cavsfan,

The easy way to overcome the Recovery 'Read Only' cafoo, is to run the 'fsck', option before dropping to a root Terminal , that resets it to Read/Write.

As to the failure of 'sudo service lightdm stop' to shut down the xorg server, it is a complete mystery to me also. Exactly the same thing happened to me on the kernal update before last.

Unfortunpely, I can not tell you how to get over it, as I tried everything I could think of, [ including removing and reinstalling lightdm] to get over nvidia-installer claiming I had modules from 295.59 as well as 304.51, [although I had used apt-get remove --purge nvidia* twice] and then got itself in a loop about some .so files not being a symbolic link and could not remove them as they wern't etc etc.

I had just decided to do a reinstall when as a last resort I did a 'Cold Finger Reset' ie. Shut down, switch off computer, remove power lead and hold down the power button for 30 secs, reconnect  and reboot.

I then went via recovery terminal, to a decompressed folder of nvidia 304.51 and ran nvidia-installer -f [ after entering 'telinit 3' ] and it installed without any problem.

After that lightdm worked as normal and after another reboot the nvidia version string had changed from 295.59 to 304.51.

Best of luck, Chao!, **bogan**.

---

### Post by Cavsfan on 2012-10-13
> **bogan said:**
> Hi!, Cavsfan,

The easy way to overcome the Recovery 'Read Only' cafoo, is to run the 'fsck', option before dropping to a root Terminal , that resets it to Read/Write.

As to the failure of 'sudo service lightdm stop' to shut down the xorg server, it is a complete mystery to me also. Exactly the same thing happened to me on the kernal update before last.

Unfortunpely, I can not tell you how to get over it, as I tried everything I could think of, [ including removing and reinstalling lightdm] to get over nvidia-installer claiming I had modules from 295.59 as well as 304.51, [although I had used apt-get remove --purge nvidia* twice] and then got itself in a loop about some .so files not being a symbolic link and could not remove them as they wern't etc etc.

I had just decided to do a reinstall when as a last resort I did a 'Cold Finger Reset' ie. Shut down, switch off computer, remove power lead and hold down the power button for 30 secs, reconnect  and reboot.

I then went via recovery terminal, to a decompressed folder of nvidia 304.51 and ran nvidia-installer -f [ after entering 'telinit 3' ] and it installed without any problem.

After that lightdm worked as normal and after another reboot the nvidia version string had changed from 295.59 to 304.51.

Best of luck, Chao!, **bogan**.

Thanks **bogan**! Sounds sort of intimidating to me. I may just give it a try in a few days. My 12.04 is on an extra partition right now and I could easily reinstall if necessary.
Still trying to hang on to Lucid as my main Ubuntu as long as I can.

---

### Post by bogan on 2012-10-14
Hi!,** Cavsfan**,

No reason to be intimidated, the basic cause of my particular problem - the orphanned .so files - was a relic of my having used the -x-swat ppa to install nvidia-current 295.40 & 295.59 and in some way it interacted with the kernal update to -31.

On another 12.04.1 installation the same kernal update produced another strange effect; despite the nvidia303.43 driver being DKMS compatible it re-booted to a low-res GUI login screen, and 'Crtl+Alt+F1-F6' produced only a Black screen, with no tty login or text, whence 'Crtl+Alt+F7' produced a 'Please wait while the graphics screen is reestablished' message, and hung there indefinitely - another, for me, previously never encountered situation.

I only found out when booting to a tty and using 'startx' instead of lightdm, which gave me a long list of errors that lightdm never displayed.

It might be worth your trying that as well.

BTW. I have noted several other Posts reporting lightdm not stopping the xorgserver, so we are not alone.

Chao!,** bogan**.

---

