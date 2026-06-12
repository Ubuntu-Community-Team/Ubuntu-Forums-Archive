---
title: "Strange vertical split using &quot;nv&quot; display driver"
date: 2006-02-20
forum: General Help
---

### Post by barakori on 2006-02-20
I installed Ubuntu (Breezy) 3 months ago, and since then, I'm unable to get a decent display driver for my (quite old) display driver. Here's what lspci says:

[FONT="Courier New"]0000:01:00.0 VGA compatible controller: nVidia Corporation NV5 [RIVA TNT2/TNT2 Pro] (rev 15)[/FONT]

Ubuntu installed the "nv" driver automatically, but used a 640x480 resolution. After modifying /etc/X11/xorg.conf, I was able to use 1024x768 (my native LCD resolution), but the vertical position is shifted, and I get a split screen (See attachments). I tried the "vesa" driver, and it works well (no vertical shift, see attachments), but makes my computer run very slow (It's an old P3 500Mhz) and with no video acceleration (e.g. I can't see standard XviD video files).

I tried installing an "nvidia" driver (version 1.0-7174 the latest that supports my card), but it didn't work out. After a lot of tries and support in the nVidia forum, the problem wasn't solved (I would simply get a black screen). The thread is available at the [NVidia Linux Forum]("http://www.nvnews.net/vbulletin/showthread.php?t=62637"). Again, I don't expect to install the NVidia drivers, but hope I can work out the "nv" driver problem.

More information: the display is a Gateway FPD1500. It's a 15" LCD monitor with a DFP (digital) connector (no VGA). My card has a DVI output (again, no VGA) and I got a DVI to DFP cable. It seems the monitor doesn't provide EDID information, but I know it works well at 1024x768 (native resolution), porbably at 60Hz.

If anyone encountered such a problem (vertical offset), or you have some suggestions, please help. Thanks.

---

### Post by r4ik on 2006-02-20
I had the same problem,other card but that does not matter.
Give this a try,

sudo apt-get install nvidia-kernel-common nvidia-glx

sudo gedit /etc/X11/xorg.conf

Find the &#8220;Module&#8221; section. Comment out the &#8220;Glcore&#8221; and &#8220;dri &#8220; modules and make sure a &#8220;glx&#8221; module is there. So basically like this:

#       Load    "GLcore"
#       Load    "dri" 
          Load "glx"

In your case uncommand Load "glx" by putting # in front


Now find the &#8220;Devices&#8221; section

Set the "driver to "nv"
BusID		"PCI:1:0:0"

Save the file and see if it works.
If it does credits go to poofhairyguy's guide on "glx"

In case xserver crashes agian make sure when you do a

sudo gedit /etc/X11/xorg.conf

your "ram" is set to 64000 and when asked for high/low settings a little later in the conf. set low 10 higher.

If nothing works change the background to a single color and you wont see the vertical split the problem will be hidden.

Hope this helps.

---

### Post by schilcha on 2006-02-20
I saw the same effect on my notebook's geforce2go using the nv-driver (not always, but regularily). I also tried the nvidia-driver from the nvidia-glx-legacy package (is it 7174?). Anyways, I still had problems with it. For now, I'm very happy with the latest nvidia-8178-driver (hope, I remember that number correctly). 

There's a howto somewhere around here on how to install the latest nvidia drivers. If you're not afraid, just go ahead and give it a try.

Good Luck!

---

### Post by r4ik on 2006-02-20
The howto can be found here,

[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=Howto](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=Howto)

---

### Post by endokrin on 2006-03-13
Hi,

I installed 5.10 on an old Gateway desktop and the installation went well, except when I logged in the first time, I had the same split screen as the Original Poster.

I went to the above mentioned HowTo and followed Method 1 and upon rebooting, the login screen did not appear and I get this error message:  
Failed to start X Server........

It looks like the Ubuntu version of Windows' blue screen of death.

After hitting Enter, I get a black screen with my login, asking for password just like in a Terminal. 

Any help?

---

### Post by endokrin on 2006-03-16
bump

---

### Post by endokrin on 2006-03-16
Well, I completely reinstalled 5.10

I then followed the instructions in the second post in this thread, rebooted, and got the same result.. xserver isn't working or something.

I have the same monitor the OP has.


Help pleeeeeease!

---

### Post by MrDave2176 on 2007-12-20
I just installed Linux Mint Cassandra (which uses the Ubuntu repositories) and got the exact same issue as the OP (same hardware and everything!).

I used the suggestions posted here:
[Gateway FPD1500 LCD Monitor -- how to make it work under Linux]("http://groups.google.com/group/comp.os.linux.setup/browse_thread/thread/205342c8221c97/554a6194d9d112ee?hl=en&lnk=st&q=Gateway+FPD1500+LCD+Monitor+--+how+to+make+it+work+under+Linux#554a6194d9d112ee")
	
But it didn't fix the problem.  I have yet to try the second poster's suggestion, but based on other posts in this thread I am not confident.

Suggestions are welcomed.

---

### Post by MrDave2176 on 2007-12-22
I used Envy to install the NVidia drivers and they didn't crash, but they didn't fix the split. On reboot I got a message that said "Your computer is running in low graphics mode" and showed me the dialog boxes to set the display driver and monitor.  The defaults set were "Plug and play" monitor and "vesa-compatible" for the graphics card. 

I set the appropriate monitor and card for my machine and once booting had completed the display was correct.  The split was gone.  I used it a while and then shut it down but on restart the split was back.

So I went back to Envy and re-installed the nvidia drivers and restarted.  Again, the "low graphics mode" warning and the dialog boxes. Once set the display worked fine.  I've had to restart since and it is back to the split.

I am open to suggestions.

---

