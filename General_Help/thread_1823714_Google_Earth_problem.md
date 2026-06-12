---
title: "Google Earth problem"
date: 2011-08-12
forum: General Help
---

### Post by Cosmopolitan1 on 2011-08-12
Hi to all :)

After two hours looking around for an answer to my problem on this forum I haven't found it.

However, I have the last Ubuntu OS installed and I tried to install Google Earth.
The installation went smoothly, I can start the program, it appears on the screen but at the place where the globe should be it's just a black space.
I can click upon File, Edit, View etc but the globe is not there and that's it.

By the way, when I turn off the program one process is still running which I must stop in System Monitor.

I uninstalled and installed the program for 4 times but it's always the same.

Any idea how to solve this?

Thanks :)

---

### Post by ~!geek!~ on 2011-08-12
Try this command after installing google earth:
> sudo apt-get install lsb-core 

---

### Post by Cosmopolitan1 on 2011-08-12
Had tried this one previously but it says that the newest version is already installed.

Update to my problem:
When I go into .googleearth, there were three folders there:
              1. Cache
              2. Temp
              3. Instance-runing-lock

The third one became a document now and it says that a link to it is broken.

By the way, before this change the problem was the same.

Any other idea? =D> :)

---

### Post by AlphaLexman on 2011-08-12
Make sure your system meets the [requirements]("http://earth.google.com/support/bin/answer.py?answer=20701") especially the graphics card.

---

### Post by Cosmopolitan1 on 2011-08-12
Not sure about these:

[LIST]
[*]Kernel: 2.4 or later
[*]glibc: 2.3.2 w/ NPTL or later
[*]XFree86-4.0 or x.org R6.7 or later
[*]Graphics Card: DirectX9 and 3D capable with 64MB of VRAM
[/LIST]
It worked in Windows with no problem.
I think I had DirectX10 in Windows and openGL is supported.
My graphic card is integrated Mobile Intel Graphic Media Accelerator.

I met some people on different forums having the same problem:
[http://www.google.com/support/forum/p/earth/thread?tid=7978c84e0733482b&hl=en&fid=7978c84e0733482b0004aa51c6ca3d3e](http://www.google.com/support/forum/p/earth/thread?tid=7978c84e0733482b&hl=en&fid=7978c84e0733482b0004aa51c6ca3d3e)

Anyway, how could I check if I have these on the list? :confused:

---

### Post by AlphaLexman on 2011-08-12
If you have Ubuntu 11.04 as noted below your avatar, the first three requirements should be met.

The graphics card however relates to the physical hardware of your computer and it's drivers.

Probably the easiest way to check the GPU is to use the 'hardinfo' program. Use 'Alt-F2' and type in 'hardinfo' and press enter.

Go to 'Computer -> Display -> OpenGL -> Direct Rendering' 

If it equals '**Yes**' your graphics card is good enough.

If it says '**No**' you may need to update the video drivers.

---

### Post by Cosmopolitan1 on 2011-08-12
Thanks.
It says "Yes".

It's about the software.
I need to perform a trick, but I never had installed this program on Linux before :confused:

---

### Post by AlphaLexman on 2011-08-12
Good.

It is most likely a driver issue...

Please post the following:
```
lspci | grep VGA
```
```
sudo lshw
```
Just the section '***-display**'

---

### Post by Cosmopolitan1 on 2011-08-13
Ok.

Here it is:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 03)
```And the display:
```
*-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller (secondary)
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:fc100000-fc1fffff
```

I must mention that Google Earth worked on this computer in Windows so I suppose the requirements of the hardware suit to GE's needs.

---

### Post by Cosmopolitan1 on 2011-08-14
People,

pls help, what else could I try?

If you help mi I m gonna buy you a big :popcorn: :D

---

### Post by AlphaLexman on 2011-08-14
Please check your video driver...
```
cat /etc/X11/xorg.conf | grep Driver
```
And then look at some of the answers [here]("http://www.google.com/support/forum/p/earth/thread?tid=4b72ea672d8f2971&hl=en").

---

### Post by Cosmopolitan1 on 2011-08-14
Thanks but when I run that command I get this:
```
cat: /etc/X11/xorg.conf: No such file or directory
```And in the link everyone mention 64 bits system but I have 32 :(
..and I have no NVidia but integrated graphic card

---

### Post by AlphaLexman on 2011-08-14
Did it get moved or renamed between versions ??
```
ls -l /etc/X11
```

---

### Post by Cosmopolitan1 on 2011-08-14
I am really not sure but I've got this:
```
drwxrwxrwx 2 root root  4096 2011-04-26 06:05 app-defaults
drwxrwxrwx 2 root root  4096 2011-04-26 06:05 cursors
-rwxrwxrwx 1 root root    14 2011-04-26 06:04 default-display-manager
drwxrwxrwx 4 root root  4096 2011-04-26 06:00 fonts
-rwxrwxrwx 1 root root 17394 2010-02-19 07:02 rgb.txt
lrwxrwxrwx 1 root root    13 2011-05-21 21:56 X -> /usr/bin/Xorg
drwxrwxrwx 3 root root  4096 2011-04-26 06:05 xinit
drwxrwxrwx 2 root root  4096 2011-02-08 20:27 xkb
-rwxrwxrwx 1 root root   709 2010-11-03 04:17 Xreset
drwxrwxrwx 2 root root  4096 2011-08-09 17:34 Xreset.d
drwxrwxrwx 2 root root  4096 2011-08-09 17:34 Xresources
-rwxrwxrwx 1 root root  3730 2010-12-02 10:34 Xsession
drwxrwxrwx 2 root root  4096 2011-08-09 17:34 Xsession.d
-rwxrwxrwx 1 root root   265 2010-02-19 07:02 Xsession.options
-rwxrwxrwx 1 root root   601 2011-04-26 05:54 Xwrapper.config
```

---

### Post by AlphaLexman on 2011-08-14
Everything looks completely normal there with the **EXCEPTION** of not having a '[COLOR="Red"]xorg.conf[/COLOR]' file!

I didn't think that was even possible! Anyway, [here]("http://www.linuxquestions.org/questions/linux-software-2/no-earth-on-google-earth-644439/") is another thread that might help.

---

### Post by AlphaLexman on 2011-08-14
Deleted

---

### Post by Cosmopolitan1 on 2011-08-14
Thanks,

I tried different logins but it's still the same.
Always same :(

---

### Post by Cosmopolitan1 on 2011-08-17
Anyone? :(

---

