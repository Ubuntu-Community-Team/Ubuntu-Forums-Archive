---
title: "Questions about checking driver loaded for a hardware."
date: 2010-04-13
forum: General Help
---

### Post by csh on 2010-04-13
I would like to ask some questions about checking which driver loaded for a hardware.

Information: I am using Ubuntu and Xubuntu version 9.10.

For the following questions, you just need to answer the questions that you know the answer. For the questions that you don't know the answer, you can leave it for other people to answer.

Questions:
1. For all types of hardware (including but not limited to network adapter, video card, sound card, USB devices, etc), if the command 'lshw' configuration does not show the loaded driver for a hardware, but the hardware **work perfectly**, is there any other way to know which driver loaded for that hardware **WITHOUT ANY RESEARCH ON THE INTERNET**, (and for network device, without using "connection information" feature in NetworkManager) ? If yes, how to do it?

2. Does your answer in question 1 will work for external hardware (hardware based on USB, FireWire, etc) and also the other non-pci based hardware? If it will not work, any other ways?

3. For your answer in question 1 above, do I need to install any packages that was not installed by default during Ubuntu installation?

4. For network hardware, "connection information" feature in NetworkManager does show the driver information. But, like stated in question 1, "lshw" command does not show the information about the driver used, then how NetworkManager get information about the driver used for a network hardware?

---

### Post by sandyd on 2010-04-13
> **csh said:**
> I would like to ask some questions about checking which driver loaded for a hardware.

For the following questions, you just need to answer the questions that you know the answer. For the questions that you don't know the answer, you can leave it for other people to answer.

Questions:
1. For all types of hardware (including but not limited to network adapter, video card, sound card, USB devices, etc), if the command 'lshw' configuration does not show the loaded driver for a hardware, but the hardware **work perfectly**, is there any other way to know which driver loaded for that hardware **WITHOUT ANY RESEARCH ON THE INTERNET**, (and for network device, without using "connection information" feature in NetworkManager) ? If yes, how to do it?

2. Does your answer in question 1 will work for external hardware (hardware based on USB, FireWire, etc) and also the other non-pci based hardware? If it will not work, any other ways?

3. For your answer in question 1 above, do I need to install any packages that was not installed by default during Ubuntu installation?

4. For network hardware, "connection information" feature in NetworkManager does show the driver information. But, like stated in question 1, "lshw" command does not show the information about the driver used, then how NetworkManager get information about the driver used for a network hardware?
[B]```

ifconfig
```
[/B]```

lsmod
```
that will list the loaded kernel modules (drivers)

The only issue with that is that it doesn't show the support thats built into the kernel.

---

### Post by csh on 2010-04-13
> **carlee said:**
> ```

lsmod
```
that will list the loaded kernel modules (drivers)

The only issue with that is that it doesn't show the support thats built into the kernel.

Firstly, thanks for your answer. But ...

Question 5: lsmod command only list the loaded module. How can I know that the loaded module are for which device?

For your information, I had tried ifconfig command but it does not show the driver also.

---

