---
title: "Realtek 8111/8168 Onboard LAN Problem with 10.04 and Windows 7 dual boot"
date: 2010-04-29
forum: General Help
---

### Post by Balok on 2010-04-29
Hello. Sorry if the info I'm trying to find is already out there, but I've looked for a while, and I think I just need somebody to un-confuse me slightly.

Until today I had been using Ubuntu 9.10, and everything was just fine. I installed 10.04 (64-bit desktop) and now I can't get my on-board LAN to work, unless I completely power down my machine, unplug the power and LAN cables, and then boot straight into Ubuntu. Did I mention I'm dual-booting with Windows 7? I think that's important.

This is a Realtek 8111/8168 controller in a Gigabyte motherboard. It seems previous Realtek LAN's have had problems dual booting because when Windows shuts down it puts them in some kind of state that is unusable to Linux. It has something to do with a wake-on-lan setting, but I can't figure out how to turn it off. 

I guess in a way this is more of a Windows 7 question. Sorry. I would ask Microsoft, but I have a feeling they aren't going to be very sympathetic.

I guess I have a solution with the full-blown power down, but I would like a better one. Thanks in advance.

---

### Post by Balok on 2010-04-29
Just as an addendum, I would like to highlight the fact that I had no problem under Ubuntu 9.10 even though Windows was presumably doing its wake-on-LAN thing then. This tells me that it should be possible for Ubuntu to straighten out the state of the LAN hardware itself.

I would like to find a way to tell Windows that it can bother me all it wants while it's running, but it has to behave while it isn't, but I would also be interested in finding a way to fix this within Ubuntu.

---

### Post by yingwuzhao on 2010-04-29
I am in similar situations, my mobo is P7P55D-E Dulexe, and my network card is Realtek 8112L. I am just preparing to install the new Ubuntu 10.04. Now you make me worry.

To turn off Wake-on-lan in windows, go the Device manager as an administrator and choose your network card and then click the tab of power management, there is an "wake-on-lan" option you can un-select.

Please try it and let me know if that solves the problem.
Thanks.

---

### Post by Balok on 2010-04-30
Okay, I'm trying to do what you suggest, but in Windows I'm not really sure where the line is between running as administrator or not. There's no "sudo" that is either there or isn't. I have an administrator account, and there's a little shield next to the device manager. So I think I'm getting it at administrator level. 

Then I uncheck the box next to "Allow this device to wake the computer" in the power management tab. I haven't tried booting Linux yet, because if I simply reboot Windows, the box is checked again. It won't keep the setting.

I'm thinking my problem may be a bit unusual. I tried a different machine last night with a Gigabyte mobo, realtek LAN, and I could dual boot 10.04 and Win 7 without any problem. I didn't even have to change any of the LAN settings. You might be okay. I've just got something strange happening with Windows.

---

### Post by klemes on 2010-04-30
Maybe you could play a little with your BIOS settings like disabling completely Power Management (worthy if it is not a laptop) and mainly disabling Booting from Network option(which in older computers may be referred as PXE agent also).

---

### Post by Balok on 2010-04-30
Just found this:

[http://www.jamesonwilliams.com/hardy-r8168]("http://www.jamesonwilliams.com/hardy-r8168")

I'm going to give that a try rather than expecting Windows to ever work. I'll report back when I can.

---

### Post by dino99 on 2010-04-30
hello guys,

some confusions there: windows work on its own partition and cant interfere with an other Os on an other partition  :lolflag:

the "wake on lan" thing is a setting into your bios, so turn it off.

---

### Post by dino99 on 2010-04-30
try first to power off (unplugged wire) your pc, modem, router, wait 2 minutes then plug them back (general reinit)

maybe something to follow:

[http://ubuntuforums.org/showthread.php?t=702289](http://ubuntuforums.org/showthread.php?t=702289)

---

### Post by dino99 on 2010-04-30
found a tweak to apply with windows:

Wake on Lan after shutdown  --> enable (advanced devices)

---

### Post by Balok on 2010-04-30
Okay that script worked like a charm.

Everything works now.

---

### Post by Balok on 2010-04-30
> **dino99 said:**
> hello guys,

some confusions there: windows work on its own partition and cant interfere with an other Os on an other partition  :lolflag:



Yes it can. Yes it absolutely can. This is not a software interaction. When Windows shuts down it leaves the hardware in a state that is difficult for certain Ubuntu drivers to deal with. That's why completely removing the system power works. It resets the state of the hardware. A restart from Windows to Ubuntu does cause a problem because power is never removed from the hardware. 

That's the difference between a restart, and a full power down.




> **dino99 said:**
> the "wake on lan" thing is a setting into your bios, so turn it off.

That was my first idea. I tried absolutely every BIOS setting I could get my hands on before even searching the forums for this. It was not a BIOS issue in my case. 

My issue was that Ubuntu needed a different driver in order to straighten out what Windows does to my LAN hardware when it shuts down. The script I linked to above solved it perfectly.

---

### Post by yingwuzhao on 2010-05-03
Now the problem has two aspects, one is in windows and the other is in linux.

For windows you want to roll back the network driver to the microsoft one, instead of using the one provided by Realtek, then turn on the feature "wake on lan" in device manage -> network card -> power management. 

For linux, you want to install the tool "ethtool" and in the console do:
sudo ethtool -s eth0 wol g

to also turn on the feature "wake on lan". Then the problem should be solved. If it still doesn't work, then under linux do the following:
sudo ethtool -s eth0 wol d
then do again:
sudo ethtool -s eth0 wol g

Best

---

### Post by ssalazar on 2010-06-13
I have had many problems with this network card.
Mysteriously stopped working on my kubuntu 10.04
I solved the problem, added to rc.local
/sbin/mii-tool --reset

---

### Post by AgentWD-40 on 2010-07-23
Anybody have the script which Valok is referring to? The link posted no longer works...

---

### Post by randyklein99 on 2010-11-01
> **AgentWD-40 said:**
> Anybody have the script which Valok is referring to? The link posted no longer works...

Bump to see this thread continue.  I'm having similar issue.

---

### Post by AgentWD-40 on 2010-11-01
Sorry randyklein99, I had to put a different network card in that machine to make it work correctly. If it's become a huge issue I would suggest you do the same. Below is a link to the one I bought for $10. It works great!

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833127102]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833127102")

---

### Post by randyklein99 on 2010-11-02
> **AgentWD-40 said:**
> Sorry randyklein99, I had to put a different network card in that machine to make it work correctly. If it's become a huge issue I would suggest you do the same. Below is a link to the one I bought for $10. It works great!

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833127102]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833127102")

Thanks.  Are you running both OS's off the same one or slaving a different to each OS?

---

### Post by tlib747 on 2010-11-25
Can't take credit for this, but don't recall where the original post was. Here is what works for me:

# download driver for r8168, and unpack
[http://www.realtek.com.tw/downloads/downloadsview.aspx?langid=1&pnid=13&pfid=5&level=5&conn=4&downtypeid=3&getdown=false](http://www.realtek.com.tw/downloads/downloadsview.aspx?langid=1&pnid=13&pfid=5&level=5&conn=4&downtypeid=3&getdown=false)

# go to driver location
cd r8168-8.020.00/
sudo rmmod r8169
sudo mv /lib/modules/`uname -r`/kernel/drivers/net/r8169.ko ~/r8169.ko.backup
make clean modules
sudo make install
sudo depmod -a
sudo insmod ./src/r8168.ko
sudo mv /initrd.img ~/initrd.img.backup
sudo mkinitramfs -o /boot/initrd.img-`uname -r` `uname -r`
sudo echo "r8168" >> sudo /etc/modules
lspci -v
sudo reboot

---

