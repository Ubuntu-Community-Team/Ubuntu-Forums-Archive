---
title: "Overheating on HP Pavilion DV6"
date: 2012-09-24
forum: General Help
---

### Post by amjjawad on 2012-09-24
Hi,

HP Pavilion DV6, Core i5 (first generation), 4GB RAM, 1GB ATI Graphics Card. This machine has only two Operating Systems, Windows 7 and Lubuntu 12.04 64bit.

Long story short, the overheating while using Lubuntu ONLY is something unbelievable, I can't even touch the machine. With Windows, there is heat but LESS. Sad but true.

Any idea/thoughts/suggestion to fix this?

---

### Post by Mark Phelps on 2012-09-24
You could try using Jupiter:

[http://ubuntuforums.org/showthread.php?t=1854019]("http://ubuntuforums.org/showthread.php?t=1854019")

---

### Post by amjjawad on 2012-09-24
> **Mark Phelps said:**
> You could try using Jupiter:

[http://ubuntuforums.org/showthread.php?t=1854019](http://ubuntuforums.org/showthread.php?t=1854019)

Thanks for your reply, Mark.
Actually, Jupiter is already installed and it's totally helpless. I have noticed the overheating from day 1 when I installed Linux but I ignored it. Yesterday, the overheating and the heat was too much that I couldn't really ignore.

---

### Post by agillator on 2012-09-24
I assume this is an older machine and the overheating has started recently. If that is the case, the problem could easily be the heat sink. That has happened to me a couple of times. The solution is relatively simple. My first advice is to take it to a qualified technician and tell him it is overheating. They will check it out and probably put new thermal grease between the heat sink and the cpu. However, if you are handy this is probably something you can do yourself if you are careful. I'm not going to give specific instructions because if you need specific instructions you shouldn't be doing it yourself as you void every warranty in the book and you can destroy your machine. BE ADVISED!! AND WHATEVER YOU DO BACKUP - BACKUP - BACKUP! Oh, yes, did I mention be sure to backup everything regardless of what you do? I will only mention that anyplace that sells computer parts (motherboards, cases, etc.) should have thermal grease you can purchase. 

If it is a relatively new machine, say less than a year old, there is probably another problem. Have someone check it out.

---

### Post by JayKay3OOO on 2012-09-24
Does the machine have a lot of fan noise? If so then this will help.

Pull the back panel off and check the heat sink is not full of dust. I've found this with my laptop that the fan was blowing into a wall of thick dust and the heat was getting stuck in the casing rather than leaving the machine. Same with another machine.

You may need to pull the fan out to get to the heat sink. It looks a bit like a piece of metal with holes in leading the exit of the case. It's not that big.

You can get the dust out using a screwdriver, but make sure you don't let the dust flake over all the other components and don't bend the fins.

Check under the system load app to see if the machine is stuck @ 100% load. If it's not then for sure it's the heat sink.

[IMG]http://i1070.photobucket.com/albums/u491/Joss_Kingston/laptopheatsink1_zps611465dc.jpg[/IMG]

---

### Post by amjjawad on 2012-09-25
This is a One Year + 9 Months Old Machine, running both Windows 7 and Lubuntu 12.04 which is the Lightweight version of Ubuntu and very low on resources, that is why logically, the overheating because of the system itself is something abnormal and not logical (I'm not saying it should never happen because there are some other factors that will affect on the heat).

I'm watching the System Monitor (gnome-system-monitor - I have installed it because Lubuntu comes with LXTask) and the CPU Load is quite NORMAL. With only System Monitor Opened and it's running on the Battery right now, the MAX CPU Load is 8% on one of the Cores while it is 0% on the other. The average is 3% as far as I can tell as shown on Desklet Conky.

The unusual part is: The Temp is between 58c - 60c while idle.
It goes high if I do: sudo apt-get update.
Any operation will make the Temp jumps above 60c.

No, the fan is NOT producing any noise or high sound. ONLY when I turn the machine ON, there is a high sound. Once I login to the Desktop, it's gone.

Before installing Linux, the machine had this overheating issue with Windows 7 when the External Graphics Card was ON. It has switchable Graphics Function so I can select to use the Built-in Graphics (Intel) or the External One (ATI). The sound of the fan was so high and the overheating was too much. Whenever it was working on the Intel Graphic Card (the built-in), the overheating was less but still high sometimes.

I have contacted HP and they advised to do a BIOS Update. That helped only for few days but then, I think the issue is back.

We don't use that machine much daily and if truth to be told, when I use that machine (it's not mine but it's at our home so I use it from time to time) and it happens that I'm using it MORE than the other person is using it, I don't login to Linux, I use Windows 7.
I decided to use Linux the other day and I was shocked when the heat went so high.

IMHO, as far as my experience with that machine, I think it has a Hardware issue that has nothing to do with the System itself.
I thin it needs a cooling fan that I need to buy. I did my best to find one that can help but I couldn't find one. The fan is located on the left top corner and the cooling fans/docks I found had one or two fans in the middle.

I'm using now a Lenovo G570 Laptop and it's Core i5 2nd generation with 4GB RAM and it has NO problem at all no matter how many hours it is on (I keep it on for days) and no matter how many applications I run.

I will try to clean the fan from dust but I don't think it's the issue and I must be very very careful.

---

### Post by TenPlus1 on 2012-09-25
It seems that having both Intel and Ati graphics running at the same time will cause things to heat up considerably inside your laptop, so you will have to check out the following link and turn off one or the other...  I'd recommend disabling Ati gfx and using Intel...

[http://usernamepending.wordpress.com/2011/11/02/getting-back-some-battery-life-in-ubuntu-11-10-by-disabling-discrete-graphics/](http://usernamepending.wordpress.com/2011/11/02/getting-back-some-battery-life-in-ubuntu-11-10-by-disabling-discrete-graphics/)

---

### Post by amjjawad on 2012-09-25
> **TenPlus1 said:**
> It seems that having both Intel and Ati graphics running at the same time will cause things to heat up considerably inside your laptop, so you will have to check out the following link and turn off one or the other...  I'd recommend disabling Ati gfx and using Intel...

[http://usernamepending.wordpress.com/2011/11/02/getting-back-some-battery-life-in-ubuntu-11-10-by-disabling-discrete-graphics/](http://usernamepending.wordpress.com/2011/11/02/getting-back-some-battery-life-in-ubuntu-11-10-by-disabling-discrete-graphics/)

Before checking that link, I'd like to add something.

I rebooted that HP Laptop and entered to BIOS Setup. Then I was doing something else on the other machine (which has different problem :S) and left the HP Screen on the BIOS Setup. If I remember correctly, the whole time while the laptop was on BIOS, the fan sound was high and the heat was high. When I exit the BIOS and logged in, Temp was 72c or something like that. Then, after 1min, it went down and now it's 64c.

At BIOS Stage, I don't think the machine will run on both Graphic Cards at the same time. I just don't know what is going on :/

---

### Post by amjjawad on 2012-09-30
It's been 4 days now so any other suggestion/solution?

---

### Post by amjjawad on 2012-11-12
[CENTER][LEFT][LEFT]I was doing a memory test, rebooted, logged in to Lubuntu and you can see yourself how HIGH the temperature is O_o[COLOR=#333333][FONT=lucida grande]

[/FONT][/COLOR][/LEFT]
[/LEFT]

[IMG]http://i48.tinypic.com/16a2mti.jpg[/IMG][/CENTER]

---

### Post by tharinduNA on 2013-09-17
@TenPlus1, thanks a lot buddy, your method works :KS

---

### Post by amjjawad on 2013-09-20
Just for the record, I still do have that problem, no matter what Ubuntu Flavour I use, no matter what release I choose, all the same.

This is why I can't go FULL Linux with that machine. I still have Windows 7 and I just feel bad each and every time I see it on the list. I wish I could go full Linux but this overheating problem is pain in the neck!

Thanks!

---

### Post by Yellow Pasque on 2013-09-20
Help might be on the way:
[http://www.phoronix.com/scan.php?page=news_item&px=MTQ2NjI](http://www.phoronix.com/scan.php?page=news_item&px=MTQ2NjI)

Also, check out (though you may need to tweak the commands from card0 to card1, for example): [https://help.ubuntu.com/community/RadeonDriver#Power_Management](https://help.ubuntu.com/community/RadeonDriver#Power_Management)

---

### Post by XBNCPRk on 2013-09-22
From what youve described it sounds as though the fan is not running at all once you start linux? Its not a failed fan if it starts briefly when you power on, or while you run under windows.

There are several fan control programs available in the repository. Perhaps download one of them and see if it a) detects the fan, and b) can force it on to control the temps youre seeing.

---

### Post by amjjawad on 2013-12-05
> **XBNCPRk said:**
> From what youve described it sounds as though the fan is not running at all once you start linux? Its not a failed fan if it starts briefly when you power on, or while you run under windows.

Hi and thanks for your reply :)

No, the fan is working and working on FULL power because whenever I am using Linux (Lubuntu), I can hear the loud sound of the fan, even when the laptop is idle and it is so loud and the heat is unbelievable. 

> There are several fan control programs available in the repository. Perhaps download one of them and see if it a) detects the fan, and b) can force it on to control the temps youre seeing.

Applications/Programs like?
As I mentioned, the fan is working but the overheating issue is not yet resolved. I have tired many things, nothing :(

---

### Post by amjjawad on 2013-12-05
In fact, I no longer can use that machine because of the over heating issue. Unless I solve it, I can't use it.

---

### Post by amjjawad on 2013-12-09
> **amjjawad said:**
> In fact, I no longer can use that machine because of the over heating issue. Unless I solve it, I can't use it.

I had some free time so I decided to clean the mess on this machine, removed Lubuntu 12.04 and Ubuntu 12.04 and kept Windows 7. Had problem with GParted (Input/Output disk error) so had to use Windows 7 Disk to fix the MBR. Logged in to Windows, removed the temp files, scan disk, defragment and booted again from Xubuntu 12.04.3 LiveUSB and used GParted to create the needed partitions.

Now, this machine has ONLY Windows 7 and Xubuntu 12.04.3 where I am typing this from.

I realized that no one asked me nor I did provide this:

```
lshw -C display
  *-display               
       description: VGA compatible controller
       product: Madison [Mobility Radeon HD 5650/5750 / 6530M/6550M]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: **[COLOR=#ff0000]driver=radeon[/COLOR]** latency=0
       resources: irq:44 memory:a0000000-afffffff memory:c4400000-c441ffff ioport:4000(size=256) memory:c4440000-c445ffff
  *-display
       description: VGA compatible controller
       product: Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: **[COLOR=#ff0000]driver=i915[/COLOR]** latency=0
       resources: irq:45 memory:c0000000-c03fffff memory:b0000000-bfffffff ioport:5050(size=8)


```

So far, the heat is normal and I am surprised that I was using Lubuntu 12.04 and it has the same Kernel as Xubuntu 12.04 AFAIK and should be the same drivers so why it was overheating with Lubuntu while so far, it is not with Xubuntu? I don't really know!

It is hot but not like before.

I think I will not install additional drivers - [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) and keep using the default ones and see what will happen.

The BEST part is, the fan is no more producing a loud sound and it seems it is not running on its full power so that is a good news.

Will keep an eye and update this thread. If no more issues, I shall mark it later as Solved.

Thanks!

---

### Post by philinux on 2013-12-09
From a terminal what's the output of this now showing.

```
sensors
```

---

### Post by amjjawad on 2013-12-09
> **philinux said:**
> From a terminal what's the output of this now showing.

```
sensors
```

Thanks for posting. Output:

```
 sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +57.0°C  

radeon-pci-0100
Adapter: PCI adapter
temp1:        +58.0°C  


```

---

### Post by philinux on 2013-12-09
This is mine and by the way laptop is acer 1410. Intel® Celeron(R) CPU 743 @ 1.30GHz , Mobile Intel® GM45 Express Chipset 
Running 13.10 ubuntu 64 bit. 
Laptop been on 2 hours. Hard drive temp is 34c
```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +26.0°C  (high = +105.0°C, crit = +105.0°C)

acerhdf-virtual-0
Adapter: Virtual device
temp1:        +42.0°C  (crit = +60.0°C)
```

When I booted into win 7 the other day Core 0 shot up to 52c after an hour.

Yours is quite a bit warmer than mine but whats the crit levels. You can see sensors shows mine.

---

### Post by amjjawad on 2013-12-09
HP Pavilion DV6 - Core i5 1st generation - 4GB RAM - 500GB HDD

```
/dev/sda: 40°C
```

```
uptime
up  3:33,  1 user
```

```
sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +59.0°C  

radeon-pci-0100
Adapter: PCI adapter
temp1:        +59.5°C  

```

Before, with Lubuntu, the temp was much more - check the other posts. I think it reached to 70c

---

### Post by amjjawad on 2013-12-09
This is my other machine:
Lenovo G570
Intel(R) Core(TM) i5-2430M CPU @ 2.40GHz - 2nd generation
4GB RAM
500 GB HDD


```
hddtemp /dev/sda
/dev/sda: 43°C
```

```
 uptime 
up  5:14,  1 user
```

```
sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:         +0.0°C  (crit = +127.0°C)

```

BOTH my Lenovo and HP is currently running Xubuntu 12.04.3 (both updated to the latest updates) and both are fresh new installation less than 48hours ago.

I don't know why 'sensors' is showing different results on these two machines?!

---

### Post by amjjawad on 2013-12-09
Just a minute ago, HP Laptop was OFF all by itself, I didn't even touch it.

The heat is still below 60c as per "sensors" and I have no idea why it was turned off suddenly. Yes, it is plugged in to the power adapter and the battery is fully charged. Weird :/

---

