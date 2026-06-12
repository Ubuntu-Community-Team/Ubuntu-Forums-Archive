---
title: "I have a problem"
date: 2011-09-01
forum: General Help
---

### Post by jack_aragon on 2011-09-01
Good day!!
I am from Colombia, and i am a new user of ubuntu, I tried to install Ubuntu on my desktop computer, so when i  restart pc, the keyboard and mouse both are lost, i can`t use and i can´t to install Ubuntu, i don`t have idea what happened.

another problem is about my laptop, i have a mac and i installed a virtual machine and create on it, well i install satisfactory Ubuntu, but when i insert a USB or another device on ubuntu don't  recognize anything.

Really I don`t know what i have to do, thanks for any help, and excuse me for my english.

---

### Post by mikewhatever on 2011-09-01
Hi, and welcome to the forums.

Are they USB keyboard and mouse? If so, you may need to enable legacy support in the BIOS.

Did you use VirtualBox? If so, you need to install a separate VirtualBox Extension Pack -> [http://download.virtualbox.org/virtualbox/4.1.2/Oracle_VM_VirtualBox_Extension_Pack-4.1.2-73507.vbox-extpack](http://download.virtualbox.org/virtualbox/4.1.2/Oracle_VM_VirtualBox_Extension_Pack-4.1.2-73507.vbox-extpack)

PS: Try using a more descriptive thread titles in the future, and also try providing more info on the problem. In short, help us help you.

---

### Post by 3rdalbum on 2011-09-01
Just to explain what the earlier poster said about Virtualbox: The "virtual machine" will not grab control of USB devices by default. It assumes that the "host OS" (the operating system running on the actual hardware) should take precedence for these devices, so it leaves them alone. If both operating systems tried to use these devices at the same time, very bad things would happen.

The better virtual machine programs will have some sort of option in their settings (or an installable plugin) that allows the virtual machine to access specified USB devices directly, assuming the host OS is not using them. Depending on your software, you should look for such an option in the preferences/settings for your virtual machine.

---

