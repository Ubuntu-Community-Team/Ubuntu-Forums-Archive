---
title: "MythBuntu 12.04 and V4L-DVB recompile with patch please help"
date: 2012-05-03
forum: General Help
---

### Post by Morten ML on 2012-05-03
Hi all

I am trying to make use of my tvtuner usb (PCTVSystems QuatroStick-nano 520e), but i can't figure out what to do.
From this page i gather that i should be able to use the digital part of the stick:
[http://www.linuxtv.org/wiki/index.php/PCTVSystems_QuatroStick-nano_520e]("http://www.linuxtv.org/wiki/index.php/PCTVSystems_QuatroStick-nano_520e")

I assume I have to patch, recompile and install the V4L-DVB and when that is done i am good to go.

My problem is i don't know how to patch the V4L-DVB. From this page [http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers]("http://linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers") - using the basic approach - I have to "... add the patch file as a line to the {kernel-version}_series file in the packports dir."
But i cannot find the "{kernel-version}_series" in the backports dir. (I assume that "packports" is a spelling mistake).

any help would be appreciated.

Thx in advance

/Morten

---

### Post by gordintoronto on 2012-05-03
There is a mythbuntu forum, you might get better responses there.

Good luck!

---

### Post by najs on 2012-05-05
Hi Morten,

No, you don't have to compile any thing. Its a Perl script that needs to be patched. It is easier to use the alternative solution mention on that page.

> Alternatively, you can download the extracted firmware directly from [this link]("http://www11.zippyshare.com/v/17827014/file.html%7Cdvb-demod-drxk-pctv.fw")Download the firmware file from the link and store it in /lib/firmware
Make sure you name the file dvb-demod-drxk-pctv.fw otherwise the device driver won't find it.

I also got the same usb tvtuner and I have the DVB-T tuner working successfully.

/najs

---

### Post by Morten ML on 2012-05-06
Hi Najs, G and new viewers

@Najs:
Thx for your reply. Nice to know somebody has it working - if you hadn't posted I probably would have given up. Can you confirm that 11.10 works or did you use another version of MythBuntu?

This is not a solution but simply my progress. 
**Short answer:**
MythBuntu 12.04 (both 32 and 64) detects the 520e in another way than Mythbunty 11.10. This other way doesn't work atleast for DVB-C. So use 11.10 64 bit instead &#8211; haven't tried 32 bit.

**Long answer:**
I tried the following on Mythbuntu 12.04 32 and 64 bit and on Mythbuntu 11.10 64 bit.

I downloaded the file "dvb-demod-drxk-pctv.fw" from [http://www11.zippyshare.com/v/17827014/file.html%7Cdvb-demod-drxk-pctv.fw]("http://www11.zippyshare.com/v/17827014/file.html%7Cdvb-demod-drxk-pctv.fw")
link to it from here:[http://www.linuxtv.org/wiki/index.php/PCTVSystems_QuatroStick-nano_520e]("http://www.linuxtv.org/wiki/index.php/PCTVSystems_QuatroStick-nano_520e")

Copied it to the /lib/firmware/ using sudo.

From [http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers]("http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers")
I got:
```
sudo apt-get install git
git clone git://linuxtv.org/media_build.git
cd media_build 
sudo apt-get install patchutils libproc-processtable-perl
./build
```

Now reboot.

After this the command "lsusb" showed:
*Bus 001 Device 002: ID 2013:0251 Unknown (Pinnacle?)*

and "ls -i /dev/dvb/"
[I]total 0
drwxr-xr-x 2 root root 120 May  5 18:54 adapter0[/I]
(adapter0 in blue)

both commands the same on all OS, but when entering Mythtv backend the screens differ.

I should also state that i downloaded the "[I]New Mythbuntu
Install[/I]" for all versions. ([http://www.mythbuntu.org/downloads]("http://www.mythbuntu.org/downloads"))

On a side note I also had the "*PCTV Hybrid Stick Solo 340E*" connected at the same time as the 520e, which seemed to be the reason why i couldn't detect any DVB-C channels with both sticks connected in 11.10 64 bit.

**My challanges are now** that after changin from DVB-T to DVB-C for the 520e i cannot change back &#8211; this is actually not a big problem, since i wanna use DVB-C but still i shoudl be able to.

**The other challange** 
is getting the channel scan to work. 
Where I am, the frequency is 143 MHz, Modulation is QAM64, symbol rate is 6875000 S/s and network ID is 999. 
In Myth i can not enter the Network ID and becouse of this I can get a lock on the channels but they allways &#8220;*timed out*&#8221; and i get the message &#8220;*Failed to find any channels*&#8221;.

I have made some &#8220;*Transports*&#8221; which i believe i shouldn't have i believe. 
(from this link: [http://www.mythtv.dk/viewtopic.php?id=38]("http://www.mythtv.dk/viewtopic.php?id=38") It's in danish).

From this link it seems i have to do an awfull lot just to delete my transports:
[http://wiki.indie-it.com/index.php?title=MythTV_Freesat#UPDATE:_BBC_HD_Fix_-_Delete_All_Transports_And_Channels_Then_Rescan]("http://wiki.indie-it.com/index.php?title=MythTV_Freesat#UPDATE:_BBC_HD_Fix_-_Delete_All_Transports_And_Channels_Then_Rescan")

If anybody has some ideas please let me know.

If a mod drops by and think this belongs in Mythbuntu forums feel free to move it.

And maybe this should be reported as a bug in MythBuntu 12.04? - I don't know how to do that, so feel free to do it for me ;)

/Morten

---

### Post by Morten ML on 2012-05-14
Succes!
I have installed 12.04 and everything works now. I have made a tutorial here:
[http://ubuntuforums.org/showthread.php?t=1979760]("http://ubuntuforums.org/showthread.php?t=1979760")

---

