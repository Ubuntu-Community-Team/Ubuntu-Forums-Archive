---
title: "Minimizing Resources"
date: 2011-12-18
forum: General Help
---

### Post by xedth2 on 2011-12-18
SO I'm a college student and I know I'm getting a netbook for Christmas.  The specs on the netbook said the battery should last for up to eight hours which I don't think I'm going to get that much without closing out some services.  So let's say I need to be able to run on battery for at least six hours straight without being near an outlet.  What are services that I can shut down without causing me to have a major problem?  And is there any other window manager that runs lower on resources than GNOME?  I was looking at XFCE but I'm not sure.  And no I don't want to run only command line, as fun as that is I don't think I'll be able to be running at full personal efficiency on that.  So any body got any ideas?

Thanks

---

### Post by WorMzy on 2011-12-18
Go with a 32-bit operating system (to minimize RAM usage), and use something light-weight, like Openbox rather than a full blown desktop environment. I believe that Lubuntu uses Openbox, if you want to stick with *buntu, otherwise, I'd recommend Arch Linux -- a very minimalistic build-it-yourself distro.

---

### Post by nothingspecial on 2011-12-18
Lubuntu runs like lightening on my netbook.

---

### Post by snowpine on 2011-12-18
Jupiter is a nifty utility for optimizing your power settings: [https://launchpad.net/~webupd8team/+archive/jupiter](https://launchpad.net/~webupd8team/+archive/jupiter)

---

### Post by Rex Bouwense on 2011-12-18
I am also using Lubuntu on my EeePC netbook and it is super fast.  You can however lose some of that speed if you start to bloat it up.  Check it out your might like it.  It comes with Abiword so you may have to install Libre Office if that is too light for your school work.
I have recently discovered Bodhi Linux which installs very minimal and you only install what you want.  I have not used it extensively yet but if you aren't opposed to trying something else check it out as well.  It is based on Ubuntu I believe.

---

### Post by QIII on 2011-12-18
+1 on Bodhi.

It's an Ubuntu derivative, so it will generally be familiar.  It is extremely light.

I went to my garage and pulled out a 10 year old Dell Latitude C610 with a PIII, 512M and a nearly dead battery that would take 10 minutes to boot to XP and that took about half of the 20 minutes I could get out of a freshly charged (or as charged as I could get it) battery.

When running Bodhi, it starts in a few seconds, does everything I need it to do and the half-dead battery lasts about 90 minutes.

It is very minimal, though.  It reminds me somewhat of the old days when we installed Linux from a bunch of parts in a box and had to figure out what we wanted to add.  But you can use Synaptic or apturl to do a one-click install from Bodhi's site.  There is some documentation on how to get apturl to work, since it won't right out of the box.

The good:  Light, fast, easy on resources.  E17 desktop environment is actually sort of nice.
The bad:  VERY minimal.  Wireless setup may be frustrating, since it is already frustrating enough with heavier Ubuntu siblings.

---

### Post by xedth2 on 2011-12-19
Thanks I'll defiantly look into Bodhi.  I'm a CS major, the netbook is basically to take notes in class and quick code compiles.  The only things I really need are, gcc, g++, Google Chrome(because I use Google Docs for my office suite), and just want zsnes so I have something to play on.  And I'll need JAVA because thats how my school gets there authentication for non-M$ platforms.  I also use Python quite frequently and I know eventually I'll need probably Eclipse for my JAVA class.  And I'll probably install a C++ IDE sometime if I can ever figure out how to use sizers right, stupid VS and its giving me the easy way.  But I like to use Geany and command line for my C and C++ programming, and IDLE for Python so it shouldn't be to bad on resources.  Also I remember years ago, I think it was around '04 and '05 I used Fedora 6, I remember logging in using command line and then running startx to start the GUI does anybody know of any tut's to get Ubuntu and Bodhi to do that?  

Thanks for the replies.

---

### Post by xedth2 on 2011-12-19
What about [Ubuntu Minimal]("https://help.ubuntu.com/community/Installation/MinimalCD")? I just found it, I feel like this is a good idea, then I just install which ever window manager I want.

---

### Post by nothingspecial on 2011-12-19
Yep, that's one way :)

---

### Post by xedth2 on 2011-12-19
And I'm thinking XFCE for a window manager, from what I've read it seems to be the best balance of features over resource consumption.

---

### Post by snowpine on 2011-12-19
Good idea but remember a minimal install won't include any power management features until you deliberately install them. If you choose Xfce then the package **xfce4-power-manager** will give you what you need.

If you want a shortcut to Ubuntu + Xfce then you can just try **Xubuntu**, you don't necessarily need to go through the process of minimal install (although it sounds like a fun project you might enjoy for educational purposes).

---

### Post by xedth2 on 2011-12-19
Yeah I'll probably do the minimal install just because I kind of want to.  Is there anymore power management things? I don't really know to much about them.  I went through today on my laptop and uninstalled gnome and tried Enlightenment, E16, but didn't care for it that much.  I'm also looking for abetter file manager.

Thanks for the tips.

---

### Post by xedth2 on 2011-12-20
So I went through and installed the minimal Ubuntu on a virtual machine last night.  At the very end it asked me to select a package to install with the system.  I choose Xubuntu for XFCE but in doing so it also installed a bunch of other applications, I don't even know what services it might have installed.  Is there any way to install Ubuntu but basically get it command line only with practically nothing else installed?

---

### Post by nothingspecial on 2011-12-20
You should have chosen xfce4 rather than xubuntu. Right now you have what you would have if you had downloaded Xubuntu and installed that. Try again as it's just a vm and just install xfce4. Or if you just want a cli install, don't choose anything.

---

### Post by snowpine on 2011-12-20
> **xedth2 said:**
> So I went through and installed the minimal Ubuntu on a virtual machine last night.  At the very end it asked me to select a package to install with the system.  I choose Xubuntu for XFCE but in doing so it also installed a bunch of other applications, I don't even know what services it might have installed.  Is there any way to install Ubuntu but basically get it command line only with practically nothing else installed?

Yes, doing so is called a "minimal install" and you can read more here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

If you chose Xubuntu then you have Xubuntu, you do not have a minimal install (not that there's anything wrong with Xubuntu of course).

---

### Post by xedth2 on 2011-12-20
Yeah I just figured that out.  I forgot about the manual selection at the screen where I choose Xubuntu.  I'm trying it now to see what happens.

---

### Post by xedth2 on 2011-12-20
So I installed it as command line only, now I did "sudo apt-get install wmaker" but I'm getting could not open display error.  So I just did "sudo apt-get install xinit" and then ran startx and it works fine now.  What exactly is it that xinit does?

---

### Post by snowpine on 2011-12-20
> **xedth2 said:**
> So I installed it as command line only, now I did "sudo apt-get install wmaker" but I'm getting could not open display error.  So I just did "sudo apt-get install xinit" and then ran startx and it works fine now.  What exactly is it that xinit does?

X is the underlying GUI in Linux, and "init" generally means "start." So in this case xinit provides the command startx which allows you to init the GUI.

---

### Post by xedth2 on 2011-12-20
Okay so everything is working so far, got XFCE4 working with startx.  I installed the software center but theres a slight issue.  Whenever I open the software center it won't install anything, and it doesn't ask for the password either.  If I try and open Synaptic it asks me for the password but when I type it in, and I know it's right, it tells me its the wrong password.  When I do "sudo software-center" it works just fine and so does opening Synaptic that way.  Why is this happening?

---

### Post by snowpine on 2011-12-20
> **xedth2 said:**
> Okay so everything is working so far, got XFCE4 working with startx.  I installed the software center but theres a slight issue.  Whenever I open the software center it won't install anything, and it doesn't ask for the password either.  If I try and open Synaptic it asks me for the password but when I type it in, and I know it's right, it tells me its the wrong password.  When I do "sudo software-center" it works just fine and so does opening Synaptic that way.  Why is this happening?

You need to install **gksu** and then you can launch it with:

```
gksu software-center
```

This is covered in the how-to I linked to above: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

---

### Post by xedth2 on 2011-12-20
gksu is installed, if I run "gksu software-center" from the terminal it asks me for the administrative password, I type in the password and it tells me it's wrong, I know its right, it should be the same for the user I'm currently logged in as.

If I create a launcher on the desktop with "gksu software-center" in it, it works fine but doesn't work through the terminal.  I don't understand why that is.

---

### Post by snowpine on 2011-12-20
Here is some general troubleshooting advice for sudo/gksu issues: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

One thing to double-check is that your user is in the **admin** group because only admin users can use sudo/gksu. 

```
groups <username>
```

If not in the admin group, another privileged user (or you can reboot to recovery mode) can add you to admin group with:

```
sudo adduser <username> admin
```

Beyond that general advice... I am not a Software Center user so I'm hoping another forum member can help you out with the specifics? :)

---

### Post by xedth2 on 2011-12-20
My user is the only user, short of root, on the machine.  It is in the admin group just checked.

---

### Post by WorMzy on 2011-12-20
gksu may use su as a back-end, depending on what gconf (or possibly dconf now) has it set to use.

Try using gksudo instead.

---

### Post by xedth2 on 2011-12-20
So I did a dual boot with windows 7 and the ubuntu minimal, when I boot from the thumb drive I get the grub and choose which os to go into but when I boot from the hard disk where both OS's are installed it just jumps right into windows.  Anybody got any ideas because this one just doesn't make sense.

---

### Post by WorMzy on 2011-12-21
Presumably the thumb drive has grub installed to the boot sector, but your hard disk has Windows' bootmgr installed to the boot sector. Run the [Boot Info Script]("http://sourceforge.net/projects/bootinfoscript/") and post the results here so we can be certain + advise you how to proceed.

---

### Post by xedth2 on 2011-12-21
Alright I ran the script and I'll post the output as an attached text file.  I haven't dug through it yet but I will soon to see what I can make out of it.  The RESULTS.txt is what the script built and I redirected the output of the command to out.txt.

I just read through the RESULTS.txt.  sda is the hard drive physically in the machine.  sdc is the thumb drive that I installed Ubuntu from.  After reading the location of Grub2 as being in sdc I have no doubt that the boot loader for the dual boot is on the thumb drive.  I know I've dealt with a similar issue before so I'm going to try and fix it.

Thanks for all the help.

---

### Post by xedth2 on 2011-12-21
Okay so I was able to fix it using "[sudo grub-install /dev/sda]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")".  Now it's time to see if my wireless is working, through command line.

---

### Post by xedth2 on 2011-12-21
So I was able to install my wireless driver and get my wireless working without any issues as long as my wireless didn't have a key on it.  I put the key back on it and the key has a ! in it.  Bash didn't like this.  Is there anyway to force bash to ignore the ! or maybe like put the key in quotes?

---

### Post by nothingspecial on 2011-12-21
Use single quote or put a \ before the !

---

### Post by xedth2 on 2011-12-21
Well that fixed that issue but wouldn't let me connect, I'm trying wpa_supplicant but 5hats not working either, I push the output of wpa_passpharse into wpa_supplicant.conf and then tried to run wpa_supplicant -ieth1 -c/etc/wpa_supplicant.conf and it just keeps getting stuck After WPA: Grouping rekeying completed with (bunch of hex) [GTK=TKIP]

It may not be stuck but its taking forever. So I'm not sure.

After the wpa: grouping it says

CTRL-EVENT-DISCONNECTED bssid=morehex reason=0

Then it just starts all over

---

