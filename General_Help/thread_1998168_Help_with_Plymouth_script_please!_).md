---
title: "Help with Plymouth script please! :)"
date: 2012-06-06
forum: General Help
---

### Post by v4169sgr on 2012-06-06
Hello,

I am attempting to work around this problem:

[http://ubuntuforums.org/showthread.php?t=1997417](http://ubuntuforums.org/showthread.php?t=1997417)

on the hypothesis that the problem is a race condition between the boot sequence and '/' and my raid0 disks being available [I don't know that it is, but would like to see if that the case.]

I read this: [https://wiki.ubuntu.com/Plymouth](https://wiki.ubuntu.com/Plymouth), and have:
* played with plymouth-x11 [very nice]
* installed plymouth-theme-script

I would like to do something like this in my boot process, so Plymouth waits for the user's input before continuing:

```
Show the splash screen

    sudo plymouth show-splash 

Stop the graphical progress indicator

    sudo plymouth pause-progress 

Display a message

    sudo plymouth message --text="pausing boot - press 'c' or space bar to continue" 

Wait for the user to type either 'c', 'C' or space (no return required)

    sudo plymouth watch-keystroke --keys="cC " --command="tee /tmp/c_key_pressed" 

Change the on-screen message

    sudo plymouth message --text="resuming boot" 

Resume the graphical progress indicator

    sudo plymouth unpause-progress
```

But I don't really know how to proceed safely.

I'm an IDOIT, so would appreciate an IDIOT-proof guide :)

Thanks in advance :)

---

### Post by v4169sgr on 2012-06-06
Please help me avoid breaking my system - the payoff will be a script that other people can use tooo as a workaround [if this works!].

Thank you!!! :)

---

### Post by v4169sgr on 2012-06-06
**_Even if you don't know the answer, please recommend this thread to your friends_**. If this works, we could have a workaround for a race condition that may be affecting other people too, while the devs come up with a solution! :)

---

### Post by v4169sgr on 2012-06-06
Posted on AskUbuntu: this question is no longer needed as I now have the answer. Will post the full and gory back on the main thread.

Thanks all for listening! :)

---

