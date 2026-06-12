---
title: "nVidia &amp; Terminal Troubles"
date: 2006-02-06
forum: General Help
---

### Post by xMist on 2006-02-06
Hello!  I'm new here.  Obviously.  I'm also completely new to Linux and its terminal.  I have had a bit of experience in DOS and coding in Visual Basic, but that's about it.  Oh, and some assembly.  Yeah.

Anyway, I'm trying to get my nVidia graphic card up and running.  Ubuntu is working fine through it right now, but I doubt it's got the right drivers loaded because even when on the desktop and I click and drag for a big box selection box to appear, when it gets big, it gets shaky.  My computer is relatively fast, too - under Windows no such lag is apparent.

I've gone through [this]("http://ubuntuforums.org/showpost.php?p=406856&postcount=4") guide because my GPU is an nVidia GeForce FX 5200, but whenever I get to the sudo apt-get install nvidia-settings part, it tells me the package or something is missing.  Do I need to download anything?  Or am I doing something else wrong?

Also, while (or if) anybody is reading this, do they have any good links as to how to get Ubuntu to work with my MS wireless keyboard and mouse and/or my Linksys WUSB54G?  I have learned that I need to use something like ndiswrapper but I'm completely lost as to what to do with it.  Any help or links would be appreciated.  Thanks.

-Bobby

---

### Post by cetol on 2006-02-06
Hi Bobby,

I have the same graphics card, and installing the nvidia drivers has been problematic for me as well, however, the guide you linked to did work for me.

First make sure that you have all the repositories enabled in the synaptic package manager. Search the forums for detailed instructions on this. (I am at work on a *&^%!!! windows machine) and dont remember exactly how to accomplish it.

Open a terminal and

sudo apt-get update

then try installing the nvidia-settings

If you want the latest drivers download them from nvidia. In order for the installation to be successfull you need to make sure the kernel source is installed as the nvidia installer looks for it when compiling the module.

You should also install 

sudo apt-get install build-essentials

also 

sudo apt-get install gcc-3.2 

if you are using a kernel that is 2.6.12 or earlier (if this is incorrect anyone feel free to correct me). I read somewhere that later kernels use gcc-4.0, which is installed with the buid essentials package.

I also recommend running the automatix script found in the forums as well. It installs a lot of neat things for you automatically.

Hope this helps

Chuck

---

