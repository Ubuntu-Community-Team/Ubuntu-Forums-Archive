---
title: "Complete Newb: Can't Install"
date: 2010-01-01
forum: General Help
---

### Post by camelface on 2010-01-01
Hey, I've just put in ubuntu today. I'm excited about having something different but can't seem to get anything to work. 

For example, let's say my firefox offers some plugins to see flash, I will click on either of the 3 plugins offered and for each one it says: package not found. The same is true in the software centre where it seems none of the software is actually available for me to download. 

I also wanted to add support for mp3 with the download offered at the link below and all these restricted formats but couldn't for the same reason. 

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

I am connected to the internet. Thank you all.

---

### Post by howefield on 2010-01-01
Try opening a terminal (Applications > Accessories > Terminal) and type the following into it.

```
sudo apt-get update
```

Enter your password when prompted, (you won't see it being typed) once this is finished processing, try installing your software again.

---

### Post by Leppie on 2010-01-01
Hi and welcome to the community.

Go to System>Administration>Software Sources, on the General tab, make sure the first 4 check boxes are checked.

To get mp3 support, etc., you will have to add the medibuntu repository. Open a terminal and issue this command:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```

you may want to install w32codecs (or w64codecs for x64 systems) which is a collection of windows codecs:
```
$sudo apt-get install w32codecs
```

libdvdcss2 is necessary for watching dvd's in ubuntu:
```
$sudo apt-get install libdvdcss2
```

---

### Post by camelface on 2010-01-01
it's all good now, thank you very much. For some reason it worked the normal way after trying again. Something must have triggered this but I don't know what. I didn't do anything special. 

I may have another problem but I will reboot first to see if it will work after that.

---

### Post by 3rdalbum on 2010-01-01
The reason it can't find any packages is because your package list doesn't have anything in it apart from what came preinstalled. Usually the Ubuntu installer will get the package list from the server, but if you weren't connected to the Internet when you installed Ubuntu then this obviously wouldn't have been done.

Simple solution though, and you don't even need to go to the command-line. Just go to System > Administration > Software Sources and make sure that the first four repositories are ticked. Close this program and go to System > Administration > Synaptic Package Manager, and click on the Reload button.

Once this has been done, you can install the "ubuntu-restricted-extras" package by doing a search in Synaptic, marking it for installation and then clicking Apply. The Ubuntu Restricted Extras includes pretty much everything you want except DVD decryption support; you can install this by following the instructions at [www.medibuntu.org](www.medibuntu.org) or doing what Leppie suggested.

---

### Post by camelface on 2010-01-02
I will keep all my newb questions in this thread. 

The Update Manager proposes about 167 updates for 100mg. Should I do these? Are there notable improvements? I ask because things are working well for now, like a charm! 

Also, the computer did not boot when I had a USB key in, saying no OS was found on the device, any simple way to prevent the boot from being interrupted by a USB key with simple media on it?

---

### Post by Bartender on 2010-01-02
> **camelface said:**
> I will keep all my newb questions in this thread. 

The Update Manager proposes about 167 updates for 100mg. Should I do these? Are there notable improvements? I ask because things are working well for now, like a charm! 

Also, the computer did not boot when I had a USB key in, saying no OS was found on the device, any simple way to prevent the boot from being interrupted by a USB key with simple media on it?

You're probably used to the Windows world, where updates were mostly security-related.  Ubuntu updates can be almost anything.  New version of the kernel, sometimes big updates to OpenOffice, new versions of Firefox, etc. plus dozens of new versions of little dinky programs that just do stuff in the background that you don't have to worry about.  By all means, install all the updates found, but don't expect any huge differences from what you're seeing right now.  You won't have to reboot the PC unless there's a kernel update.

The USB booting problem should be resolved by going into your BIOS and editing your boot device priority list.  HDD and/or optical drive should be ahead of USB (unless you specifically want it that way).

The BIOS settings have nothing to do with Ubuntu or Windows.  Your PC will follow whatever directions it's given in BIOS before it gets to an operating system.

---

### Post by howefield on 2010-01-02
> **camelface said:**
> I will keep all my newb questions in this thread.

It's probably better to create a new thread for each new topic, also using more descriptive thread titles will help others decide whether or not to read your question.

On updates, most are security related as the version numbers of  applications included in each Ubuntu release remains static, (although there are a few exceptions to this).

You'd be best to take the updates imho. Learn how to create an image of your disk, that way you can re image if you mess things up.

---

