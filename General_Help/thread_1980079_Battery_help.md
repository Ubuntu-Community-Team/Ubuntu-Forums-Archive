---
title: "Battery help"
date: 2012-05-14
forum: General Help
---

### Post by prshnth23 on 2012-05-14
[B][FONT=Arial]First of all,I know battery issues have been discussed a million times here but please help me out if you can.I have a lenovo Z570 with following specs

i5 processor,4gb ram,intel hd 3000 and nvidia gpu and a 750gb hdd

Im dual booting windows and ubuntu 12.04.My problem is that my ubuntu gives me only 2hrs.I googled around a bit and found the following stuff to help me.
1)Disabling my dGPU(which I dont mind cos I dont use ubuntu for gaming)
2)Using bumblebee-website says its for optimus enabled laptops
3)TLP advanced power manager
My issue is that I have an external button to switch between intel hd and nvidia and im not sure which of the above I should do.
        Also TLP webpage says that the kernel power issue has been dealt with for 12.04 and no ACPI=Force(or something,I dont remember clearly) is required.Same is the case with [/FONT][/B][B][B][FONT=Arial]enable_rc6=1(not required in 12.04).Are these true?
Should i stick with TLP or consider bumblebee or directly disable my DGPU using the procedure here [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)

What is my best option to increase my battery life?Please help guys.I just cant live with 2 hrs on my notebook[/FONT][/B]

[/B]

---

### Post by Lekensteyn on 2012-05-14
1) Would be a good idea.
2) Lenovo IdeaPad Z570 seems to be an Optimus laptop
3) no experience.

I would not recommend noacpi, it likely increases power usage even more and has other side -effects like unable to suspend/hibernate. The other param you remember is possible pcie_aspm=force. It should not be necessary, but if you want to try it, [http://askubuntu.com/q/68372/6969](http://askubuntu.com/q/68372/6969) Be careful when modifying boot params though.

The rc6 changes are not necessary, see [http://askubuntu.com/q/98602/6969](http://askubuntu.com/q/98602/6969)

To disable your dGPU, I suggest you to install bbswitch or Bumblebee. Bumblebee also installs the bbswitch module, more information about Optimus+installation instructions for Bumblebee [http://askubuntu.com/q/36930/6969](http://askubuntu.com/q/36930/6969)

---

### Post by prshnth23 on 2012-05-15
Thank you lekensteyn.I installed Bumblebee and now my battery life is close to 4hrs.Would you also please help me out in this post that I saw on the forum somewhere
**"I've been able to more than double the battery life of my netbook by  turning off a bunch of services I don't need, and unloading their kernel  drivers.**  **Use service --status-all to see what's running on your system, and service <service-name> stop to shut it down.**
  **Use lsmod to see what kernel modules are loaded, and rmmod <module> to unload it.**
  **If/when you want to bring things back, easiest way is to simply reboot.**
  **Sometimes you also need to kill daemons or programs that are using  the service or driver before they can be turned off.  Look at output  from ps aux to see what's running, and kill -9 <pid> to terminate them.**
  **Services I usually turn off include:  Ubuntu One, ssh, apache,  databases, avahi, pulseaudio, cups, apparmor, acpi-daemon, bluetooth.   Modules I unload:  The whole audio stack, usb_storage, webcam drivers,  wireless, bluetooth.  (Some services like audio don't die easily.)**
  **I've even gone as far as shutting down x (service gdm stop) and working entirely just from consoles, which let me stretch my netbook battery life to nearly 8 hours."**
So I tried something and got this
service cups stop
stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.81" (uid=1000 pid=3628 comm="stop cups ") interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
What does this mean?

---

### Post by Lekensteyn on 2012-05-15
Stopping a service require adminstrative (root) privileges. To stop a service, use something like *sudo stop cups*. I suggest not to randomly turn services off. The most power can be saved by disabling radio (i.e. wireless and bluetooth). Use tools like *powertop* to watch power use.

---

