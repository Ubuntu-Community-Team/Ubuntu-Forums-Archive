---
title: "Enable Wireless, Suspend"
date: 2011-03-05
forum: General Help
---

### Post by d5xtgr on 2011-03-05
Hi all
Running Meerkat on a Gateway MT6700 series and am having some weird problems I think may be related.
I can no longer regularly toggle wireless on and off.  The computer has a button (Fn+F2) to enable/disable wireless networking, and it has worked previously on Lynx and Meerkat (and Vista).  It currently works when I boot into Windows 7, and will sometimes work if I restart the computer, but this is not guaranteed.  In the panel, the option to enable wireless is greyed out and cannot be selected (although the ethernet connection can be enabled and disabled).  I don't really understand how to use ifup to do this from the comand line- here is the output of ifconfig, so maybe someone will be able to help me out (ethernet was connected when I ran this):
```
 $ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:df:f6:d5  
          inet addr:164.107.198.168  Bcast:164.107.199.255  Mask:255.255.254.0
          inet6 addr: fec0::b:2e0:b8ff:fedf:f6d5/64 Scope:Site
          inet6 addr: 2002:a46b:ec8f:b:2e0:b8ff:fedf:f6d5/64 Scope:Global
          inet6 addr: 2002:a46b:c711:b:2e0:b8ff:fedf:f6d5/64 Scope:Global
          inet6 addr: fe80::2e0:b8ff:fedf:f6d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:316856 errors:0 dropped:0 overruns:0 frame:0
          TX packets:208529 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:404808996 (404.8 MB)  TX bytes:18973707 (18.9 MB)
          Interrupt:43 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:18841 (18.8 KB)  TX bytes:18841 (18.8 KB)

```Now, maybe it's just that the button is right next to it (Fn+F3), but I can't suspend the computer and I think it is related.  Again, restarting can but does not always fix the problem.  The major difference is that the option on the panel will send me to a black screen with a flashing cursor (I can't actually type here) in the top left.  This also happens at times when suspending from the login screen.  I let it sit like that for 10-15 minutes hoping it would sort itself out, but did not and proceeded to get very hot.  From this screen, the only way I have found to get out is to hold the power button down for a few seconds until the computer turns off abruptly.

---

### Post by Henk Poley on 2011-03-07
btw, `iwconfig` (with a 'w') is for wireless configuration. Your ifconfig only shows a 'eth0' (ethernet) and 'lo' (loopback, machine internal "network"). This either means you are just not connected, or your wireless doesn't work anymore. Bit hard to tell from ifconfig.

You can probably solve this by unloading and reloading your wireless driver. First figure out what driver module is used, for me it is shown by iwconfig.

Then create a file `sudo nano -w /etc/pm/config.d/89_wireless-workaround` with the contents:
```

# unload and reload wireless during suspend.
SUSPEND_MODULES="<your wireless driver goes here>"

```

---

### Post by d5xtgr on 2011-03-13
Sorry for not getting back sooner, as I have noted, the problem is intermittent and it happened to be working last week but not today.  While I have the problem, the output from iwconfig is as follows:
```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```
Does anyone have an idea what causes suspend and wireless to fail together intermittently?

---

### Post by leviathan8 on 2011-03-13
Regarding the suspend problem, download and install the package *uswsusp. *This will generate a new initramfs image, so hopefully suspending will work again. In order to hibernate your computer, use *s2disk* and to suspend use *s2ram*. If s2ram reports a error about not being able to suspend, just use *sudo s2ram -f*. This will force suspension if the computer is not on the whitelist, but use with caution(!!).

---

### Post by d5xtgr on 2011-03-13
Thanks, but that didn't solve the problem.

Used without the -f flag, I get a message saying that the machine is unknown.  When I use the -f flag, I get a screen similar to the alt-F1 login, but it doesn't accept keypresses and I have to hold down the power button for a few seconds (is this what is known as a hard shutdown?)
I consequently had to restart; and the problem is no longer present, which is not unusual after a restart.

Wireless and suspend are both working for the present.  My iwconfig output hasn't changed now that it's working, by the way.

---

### Post by d5xtgr on 2011-03-13
I've noticed something I think may be another symptom: once wireless starts working again after a restart, I am required to log into the network; normally connection is automatic (it is set up to be automatic).

Hope this info helps.

---

### Post by leviathan8 on 2011-03-14
> **d5xtgr said:**
> I've noticed something I think may be another symptom: once wireless starts working again after a restart, I am required to log into the network; normally connection is automatic (it is set up to be automatic).

Hope this info helps.

To my understanding, the connection asks for the keyring password at login, or the network encryption key (WPA/WEP)? If yes, edit the wireless connection (right click on nm-applet => Wireless => Your router's SSID => Edit) and set it "Available to all users".

---

### Post by grahammechanical on 2011-03-14
When the wireless option is greyed out it is because the boot process did not detect an active wireless adapter. In your attempts to get wireless access you may have removed the information (including pass phrase) from network manager. This could be why you are asked to authenticate.

Is it possible to make sure that the wireless adapter is switched on by fn+f12 before booting into Ubuntu? When using Windows do you deactivate wireless using Windows? If so. do not do it.

Consider, there could be dust or something preventing either the fn key from working properly of the f12 and f13 keys from working properly.

When you have this problem, type in a terminal rfkill list. This command will tell you if the wireless is blocked either in software or in hardware.

Regards.

---

### Post by d5xtgr on 2011-03-16
I set the connection to "Available to all users", but the problem recurred anyway.  Wireless was left on the last time I shut down Windows as per grahammechanical.

Rfkill returns
```
$ rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```
which is the same as when it is simply switched off.

I don't think that the Fn key is sticking; the reason being that even if I use the GUI to suspend, it doesn't work properly but simply blanks the screen and gets hot (I normally have no problem using this method).

Thanks all for bearing with me on this.

---

