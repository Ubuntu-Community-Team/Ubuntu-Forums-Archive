---
title: "Newbie as XFCE user"
date: 2010-08-19
forum: General Help
---

### Post by cespinal on 2010-08-19
So.... After having some days experiencing a very laggy Gnome desktop, I said screw it and went for a full XFCE installation. 

I like it, I had been stripping down my gnome desktop in search for a minimal setup and XFCE pretty much delivers this from the first moment. 
I have ran into a couple of issues that, if I don't get to resolve, they will pretty much make me go back to Gnome... 

The first one is the up/down volume and mute media keys.... there seems to be no output when trying them using xev.... 
The second one is the compiz config manager: changes I make in it just wont take effect. When I close it, it is again reverted to the original options. 

For the rest, I love the simplicity, the snappyness and the overall looks... 

Let me hear about some XFCE brothers out there :)

---

### Post by XubuRoxMySox on 2010-08-19
There's a whole "Desktop Environments" section here on UF that can offer alot of help. A mod might even move this thread there, lol.

Xfce is kinda sorta like "Gnome Lite." It has all kindsa cool features but it's faster and, in my opjnion, alot simpler.

Using Xfce with Compiz seems a built-in contradiction though. Compiz is eye candy, and Xfce is meant to go easy on your computer's resources. It's possible to do that, of course, but I don't think many people use the two in combination.

I don't use Compiz, but the Xfce window manager has a little composting for stuff like translucent panels and stuff. 

Are you just using Xfce on top of regular Ubuntu? Did you install "xubuntu-desktop" from the repositories or "Xfce-4?"

I've played with Gnome, Xfce, KDE, Openbox, and LXDE so far. Xfce is my favorite! Sweetly balanced between lightweightness and full-features (the applets are cool - weather and everything in Xfce panel), It's pretty, lighter on resources without being bare-bones or "Win 98ish," and simple enough for even a little dixiedancer to use. :D

Enjoy!

-Robin

---

### Post by cespinal on 2010-08-19
Sorry...double post... disregard this

---

### Post by cespinal on 2010-08-19
Hello Robin, thanks for your kind post. 

So far the experience has been quite enjoyable. Sure Compiz is not meant for a super quick desktop but I have found that the system feels a lot more responsive than Gnome even with full effects on. 
As for the usual nicks and dings coming with this kind of installations, I just got to solve them thanks to Saint Google. I made a xubuntu-desktop install... no more problems for the moment. 

Another big reason I wanted to try this is because i'm becoming dependant of Windows so I'm doing a lot of virtualization. With Gnome I could use either the guest or the host OS alone. With xfce everything runs quite well, so I'm very happy. 

thanks again

---

### Post by NightwishFan on 2010-08-20
Compiz - I think it is trying to use Gconf, either install Gconf, and then go to the XFCE session manager and check enable gnome services, or change compiz to use the flat file backend under preferences in CCSM.

Volume Keys - Not sure here, I have this problem in pure XFCE but not in Xubuntu. Perhaps try Xubuntu if you have not. (No need to reinstall just install Xubuntu-Desktop)

What are your specs by the way. If you are low on ram there is a nice tweak to speed things up. Set the swappiness to be more aggressive at moving data out of RAM. Run this command for temporary:
```
sudo sysctl vm.swappiness=100
```

To make the change permanent, run these commands one at a time:
```
sudo su
cp /etc/sysctl.conf /etc/sysctl.conf.backup
echo "vm.swappiness=100" >> /etc/sysctl.conf
exit
```

---

### Post by cespinal on 2010-08-20
> **NightwishFan said:**
> Compiz - I think it is trying to use Gconf, either install Gconf, and then go to the XFCE session manager and check enable gnome services, or change compiz to use the flat file backend under preferences in CCSM.

Volume Keys - Not sure here, I have this problem in pure XFCE but not in Xubuntu. Perhaps try Xubuntu if you have not. (No need to reinstall just install Xubuntu-Desktop)

What are your specs by the way. If you are low on ram there is a nice tweak to speed things up. Set the swappiness to be more aggressive at moving data out of RAM. Run this command for temporary:
```
sudo sysctl vm.swappiness=100
```

To make the change permanent, run these commands one at a time:
```
sudo su
cp /etc/sysctl.conf /etc/sysctl.conf.backup
echo "vm.swappiness=100" >> /etc/sysctl.conf
exit
```

Thank you very much for taking the time to answer me. 

I solved my compiz issues with this: [http://www.infobarrel.com/How_To_Install_Compiz_On_Xubuntu,_The_Easy_Way](http://www.infobarrel.com/How_To_Install_Compiz_On_Xubuntu,_The_Easy_Way)

And the volume control nicks by binding the commands in this video manually to each media key: [http://www.youtube.com/watch?v=iStCFtrvNnM](http://www.youtube.com/watch?v=iStCFtrvNnM)

This is an AMD Turion with 2gb of RAM. In gnome, RAM usage was always above 30%, whilst in xfce is always below 20% unless I'm using the virtual machine. cpu usage is around 30% while in gnome was always peaking at 70% and 80% with the fan at full speed and the little computer turned into a nice little groin baking machine. 

Your tweak on the other hand, doesn't seem to make any noticeable difference in the amount of ram used. I will report any improvement on this later.

Cheers.

---

### Post by NightwishFan on 2010-08-20
I would not noticeably unless you were very pressed for ram, however on those specs I would not see it being that much use except you will see better performance on the virtual machines.

As for high cpu usage, you might want to see what is hogging it, as that is unusual. Though I am glad you like it.

---

### Post by cespinal on 2010-08-20
Awesome.... I'll make this permanent then. Thank you very much

---

### Post by Elfy on 2010-08-20
moved to support forum - testimonials is NOT for support

---

