---
title: "Unity won't work even though..."
date: 2011-08-14
forum: General Help
---

### Post by zaabi1995 on 2011-08-14
Hello, I have a problem that Unity wont work with me, i have a Samsung laptop with Nivida - Inter i7 - 8processors - 2.8ghz - 6GB ram
and when i first logged in to Ubuntu it told me that their isn't enough hardware :/ which i dont think is correct and i updated all my drivers as you can see from the pic

Thanks!

Solved Thanks to 
 				 				[apollothethird]("http://ubuntuforums.org/member.php?u=1176033")
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by apollothethird on 2011-08-14
> **zaabi1995 said:**
> Hello, I have a problem that Unity wont work with me, i have a Samsung laptop with Nivida - Inter i7 - 8processors - 2.8ghz - 6GB ram
and when i first logged in to Ubuntu it told me that their isn't enough hardware :/ which i dont think is correct and i updated all my drivers as you can see from the pic

Thanks!

I have never seen the error you refer to.  What exactly is the error message.

There are steps you can take for unity support.  One of them include running

```
/usr/lib/nux/unity_support_test -p
```How is your video adapter named in the xorg.conf file?  How is it reportedly named in the nvidia X Server Settings application?

If your card is blacked listed by Unity, it doesn't mean that it won't work, it just mean it hasn't been tested as being supported.  You can override this blacklisting by adding UNITY_FORCE_START=1 to /etc/environment.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by zaabi1995 on 2011-08-14
> **apollothethird said:**
> I have never seen the error you refer to.  What exactly is the error message.

There are steps you can take for unity support.  One of them include running

```
/usr/lib/nux/unity_support_test -p
```How is your video adapter named in the xorg.conf file?  How is it reportedly named in the nvidia X Server Settings application?

If your card is blacked listed by Unity, it doesn't mean that it won't work, it just mean it hasn't been tested as being supported.  You can override this blacklisting by adding UNITY_FORCE_START=1 to /etc/environment.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

Thanks for your reply
I tried the code and got 
"
ali@Ali:~$ /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: unable to create the OpenGL context
"

and i just tried running Nvidia x server settings and got this error message
"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

And i didn't really know how to " You can override this blacklisting by adding UNITY_FORCE_START=1 to /etc/environment." :/

Thanks!

---

### Post by apollothethird on 2011-08-14
> **zaabi1995 said:**
> Thanks for your reply
I tried the code and got 
"
ali@Ali:~$ /usr/lib/nux/unity_support_test -p
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: unable to create the OpenGL context
"

and i just tried running Nvidia x server settings and got this error message
"You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

And i didn't really know how to " You can override this blacklisting by adding UNITY_FORCE_START=1 to /etc/environment." :/

Thanks!

Hi, Zaabi.  I'm still wondering where Ubuntu told you "there isn't enough hardware"?  Thanks in advance if you'd make a reference to that.

You also didn't make a reference to whether your video adapter is named in your xorg.conf file.  I probably mentioned a number of things in one message, but all of them were important, just about in the order I mentioned them.  One of the most important components is your /etc/X11/xorg.conf file.
You can run "nvidia-xconfig" to help you setup your xorg.conf file, since nvidia settings is reported it's not setup.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by zaabi1995 on 2011-08-14
> **apollothethird said:**
> Hi, Zaabi.  I'm still wondering where Ubuntu told you "there isn't enough hardware"?  Thanks in advance if you'd make a reference to that.

You also didn't make a reference to whether your video adapter is named in your xorg.conf file.  I probably mentioned a number of things in one message, but all of them were important, just about in the order I mentioned them.  One of the most important components is your /etc/X11/xorg.conf file.
You can run "nvidia-xconfig" to help you setup your xorg.conf file, since nvidia settings is reported it's not setup.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

Oh when i First ran Ubuntu it gave me that message and told me something about Ubuntu classic.. i didnt screenshot it or anything though.

I dont get what is xorg.conf file :(?

---

### Post by bro on 2011-08-14
I've had the same message as you show in the first post. You can see it says the driver is installed, but not currently in use. 

Do you have Nvidia Optimus? This won't work properly with linux (though workarounds are in the making)

---

### Post by apollothethird on 2011-08-14
> **zaabi1995 said:**
> Oh when i First ran Ubuntu it gave me that message and told me something about Ubuntu classic.. i didnt screenshot it or anything though.

I dont get what is xorg.conf file :(?

Can you give us the content of your xorg.conf file?  You can get this by typing in a terminal:

```
cat /etc/X11/xorg.conf
```Will you give us the output.  Be sure to place the output between code tags to help keep your message readable.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by bro on 2011-08-14
Can you post the output of ```
lspci | grep VGA

```

---

### Post by zaabi1995 on 2011-08-14
> **apollothethird said:**
> Can you give us the content of your xorg.conf file?  You can get this by typing in a terminal:

```
cat /etc/X11/xorg.conf
```Will you give us the output.  Be sure to place the output between code tags to help keep your message readable.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

Alright
```

ali@Ali:~$ cat /etc/X11/xorg.conf

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection


```

---

### Post by apollothethird on 2011-08-14
> **zaabi1995 said:**
> Alright
```

ali@Ali:~$ cat /etc/X11/xorg.conf

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
EndSection


```


Great.  We see that you don't have nvidia support settings in your X configuration.  You can use the nvidia program to help you configure it.

Run (as nvidia settings is telling you:

```
nvidia-xconfig
```Also, will you give us the output of Bro's suggestion?

```
lspci | egrep VGA
```-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by zaabi1995 on 2011-08-14
> **apollothethird said:**
> Great.  We see that you don't have nvidia support settings in your X configuration.  You can use the nvidia program to help you configure it.

Run (as nvidia settings is telling you:

```
nvidia-xconfig
```Also, will you give us the output of Bro's suggestion?

```
lspci | egrep VGA
```-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

Okay i get
```

ali@Ali:~$ lspci | egrep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

```

And Yes i do have Nvidia Optimus:$

Thanks!

---

### Post by WyleECoyote on 2011-08-14
did you disable the integrated graphics in your BIOS?

---

### Post by zaabi1995 on 2011-08-14
> **WyleECoyote said:**
> did you disable the integrated graphics in your BIOS?

ill try that and tell you what happens!

---

### Post by zaabi1995 on 2011-08-14
> **WyleECoyote said:**
> did you disable the integrated graphics in your BIOS?

i couldnt find anything like that in the bios :/

---

### Post by apollothethird on 2011-08-14
> **zaabi1995 said:**
> Okay i get
```

ali@Ali:~$ lspci | egrep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

```And Yes i do have Nvidia Optimus:$

Thanks!

What do you get when you run nvidia-xconfig?

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljaes](www.apollo3.com/~ljaes)

---

### Post by zaabi1995 on 2011-08-14
> **apollothethird said:**
> What do you get when you run nvidia-xconfig?

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljaes]("http://www.apollo3.com/%7Eljaes")


Hmm
```

ali@Ali:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

ERROR: Unable to write to directory '/etc/X11'.


```

---

### Post by WyleECoyote on 2011-08-14
> **zaabi1995 said:**
> Hmm
```

ali@Ali:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

ERROR: Unable to write to directory '/etc/X11'.


```

should be:

```
sudo nvidia-xconfig
```

---

### Post by zaabi1995 on 2011-08-14
> **WyleECoyote said:**
> should be:

```
sudo nvidia-xconfig
```


alrightt got this :

```
ali@Ali:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

---

### Post by WyleECoyote on 2011-08-14
yep, sounds right now check to see that it was properly written to by 

```
cat /etc/X11/xorg.conf
```

should have more info now

or you can just start with root the nvidia-settings like this:

```
gksudo nvidia-settings
```

if you try as regular user you have missing options that cannot be enabled and dont forget you have to restart x by rebooting or restarting gdm kdm or xdm whatever you use

---

### Post by apollothethird on 2011-08-14
> **zaabi1995 said:**
> alrightt got this :

```
ali@Ali:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
```

You'll have to reboot your computer to check the new configuration.  If don't get a menu panel you can use Alt-F2 and run gnome-terminal.  Then run gnome-panel.  Use that to log out and log back in using Ubuntu Classic.  You'll have this option in the status  bar when you click your login name just before putting in your password.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by zaabi1995 on 2011-08-14
> **WyleECoyote said:**
> yep, sounds right now check to see that it was properly written to by 

```
cat /etc/X11/xorg.conf
```

should have more info now

okay i did that and i got

```
ali@Ali:~$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.41.06  (buildmeister@swio-display-x86-rhel47-08.nvidia.com)  Mon Apr 18 15:14:00 PDT 2011


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

ali@Ali:~$ 

```

:$?

---

### Post by zaabi1995 on 2011-08-14
> **apollothethird said:**
> You'll have to reboot your computer to check the new configuration.  If don't get a menu panel you can use Alt-F2 and run gnome-terminal.  Then run gnome-panel.  Use that to log out and log back in using Ubuntu Classic.  You'll have this option in the status  bar when you click your login name just before putting in your password.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

Alright ill try that;)

---

### Post by zaabi1995 on 2011-08-14
Alright guys i restarted it and the system just failed (I am using Windows 7 currently)
it wouldnt let me go in
the error was showing me loads of auto generating stuff etc
99% were ok
except the auto generating crash report which gave a 'fail'

anyways since its like this i guess ill unistall ubuntu for now (: sorry for everything, its kinda getting on my nerves:$

---

### Post by apollothethird on 2011-08-14
> **zaabi1995 said:**
> Alright guys i restarted it and the system just failed (I am using Windows 7 currently)
it wouldnt let me go in
the error was showing me loads of auto generating stuff etc
99% were ok
except the auto generating crash report which gave a 'fail'

anyways since its like this i guess ill unistall ubuntu for now (: sorry for everything, its kinda getting on my nerves:$

I'm kind of surprised that you prefer to run Windows 7 than to run Ubuntu without Unity, something you haven't seen.  There's a lot more to Linux/Ubuntu than just Unity.  Also, Unity 2D can easily run without the 3D support which the system attempts by default.  You'd still basically experience Unity if you set it up in 2D.

But it's your call.

I was glad to help.

Have a nice day!

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by WyleECoyote on 2011-08-14
sorry to hear that but it is understandable. It is a driver problem, and maybe your card is too new and not fully supported yet but I hope you come back and try again later and there are other distro's out there that you may try... ultimate edition is based off ubuntu maybe you can give it a try, my friend swears by it but I am not sure if it has unity enabled I have really only used that distro for a little while, right now I only run Debian Wheezy but do not recommend that to you at all. I am not a bug unity fan and if I did have Ubuntu installed I would still choose Gnome

---

### Post by zaabi1995 on 2011-08-14
> **apollothethird said:**
> I'm kind of surprised that you prefer to run Windows 7 than to run Ubuntu without Unity, something you haven't seen.  There's a lot more to Linux/Ubuntu than just Unity.  Also, Unity 2D can easily run without the 3D support which the system attempts by default.  You'd still basically experience Unity if you set it up in 2D.

But it's your call.

I was glad to help.

Have a nice day!

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)



Its not just that :$, its the fact that it doesn't support my driver which is kinda annoying :p so i guess it will be slower etc :/..
i might go back to it when the gnome3.0 stable gets released etc :D
And sorry if i was a pain :/:$ Thanks a lot:D!

---

### Post by zaabi1995 on 2011-08-14
> **WyleECoyote said:**
> sorry to hear that but it is understandable. It is a driver problem, and maybe your card is too new and not fully supported yet but I hope you come back and try again later and there are other distro's out there that you may try... ultimate edition is based off ubuntu maybe you can give it a try, my friend swears by it but I am not sure if it has unity enabled I have really only used that distro for a little while, right now I only run Debian Wheezy but do not recommend that to you at all. I am not a bug unity fan and if I did have Ubuntu installed I would still choose Gnome

Yah its prob that :/.. i read in one forum that they won't support nvidia optimus since 
well :
> NVIDIA has no plans for Optimus support in their binary blob drivers for Linux:
Quote:
We have no plans to support Optimus on Linux at this time.
Source: [http://www.nvnews.net/vbulletin/show...77#post2183477](http://www.nvnews.net/vbulletin/show...77#post2183477)

There are architectural problems with the X.org server implementing Optimus:
Quote:
... there is no way without a major rearchitecture of the X.org and DRI stacks we can support optimus anytime soon.
Source: [http://www.mail-archive.com/hybrid-g.../msg00007.html](http://www.mail-archive.com/hybrid-g.../msg00007.html)

That isn't to say new Optimus machines won't run Linux at all, just that they will probably only be able to use integrated graphics, since the actual video output is handled with a single multiplexer on the Intel IGP (previous switchable graphics implementations used a switch to select the mux).

Further reading: [http://www.notebookcheck.net/Nvidia-...0.html#c379533](http://www.notebookcheck.net/Nvidia-...0.html#c379533)

Nouveau may someday support Optimus, but as of yet there has been no discussion on their mailing list so this is mere speculation. There is no mention of any change that would allow X.org to support Optimus in the upcoming 1.9 release.
this is from 
```
http://forum.notebookreview.com/linux-compatibility-software/473915-no-support-nvidia-optimus-linux.html
```

Anyhow they might support it later :$ 

and thanks loads:D

---

### Post by apollothethird on 2011-08-14
> **zaabi1995 said:**
> Its not just that :$, its the fact that it doesn't support my driver which is kinda annoying :p so i guess it will be slower etc :/..
i might go back to it when the gnome3.0 stable gets released etc :D
And sorry if i was a pain :/:$ Thanks a lot:D!

Actually Ubuntu does support your driver using Gnome or Unity 2D.  It'd probably support it using Unity 3D, but I understand you don't want to be bothered with trying to configure it.

By the way, the last thing you did to bring the video card into the mix was given to you as a suggestion in my first message.  NVidia-xconfig put support in your xorg.conf file for what you probably don't have (readily seen by the OS).  Removing the change would be as simple as removing the new xorg.conf file (sudo rm /etc/X11/xorg.conf).  You can replace it with the xorg.conf.backup file that nvidia provided you.

You can easily run Unity on your system.  Just run "sudo apt-get unity-2d" and your machine would boot into Unity.  I'm sure I could also have your running unity 3D, but I understand that you get frustrated with configuring the system.

I'm still see this as a first that a someone looking to check out an alternative to Windows was looking for Unity than the OS itself.

I'm sure Canonical are happen with their promotions to have achieved such devotion to Unity over the OS itself.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by zaabi1995 on 2011-08-14
> **apollothethird said:**
> Actually Ubuntu does support your driver using Gnome or Unity 2D.  It'd probably support it using Unity 3D, but I understand you don't want to be bothered with trying to configure it.

By the way, the last thing you did to bring the video card into the mix was given to you as a suggestion in my first message.  NVidia-xconfig put support in your xorg.conf file for what you probably don't have (readily seen by the OS).  Removing the change would be as simple as removing the new xorg.conf file (sudo rm /etc/X11/xorg.conf).  You can replace it with the xorg.conf.backup file that nvidia provided you.

You can easily run Unity on your system.  Just run "sudo apt-get unity-2d" and your machine would boot into Unity.  I'm sure I could also have your running unity 3D, but I understand that you get frustrated with configuring the system.

I'm still see this as a first that a someone looking to check out an alternative to Windows was looking for Unity than the OS itself.

I'm sure Canonical are happen with their promotions to have achieved such devotion to Unity over the OS itself.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

Thanks for all the support,, hmm i just really liked unity and the interface etc...  but if my driver really does support it i wouldnt mind trying:$ ill install ubuntu again on 32bit it might work better, cuz last time it was on 64..so that might of caused some of the drivers not to function well or something?
but ill try it out.. and Linux is niceeee!

---

### Post by apollothethird on 2011-08-14
> **zaabi1995 said:**
> Thanks for all the support,, hmm i just really liked unity and the interface etc...  but if my driver really does support it i wouldnt mind trying:$ ill install ubuntu again on 32bit it might work better, cuz last time it was on 64..so that might of caused some of the drivers not to function well or something?
but ill try it out.. and Linux is niceeee!

When did you see/use Unity?

I don't think you'll have any difference with the 32bit as far as hardware support.  There's a chance it might work on first go, but unlikely.  If it worked it might have something to do with something you might have done slightly different and if you uninstall the 32bit and try the 64bit again, it might work and vice-versa.

I'm sure with work you can have the Unity 3D.  You can easily have the Unity without uninstalling or starting over.  All you have to do is run "sudo apt-get install Unity-2d" and Unity will come right up.  I run Unity 2D on some of my machines and don't see obvious differences.  The fancy tweaks aren't available, but I hardly use them on my main "super" computer.  Almost every time I set a couple of options something breaks and I have to tweak a different option.  You'll find the advice all over to run "unity --reset" to recover from minor changes.  I never have to do that on my Unity 2D machines.

I'm glad to see you like Linux.  It's really nice.  The more you use it the more you like it.  A person doesn't have to spend time tweaking their machines.  They can just use it as a productive tool.  But many people like it so much that they spend lots of time playing with it and all the many features.

It's really easy to fix things on a Linux machine, as compared to Windows.  You almost always have to perform reinstalls to fix problems on Windows.  You almost never have to do that with Linux.  Often all you have to do is just create a new user, then use that account and you're fresh.  Copy your files over to the new side and you're all set.

There are lots of things you can do to fix problems.  And, of course, you don't have to have problems if you just use it instead of playing with it.  But again, most people can't help but to spend a lot of time tweaking.  I sometimes spend weeks tweaking, then I might spend a few weeks and never make a change, just use the tool (word processing, accounting, web development, video editing, etc).

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by zaabi1995 on 2011-08-14
> **apollothethird said:**
> When did you see/use Unity?

I don't think you'll have any difference with the 32bit as far as hardware support.  There's a chance it might work on first go, but unlikely.  If it worked it might have something to do with something you might have done slightly different and if you uninstall the 32bit and try the 64bit again, it might work and vice-versa.

I'm sure with work you can have the Unity 3D.  You can easily have the Unity without uninstalling or starting over.  All you have to do is run "sudo apt-get install Unity-2d" and Unity will come right up.  I run Unity 2D on some of my machines and don't see obvious differences.  The fancy tweaks aren't available, but I hardly use them on my main "super" computer.  Almost every time I set a couple of options something breaks and I have to tweak a different option.  You'll find the advice all over to run "unity --reset" to recover from minor changes.  I never have to do that on my Unity 2D machines.

I'm glad to see you like Linux.  It's really nice.  The more you use it the more you like it.  A person doesn't have to spend time tweaking their machines.  They can just use it as a productive tool.  But many people like it so much that they spend lots of time playing with it and all the many features.

It's really easy to fix things on a Linux machine, as compared to Windows.  You almost always have to perform reinstalls to fix problems on Windows.  You almost never have to do that with Linux.  Often all you have to do is just create a new user, then use that account and you're fresh.  Copy your files over to the new side and you're all set.

There are lots of things you can do to fix problems.  And, of course, you don't have to have problems if you just use it instead of playing with it.  But again, most people can't help but to spend a lot of time tweaking.  I sometimes spend weeks tweaking, then I might spend a few weeks and never make a change, just use the tool (word processing, accounting, web development, video editing, etc).

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

Alright I am in the "Try Ubuntu" and its currently installing whats weird is Now Unity is working etc..and it still didn't install but after it installs the unity dissapears.. what made me really like ubuntu is the launcher on the left but then it dissapears randomly which made me panic and it was like i am using an outdated version even though am not but yeah..unity does feel much better (Y)

And yes you do have a point (Y) the fun in Ubuntu is that everything is customizable unlike Windows!

Thanks! and check the pic its the 'Try' and Everything seems to be working pretty well,,anyways ill install and tell you how it goes after the install-restart..

---

### Post by zaabi1995 on 2011-08-14
Errr no luck:$

Hmm here you go the pics i took em from my phone (The error message i get when i First run Ubuntu, and i only get it Once..)

---

### Post by apollothethird on 2011-08-15
> **zaabi1995 said:**
> Errr no luck:$

Hmm here you go the pics i took em from my phone (The error message i get when i First run Ubuntu, and i only get it Once..)

You can have Unity just by running "sudo apt-get install unity-2d".  You'll see the menu exactly the way you described it.

If I were you, I'd use the 64bit version since your computer supports it.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by zaabi1995 on 2011-08-15
> **apollothethird said:**
> You can have Unity just by running "sudo apt-get install unity-2d".  You'll see the menu exactly the way you described it.

If I were you, I'd use the 64bit version since your computer supports it.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

I just thought the 32bit would enable it:$ and as u said Unity2D ftw;) Thanks a lot:D ill go for unity2D and will prob change to 64bit but ill do that tomorrow :$ it has been a long day!
Thanksssss!

---

### Post by zaabi1995 on 2011-08-15
> **apollothethird said:**
> You can have Unity just by running "sudo apt-get install unity-2d".  You'll see the menu exactly the way you described it.

If I were you, I'd use the 64bit version since your computer supports it.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

And As you said :$ Unity2D is perfect :$ Thanks:D Be proud of your self;)!

---

### Post by bro on 2011-08-15
I'm almost certain your problem is somehow related to optimus and that there is a solution. Optimus makes you nvidia integrate with the integrated graphics. But your intel drivers for the integrated graphics should be able to handle 3d unity. The fact that you can use it from the cd confirms this. 

What I did is totally remove every driver/settings nvidia related. We can't compare completely though, because I'm also able to completely disable the nvidia card in the bios.

What might help you is to look into a project called bumblebee. These guys try to make optimus work as good as possible with linux and they're making some good progress. It is quite experimental but it worked on my laptop after some fiddling.  

[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)
and
[https://launchpad.net/~mj-casalogic/+archive/bumblebee/](https://launchpad.net/~mj-casalogic/+archive/bumblebee/) 

To try and install:```

sudo apt-add-repository ppa:mj-casalogic/bumblebee
sudo apt-get update
sudo apt-get install bumblebee

```

> Now 3D is enabled on both the Intel and the nVidia at the same time..

The Intel card is running the Desktop and the nVidia card can be used for
the thougher applications with the command "optirun32 <application>" or
"optirun64 <application>"...

---

### Post by realzippy on 2011-08-15
If your output shows 2 graphic devices then it is definitely an
Optimus issue.
```
lspci |grep VGA
```

---

### Post by zaabi1995 on 2011-08-16
> **bro said:**
> I'm almost certain your problem is somehow related to optimus and that there is a solution. Optimus makes you nvidia integrate with the integrated graphics. But your intel drivers for the integrated graphics should be able to handle 3d unity. The fact that you can use it from the cd confirms this. 

What I did is totally remove every driver/settings nvidia related. We can't compare completely though, because I'm also able to completely disable the nvidia card in the bios.

What might help you is to look into a project called bumblebee. These guys try to make optimus work as good as possible with linux and they're making some good progress. It is quite experimental but it worked on my laptop after some fiddling.  

[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)
and
[https://launchpad.net/~mj-casalogic/+archive/bumblebee/]("https://launchpad.net/%7Emj-casalogic/+archive/bumblebee/") 

To try and install:```

sudo apt-add-repository ppa:mj-casalogic/bumblebee
sudo apt-get update
sudo apt-get install bumblebee

```


That made it work :O:O Thaaaaaaaaaaaaaanks:D:D:D:DD

---

### Post by zaabi1995 on 2011-08-16
> **realzippy said:**
> If your output shows 2 graphic devices then it is definitely an
Optimus issue.
```
lspci |grep VGA
```


```
ali@Ali-RF511-RF411-RF711:~$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
ali@Ali-RF511-RF411-RF711:~$ 

```

this is after the bumble bee:$
Thanks:D

---

### Post by bro on 2011-08-16
> **zaabi1995 said:**
> That made it work :O:O Thaaaaaaaaaaaaaanks:D:D:D:DD

You're welcome. Enjoy Ubuntu...

---

### Post by apollothethird on 2011-08-16
> **zaabi1995 said:**
> ```
ali@Ali-RF511-RF411-RF711:~$ lspci |grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
ali@Ali-RF511-RF411-RF711:~$ 

```this is after the bumble bee:$
Thanks:D

Zaabi, glad for the success!  You can give back to the community by marking this topic as solved.  Many people try to search the solved topics when they have related issues.  This will help another person that's having similar problems.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by zaabi1995 on 2011-08-16
> **apollothethird said:**
> Zaabi, glad for the success!  You can give back to the community by marking this topic as solved.  Many people try to search the solved topics when they have related issues.  This will help another person that's having similar problems.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

Alirhgt:$ But but how do i do that :o?

---

### Post by zaabi1995 on 2011-08-16
> **apollothethird said:**
> Zaabi, glad for the success!  You can give back to the community by marking this topic as solved.  Many people try to search the solved topics when they have related issues.  This will help another person that's having similar problems.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

nvm got it :D
Thanks:D!

---

### Post by zaabi1995 on 2011-08-18
to anyone out their ill suggest Ubuntu 2D more than the normal one!
It is much much smoother!
Thanks!

---

### Post by apollothethird on 2011-08-21
> **zaabi1995 said:**
> to anyone out their ill suggest Ubuntu 2D more than the normal one!
It is much much smoother!
Thanks!

Zaabi, I'm very impressed with your compassion for Unity.  I share the same.

Thanks for your update to the on how to use Unity in such that you have the best as in smoothness.

I'm glad the developers demonstrate a concern for using the resources available in the hardware of today, and somewhat pushing it.  The more they use it, the more incentive the hardware developers will have for upping the level.  Without this cycle, much potential would be stagnate.

The hardware developers do this for the gamer.  I'm glad foundations such as Ubuntu and Unity gives them this incentive to do it for desktop users.

They have resolved to include downward compatibility for unsupported hardware in the support for Unity 2D.  But for me, if I didn't have the hardware to support 3D, the existence of it gives me incentive to upgrade.  I upgrade my hardware annually.  I used to do this for my hobby in Flight Simulator.  I was always happy at how the environment looked with each upgrade.  But for a very long time I always used Linux in a terminal window with commandlines.  That's a very powerful form in computer experience and productivity.  But recently (in about a year) started experiencing the GUI environment.  It has been so exciting that I don't have as much time for Flight Simulator as I used to have.

To me the environment is not only productive, but fun.  It's nice having this fun while I'm performing my business on the computer.

I'm saying a lot of this to say, it might not hurt to spend some time investigating how to optimise Unity 3D is it's possible with your hardware, or upgrade your hardware to achieve this.

I understand it isn't easy to upgrade a Laptop short of purchasing another one.  I would recommend that you consider getting a desktop for your main computer and using your Laptop as a satellite.  Then you could easier stay on the top edge of the technological scale of development.

It's fun.

Throughout the years some of my close friends and family have often asked me why would I invest so much money in my computer hardware (which is included as a major part of my hobby and leisure time).  Most of them spend more than $300.00 annually in their hobbies and leisure time.  After then have spent the money, most of them retain the experience, but don't have something they can physically touch (like the bowlers for instance).  But I have my computer which has grown and I can touch it.  So one year I might upgrade the video card.  A different year I might upgrade the hard drive or motherboard and or ram.

Since I'm using Ubuntu, I can check the forums and upgrade based on what is compatible with the environment.

My benefit is doubled since the computer is a useful tool in my business at work as well as other important personal chores.  So the enjoyment I get from the fun environment that Unity provides, I'm also coincidently spending more time and productivity with my work chores.

My computer would be faster if I didn't use any graphics, or turned down the graphics very low and didn't use any effects.  It would be even faster if I didn't load the GUI and worked from a console.  But to expend a second in time here or there isn't so bad a price to pay when you consider the anaesthetic experience it brings.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by knightvoid on 2011-09-12
I installed Ubuntu on two computers, and got the following error on both. 
"Its seems that you do not have the hardware required to run unity. Please choose ubuntu classic at the login screen and you will be using the traditional environment."
```


/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

```and
```

lspci |grep VGA
 lspci | grep VGA  00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

```I got to reply 15 and got Stuck.

As a side note I want to run Compiz eventually, but am starting with unity.
Thanks in advance.

---

### Post by apollothethird on 2011-09-13
> **knightvoid said:**
> I installed Ubuntu on two computers, and got the following error on both. 
"Its seems that you do not have the hardware required to run unity. Please choose ubuntu classic at the login screen and you will be using the traditional environment."
```


/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  2.1 Mesa 7.10.2

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  no
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no

```and
```

lspci |grep VGA
 lspci | grep VGA  00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

```I got to reply 15 and got Stuck.

As a side note I want to run Compiz eventually, but am starting with unity.
Thanks in advance.

You can either disable the blacklisted card check or install Unity 2D from synaptic. 

To disable the blacklisted chard check add "UNITY_FORCE_START=1" to /etc/environment.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

