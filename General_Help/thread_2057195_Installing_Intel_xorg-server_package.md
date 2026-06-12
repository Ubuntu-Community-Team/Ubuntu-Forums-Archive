---
title: "Installing Intel xorg-server package"
date: 2012-09-13
forum: General Help
---

### Post by rickm1945 on 2012-09-13
I had a previous post about "My Unity" and Epodx64 said to try the Intel xorg-server for the i9xx driver package to maybe solve my resolution problem.
This is my post for the "My Unity" problem.

[http://ubuntuforums.org/showthread.php?t=2054992](http://ubuntuforums.org/showthread.php?t=2054992)

and this is my post for the resolution problem on my laptop.

[http://ubuntuforums.org/showthread.php?t=2014562](http://ubuntuforums.org/showthread.php?t=2014562)

I found the Intel xorg-server package, I think, but I have no idea how to install it and then install the i965 driver which Epodx64 was referring to. To get the resolution on my laptop resolved would make my Ubuntu day.

---

### Post by snowpine on 2012-09-13
The correct name of the package is xserver-xorg. If your Ubuntu has a GUI then it is already installed. You can verify this with:

```
apt-cache policy xserver-xorg
```

To identify your video card, please post the output of:

```
lspci | grep VGA
```

---

### Post by rickm1945 on 2012-09-13
> **snowpine said:**
> The correct name of the package is xserver-xorg. If your Ubuntu has a GUI then it is already installed. You can verify this with:

```
apt-cache policy xserver-xorg
```To identify your video card, please post the output of:

```
lspci | grep VGA
```

```
richard@RichardM:~$ apt-cache policy xserver-xorg
xserver-xorg:
  Installed: 1:7.6+12ubuntu1
  Candidate: 1:7.6+12ubuntu1
  Version table:
 *** 1:7.6+12ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
richard@RichardM:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
richard@RichardM:~$ 

```
 have been working on my resolution since April 2012 and it is still 1024x768. In Windows it is 1368x768 and is nice.
Here are he other post if your interested.

[http://ubuntuforums.org/showthread.php?t=2014562](http://ubuntuforums.org/showthread.php?t=2014562)
[http://ubuntuforums.org/showthread.php?t=2054992](http://ubuntuforums.org/showthread.php?t=2054992)

I have to run "nomodeset" and can't take advantage of 3-D graphics.

---

### Post by snowpine on 2012-09-13
Apologies, I am not familiar with that specific video card.

If you already have other people helping you in the other thread then my advice is to continue to post there rather than starting a new thread.

Hopefully I was able to clear up your question about xserver-xorg and you can mark this one solved?

---

