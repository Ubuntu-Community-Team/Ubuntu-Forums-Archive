---
title: "How can I replace pulseaudio"
date: 2012-03-19
forum: General Help
---

### Post by MooseMagnet on 2012-03-19
Still having various problems with pulseaudio - especially with Skype.
Skype won't quit - it hangs because of pulseaudio - and that's just one problem.

I do not want to 'fix' pulseaudio. I want to remove it and use alsa. How can I do that?

Ubuntu 10.4, Dell Inspiron.

Do you know how I can remove pulseaudio and use alsa instead? Alsa is so much more stable and trouble-free. I do not want to 'fix' pulseaudio. I want to remove it.

thanks.
RB

---

### Post by marinara on 2012-03-20
sudo apt-get purge pulseaudio

---

### Post by Frogs Hair on 2012-03-20
There are some methods easily found with a search for replacing Pulse audio with Alsa ._Make sure_ any instructions are current and compatible with Gnome 3 if using 11.10.

---

### Post by MooseMagnet on 2012-03-20
Can I change the topic somewhat? I asked Skype about the problems I'm having and they said to make sure I have the following installed. How can I know if I do have these installed?

Make sure that at least the following package-versions are installed:

    Qt 4.4.0
    D-Bus 1.0.0
    libasound2 1.0.18 
    PulseAudio 0.9.16 (optional)
    BlueZ 4.0.0 (optional)

thanks,
RB

---

### Post by Paqman on 2012-03-20
> **MooseMagnet said:**
> How can I know if I do have these installed?


[Synaptic]("apt:synaptic") Package Manager is a good tool for this kind of thing. Go ahead and install it and then filter for those package names and "installed packages" and it'll show you what versions you have.

---

### Post by MooseMagnet on 2012-03-20
Oh dang. I'm being a burden to the community.
I've used Synaptic Package Manager 100s of times, and did my best to understand what you suggested. But I don't have a clue what you mean by "filtering" and "installed packages." So sorry to be so dense.....
RB

---

### Post by Elfy on 2012-03-20
> **MooseMagnet said:**
> Oh dang. I'm being a burden to the community.
I've used Synaptic Package Manager 100s of times, and did my best to understand what you suggested. But I don't have a clue what you mean by "filtering" and "installed packages." So sorry to be so dense.....
RB

Couple of for instances ...

You can see that I have libasound at 1.025 and d-bus is at 1.4.18

Hope that helps.

> I'm being a burden to the community.No you're not :)

---

### Post by MooseMagnet on 2012-03-20
I followed these instructions and fouled up the whole thing.

[http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/](http://howto.blbosti.com/2010/04/ubuntu-make-alsa-default-instead-of-pulseaudio/)

How can I get pulseaudio back like it was before?

Such a hassle just to get proper sound in Skype. What am I doing wrong?

---

### Post by MooseMagnet on 2012-03-20
I'm way beyond my ability and understanding here. 
Frustrating - just trying to get the sound to work with Skype.

---

### Post by MooseMagnet on 2012-03-20
OK. I've got it all back to where it was, and have identified which packages are installed - except QT. 
There's qt 4, and qt, ... ?
What is it and which should I install?
It's a C++ addition, or a backport, or ?

Skype says I need to have Qt 4.4.0

All the other required packages are installed, but I can't tell what to install as far as Qt.

---

### Post by Bobhuber on 2012-03-20
> **MooseMagnet said:**
> OK. I've got it all back to where it was, and have identified which packages are installed - except QT. 
There's qt 4, and qt, ... ?
What is it and which should I install?
It's a C++ addition, or a backport, or ?

Skype says I need to have Qt 4.4.0

All the other required packages are installed, but I can't tell what to install as far as Qt.
Go to the middle bar in synaptic where it says version and you can see what the package you have highlighted is.You need gt 4 (4.4 or higher) which I don't think has anything to do with your sound problem.

---

### Post by PhantomTurtle on 2012-03-20
I'm not sure how you can get pulseaudio back but it says on the Skype for Linux blog that the Skype 2.2 beta fixes that pulseaudio problem in Ubuntu. Look here for more details: [http://blogs.skype.com/linux/2011/04/2_2_beta.html]("http://blogs.skype.com/linux/2011/04/2_2_beta.html").

---

