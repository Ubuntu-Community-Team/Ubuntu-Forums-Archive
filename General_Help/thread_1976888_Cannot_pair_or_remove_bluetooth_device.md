---
title: "Cannot pair or remove bluetooth device"
date: 2012-05-09
forum: General Help
---

### Post by sunbird on 2012-05-09
I just did a clean 12.04 install. My Microsoft Bluetooth Notebook Mouse 5000 used to pair just fine in 10.04. Not so now. When I run the bluetooth setup, the machine sees the mouse, but when I click to continue, it says that setup failed.

I should note that bluetooth otherwise works. I.e. I have paired with other devices no problem.

Here's the strange part, the (unpaired) mouse shows up (as disconnected) on the list of devices on the bluetooth drop-down menu. However, when I bring up bluetooth preferences, it is not listed there, so I cannot remove it.

So, this is a two-part question: 1. Any ideas to get my trusty mouse working again? 2. If not, how can I remove the device?

Thanks!

---

### Post by fooman on 2012-05-09
Have you tried setting it up using "blueman" (Bluetooth manager...available in the software center or synaptic)

I find it much easier to configure Bluetooth devices using that over the default Bluetooth app.

Hope that helps.

---

### Post by sunbird on 2012-05-09
> **fooman said:**
> Have you tried setting it up using "blueman" (Bluetooth manager...available in the software center or synaptic)

I find it much easier to configure Bluetooth devices using that over the default Bluetooth app.


Thanks for the tip. I now can remove the device, which is great, but I still can't connect. This is in syslog:

```
bluetoothd[1248]: Connection refused (111)
```

But strangely, the device shows as paired.

This mouse worked fine before the upgrade...

Other ideas?

---

### Post by dado023 on 2012-05-09
same problem here:
[http://i50.tinypic.com/2552wdc.png](http://i50.tinypic.com/2552wdc.png)

cant get it to work, no matter what i do.
In windows this mouse works normal.

---

### Post by sunbird on 2012-05-09
So this is what I did to fix this.

As suggested by the earlier poster, I installed the package blueman:

```
sudo apt-get install blueman
```

The problem was that the Blueman Applet was conflicting with the Bluetooth Manager Applet. You can disable the Bluetooth Manager Applet from the Startup Items menu, but first you have to make it visible:

```
sudo gedit /etc/xdg/autostart/bluetooth-applet-unity.desktop
```

Then change this line to read:

```
NoDisplay=false
```

Save and exit.

Now you should be able to openup the Startup Items and uncheck the Bluetooth Manager. 

Now quit and log back in.

My mouse works now!

---

### Post by mattlezeay on 2012-05-10
I just tried the steps to add my Microsoft Bluetooth Notebook Mouse 5000 and it doesn't work. Am I missing something? I tries to pair but fails each time. Are you using a pin? Thanks for any help, mouse was working just fine until about two days ago, then just wouldn't connect, I removed it and haven't been able to get it added/working since.

---

### Post by dado023 on 2012-05-11
i am trying to use this mouse:
[http://goo.gl/MxBFq](http://goo.gl/MxBFq)

---

### Post by gauravashq on 2013-01-29
I was not able to remove devices from bluetooth manager.
What I did was:

Installed Bluetooth manager
sudo apt-get install blueman

After opening the "blueman" select a device which you want to remove. Try to click on a red circle which says "Remove this device from known devices list". If that doesn't work then after selecting the device (device hardware ID) go to "Device" menu under "file menu Bar" then select a menu option saying "Refresh Services". It should remove the device after saying that "Host is Down".

Thanks,
Gaurav M

---

### Post by os2 on 2013-04-10
> **sunbird said:**
> Thanks for the tip. I now can remove the device, which is great, but I still can't connect. This is in syslog:

```
bluetoothd[1248]: Connection refused (111)
```

But strangely, the device shows as paired.

This mouse worked fine before the upgrade...

Other ideas?

How is this topic solved? I still get this same error with a BT RC.

---

### Post by Strikeiron on 2014-01-22
Sorry I don't like to bother you, but I've got a similar problem with pairing a computer with Lubuntu and an android cell. I tried installing blueman etc, now I can see the bluetooth but I can't pair them... Anyone here could help?
Thanks in advance!

---

### Post by esko-kauppinen-y on 2014-12-13
Where in this thread is the answer to get this problem solved?
I have the same problem. BT mouse is paired but doesn't work, host is down.

---

### Post by deadflowr on 2014-12-13
> **esko-kauppinen-y said:**
> Where in this thread is the answer to get this problem solved?
I have the same problem. BT mouse is paired but doesn't work, host is down.

The OP solved the problem the OP had as of post #5.
How it affects you or anyone else may not work the same.

The solution at the time was for the OP running Ubuntu 12.04.

---

