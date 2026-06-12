---
title: "Virtualbox problems"
date: 2011-07-30
forum: General Help
---

### Post by ghost25 on 2011-07-30
Hey guys, got an interesting problem, hoping someone can help me out here.

I'm running Ubuntu 11.04 on a Compaq Presario CQ62, with factory specs. I have downloaded and installed VirtualBox 4.1.0 r73009, and successfully installed Windows XP SP3 and Windows 7. However, I have now hit a problem.

When I go to Settings for either virtual machine, I get an error that says "Invalid settings detected". It doesn't matter what I try to change or adjust, this message will not disappear. I do not currently have USB support for the Virtual machines, but it's not a big concern to me at this time.

This is causing me a bit of a headache. I don't know what commands I need to issue or what information I can offer to get the readout of what's not working right. I am very comfortable using Terminal, but have no idea what to look for or where to go. (And, before telling me to Google it, I've been searching Google for the better part of this week trying to find information... nothing.) Any help here would be greatly appreciated.

---

### Post by dim_hyder on 2011-07-30
How was virtual box downloaded and installed via apt-get or manually?

If you do not require the USB support maybe remove the version installed and installed virtualbox ose from the repository via software centre.

I'm fully up to date and have v 4.0.4_OSE r70112

---

### Post by jerrrys on 2011-07-30
durning setup, did you assign more ram or more hdd space than you physically have?

host + guest#1 + guest#2 cannot equal more then you physically have if you are running both guest at the same time.

also you can download the usb package from the virtualbox site.

---

### Post by ghost25 on 2011-07-30
> **dim_hyder said:**
> How was virtual box downloaded and installed via apt-get or manually?

If you do not require the USB support maybe remove the version installed and installed virtualbox ose from the repository via software centre.

I'm fully up to date and have v 4.0.4_OSE r70112

VirtualBox was downloaded manually, and installed manually as well. Do I maybe need to go into the package manager and uninstall it that way, then go through Terminal and apt-get it instead? If so, is there any particular version that I need to be aware of to enter?

> **jerrrys said:**
> durning setup, did you assign more ram or more hdd space than you physically have?

host + guest#1 + guest#2 cannot equal more then you physically have if you are running both guest at the same time.

also you can download the usb package from the virtualbox site.

No, I have a 250GB HDD that I allotted 20GB of, and IIRC I have 1GB of RAM so I allotted something like 192MB of RAM initially. But, how could I limit the memory used by host + guest#1? I don't include guest#2 because I only ever use one virtual environment at a time.

---

### Post by dim_hyder on 2011-07-31
To remove from the terminal run:

sudo apt-get remove virtualbox-4.0

(if this does not work search for the correct title for virtualbox with:
 dpkg --get-selections | grep virtualbox
and replace virtualbox-4.0 with the version displayed)

To install the opensource edition:

sudo apt-get install virtualbox

---

