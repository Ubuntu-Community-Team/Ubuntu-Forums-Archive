---
title: "Lost Audio"
date: 2010-09-16
forum: General Help
---

### Post by Yogi2 on 2010-09-16
I'm using Ubuntu 10.04 (Lucid) and have had no major problems with it out of the box.  Yesterday I tried to install VirtualBox so that I could run Windows as a virtual machine.  The software downloaded and installed perfectly from the repository.  I then went to the VirtualBox website, downloaded and installed their current version of VirturalBox.  In this case I could not start the Windows VM session because the DKMS kernel module was not installed.  I installed that module but also installed the DKMS Open Sound System (oss4) module by mistake.  Ever since then I no longer have audio.

I un-installed the oss4 module via the Ubuntu Software Center - the same way I unintentionally installed it - but still no audio.  The Pulse Audio server was the default subsystem before all this happened, but now I can't get any audio at all.  

Can anyone suggest how I can get audio back

---

### Post by -kg- on 2010-09-16
Hi Yogi!

Have you checked to see whether Pulse Audio is still installed?  If it is, you might want to try a re-installation, and if that doesn't work, a complete removal and then reinstall it.

You might want to use Synaptic instead of Software Center.  I don't know whether there is much difference, but Synaptic seems to me to be much more detailed, while Software Center makes it a bit easier to find packages.  They're both GUI front ends for apt-get, so it won't make much difference overall.

If that doesn't work, there are a few command line things you need to issue, and I'm not sure that you might not have to deal with a configuration file or two.  Hopefully someone with a bit more knowledge on this specific problem will find this post.

At least this will bump the thread, with a couple of things to try.

---

### Post by -kg- on 2010-09-16
As promised elsewhere, I have done a little research and found this:

[Howto Install OSS4 in ubuntu 10.04 (Lucid) for better sound quality]("http://www.ubuntugeek.com/howto-install-oss4-in-ubuntu-10-04-lucid-for-better-sound-quality.html"):

> ...the oss4-dkms package is currently broken for Ubuntu ([bug #519577]("https://bugs.launchpad.net/ubuntu/+source/oss4/+bug/519577")), so for the time being use the package from the Opensound website (recommended, see below)

Down the article, it tells you how to reverse changes.

---

### Post by Yogi2 on 2010-09-17
**-kg-** Thanks for your usual generous assistance.  

I tried the steps in the link for a total removal of oss4 and was told at various points that files/commands don't exist.  However, I was encouraged to see the report that all my PulseAudio files are the current ones.  That tells me PulseAudio is in there and oss4 is not.  

In spite of all the software apparently being in place, I still have no audio. Grub shows two other versions of Ubuntu for me to boot into, and neither of them have audio now as well.  I'd think there is a hardware problem, but it all works fine when I boot into Windows.

---

