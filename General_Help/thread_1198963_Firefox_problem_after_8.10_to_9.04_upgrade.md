---
title: "Firefox problem after 8.10 to 9.04 upgrade"
date: 2009-06-28
forum: General Help
---

### Post by luvbugerr on 2009-06-28
Hi, please help me! Am truly a beginner to Ubuntu.

Upgraded from 8.10 to 9.04 and had problems on the net - streaming, videos, etc.
I hadn't seen that all that was required was an installation of "Ubuntu-restricted-extras"; I proceeded to install heaps of different plugins. I uninstalled Firefox and reinstalled it, but think that I messed up and don't know where!!! I eventually found SWF website and followed the instructions to install, but obviously not successfully.

Here are the instructions from SWF, that I followed:

[As time of writing latest stable releases are swfdec 0.8.4 and swfdec-mozilla 0.8.2. 
Before you start should should make sure you have the following packages installed from your package manager or another source, debian / ubuntu names listed, yours may be a little different: 
*autoconf automake binutils gcc libasound2-dev libc6-dev libcairo2-dev libglib2.0-dev libgtk2.0-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libnss3-dev liboil0.3-dev libpango1.0-dev libsoup2.4-dev libtool make pkg-config* 
If you want to use pulseaudio as audio backend add *libpulse-dev*, *BSD users needs to do so. 
In order to have a good experience you have to install the gstreamer good and ugly plugins, called *gstreamer0.10-plugins-good*, *gstreamer0.10-plugins-ffmpeg* and *gstreamer0.10-plugins-ugly*. 
You can then download the source code from the swfdec site and configure it. 
*wget [http://swfdec.freedesktop.org/download/swfdec/0.8/swfdec-0.8.4.tar.gz](http://swfdec.freedesktop.org/download/swfdec/0.8/swfdec-0.8.4.tar.gz)* 
*tar xvzf swfdec-0.8.4.tar.gz* 
*cd swfdec-0.8.4* 
*./configure* 
If you want the pulseaudio backend use: 
*./configure --with-audio=pulse* 
If you get any error messages here then it's probably because you are still missing some libraries that the application needs. If this is the case you can try your package manager for a package of a similar name with -dev on the end. 
You can then make and install it... 
*make* 
*sudo make install* 
...before installing the plugin. 
*cd ..* 
*wget [http://swfdec.freedesktop.org/download/swfdec-mozilla/0.8/swfdec-mozilla-0.8.2.tar.gz](http://swfdec.freedesktop.org/download/swfdec-mozilla/0.8/swfdec-mozilla-0.8.2.tar.gz)* 
*tar xvzf swfdec-mozilla-0.8.2.tar.gz* 
*cd swfdec-mozilla-0.8.2* 
*./configure --with-plugin-dir=$HOME/.mozilla/plugins* 
*make* 
[I]make install]

[/I]After doing all of the above, this is what I get:
[I]eva@eva-pc:~/swfdec-mozilla-0.8.2$ make
make  all-recursive
make[1]: Entering directory `/home/eva/swfdec-mozilla-0.8.2'
Making all in icons
make[2]: Entering directory `/home/eva/swfdec-mozilla-0.8.2/icons'
Making all in 16x16
make[3]: Entering directory `/home/eva/swfdec-mozilla-0.8.2/icons/16x16'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/eva/swfdec-mozilla-0.8.2/icons/16x16'
Making all in 22x22
make[3]: Entering directory `/home/eva/swfdec-mozilla-0.8.2/icons/22x22'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/eva/swfdec-mozilla-0.8.2/icons/22x22'
Making all in 24x24
make[3]: Entering directory `/home/eva/swfdec-mozilla-0.8.2/icons/24x24'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/eva/swfdec-mozilla-0.8.2/icons/24x24'
Making all in 32x32
make[3]: Entering directory `/home/eva/swfdec-mozilla-0.8.2/icons/32x32'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/eva/swfdec-mozilla-0.8.2/icons/32x32'
Making all in 48x48
make[3]: Entering directory `/home/eva/swfdec-mozilla-0.8.2/icons/48x48'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/eva/swfdec-mozilla-0.8.2/icons/48x48'
Making all in scalable
make[3]: Entering directory `/home/eva/swfdec-mozilla-0.8.2/icons/scalable'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/eva/swfdec-mozilla-0.8.2/icons/scalable'
make[3]: Entering directory `/home/eva/swfdec-mozilla-0.8.2/icons'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/eva/swfdec-mozilla-0.8.2/icons'
make[2]: Leaving directory `/home/eva/swfdec-mozilla-0.8.2/icons'
Making all in mozilla-sucks
make[2]: Entering directory `/home/eva/swfdec-mozilla-0.8.2/mozilla-sucks'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/eva/swfdec-mozilla-0.8.2/mozilla-sucks'
Making all in src
make[2]: Entering directory `/home/eva/swfdec-mozilla-0.8.2/src'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/eva/swfdec-mozilla-0.8.2/src'
make[2]: Entering directory `/home/eva/swfdec-mozilla-0.8.2'
make[2]: Leaving directory `/home/eva/swfdec-mozilla-0.8.2'
make[1]: Leaving directory `/home/eva/swfdec-mozilla-0.8.2'
eva@eva-pc:~/swfdec-mozilla-0.8.2$ make install
Making install in icons
make[1]: Entering directory `/home/eva/swfdec-mozilla-0.8.2/icons'
Making install in 16x16
make[2]: Entering directory `/home/eva/swfdec-mozilla-0.8.2/icons/16x16'
make[3]: Entering directory `/home/eva/swfdec-mozilla-0.8.2/icons/16x16'
make[3]: Nothing to be done for `install-exec-am'.
test -z "/usr/local/share/icons/hicolor/16x16/apps" || /bin/mkdir -p "/usr/local/share/icons/hicolor/16x16/apps"
/bin/mkdir: cannot create directory `/usr/local/share/icons/hicolor/16x16': Permission denied
make[3]: *** [install-iconDATA] Error 1
make[3]: Leaving directory `/home/eva/swfdec-mozilla-0.8.2/icons/16x16'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/eva/swfdec-mozilla-0.8.2/icons/16x16'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/eva/swfdec-mozilla-0.8.2/icons'
make: *** [install-recursive] Error 1
eva@eva-pc:~/swfdec-mozilla-0.8.2$ 

[/I]Thanks to anyone for ANY assistance to put me out of my misery:confused:

---

### Post by plewisfdx on 2009-06-28
Open Synaptic (Administration->Synaptic Package Manager) hit Reload (to refresh the packages available to their most current) and in the search box type Firefox.  Make sure you have the latest version installed (should be a green box to the left of firefox).

Search for ubuntu-restricted-extras and make sure you have the latest version installed.

Run Firefox and it should work.

Optionally you can delete the /home/eva/swfdec-mozilla-0.8.2 directory you created, as you shouldn't need that for flash video on firefox.

---

### Post by lovinglinux on 2009-06-28
Please use the "[quote]" and "```
" tags to encapsulate text from other posts and terminal outputs.

The instructions you followed seems over complicated to me, since it is for compiling swfdec, which is already available in the repositories. Besides, swfdec doesn't work on all web sites. 

The solution to your problem is in the Troubleshooting section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567). Re-installing Firefox is usually unnecessary. 

See quote below:

> **lovinglinux said:**
> 
Some video issues are caused by conflicting plug-ins. It's not a good idea to have multiple plug-ins for the same type of content.

To remove conflicting flash plug-ins and install only the one from Adobe open "Applications >> Accessories >> Terminal", then paste (CTRL+SHIFT+V) the code below in the terminal window and hit enter:

[code]sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash && sudo apt-get install flashplugin-nonfree 
```



---

### Post by luvbugerr on 2009-06-29
Lovinglinux,

Thank you very much. It worked perfectly. I have learned not to mess around with things I don't know too much about. Should have asked for help ages ago.

Sorry about the quotes, will be sure to remember next time.

---

### Post by lovinglinux on 2009-06-29
> **luvbugerr said:**
> Lovinglinux,

Thank you very much. It worked perfectly. I have learned not to mess around with things I don't know too much about. Should have asked for help ages ago.

Sorry about the quotes, will be sure to remember next time.

You are welcome. I recommend posting in the [Absolute Beginner Talk](http://ubuntuforums.org/forumdisplay.php?f=326) instead of the General Help, since most people will avoid giving too complicated solutions there. Usually there are different approaches to the same problem so, instead of applying the first solution you receive, wait for a few replies, since someone might know a simpler solution to the same problem. Additionally, sometimes people trying to help will post possible solutions they are not sure it will work (I do it all the time), because is not always easy to pinpoint the problem without physical access to the machine.

It is not a good idea to run commands without knowing what they do. So ask if you don't know. Take a look at [this](http://ubuntuforums.org/announcement.php?f=326).

---

