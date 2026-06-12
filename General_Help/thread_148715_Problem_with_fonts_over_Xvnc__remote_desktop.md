---
title: "Problem with fonts over Xvnc / remote desktop"
date: 2006-03-22
forum: General Help
---

### Post by ditikos on 2006-03-22
Hello,

I have this problem with my fonts. I've installed msstcorefonts using apt-get, did an fc-cache update, everything are ok.

I am using a box that has no monitor, therefore I have created an XDMCP solution. The problem is that when I use a vnc client (either RealVNC or Ultravnc) all my localized fonts (Greek) are garbled. When I use them natively from the box they appear normal.

I've tried to change the -fp path, or even add some more to the truetype fonts but that does not solve the problem. In fact, in some cases it did not start up the remote desktop process as well.

As I see through numerous pages, there is an X Font Server. How do I enable the service and how is this passed as a directive to Xvnc (in my xinetd.d directory)?

Thanks in advance,
Panagiotis

---

### Post by archis on 2006-03-23
Panagiotis, 

sorry I can't help with configuring X Font Server but perhaps you can solve your issue by using [freenx]("http://freenx.berlios.de/"), the gpl version of [NX server]("http://www.nomachine.com/") instead. IMHO, NX is vastly superior to VNC in terms of performance. Reminds me of [Vmware]("http://www.vmware.com/"). You can use the (free) NX [Clients]("http://www.nomachine.com/download.php") from nomachine with the freenx server. 

If I understand you correctly everything looks ok to you when you connect a screen to the headless box? Then this might just work for you. The NX Clients have a nice GUI and are very easy to configure, including Font Server config AFAIK. There's a [good tutorial for setting up freenx]("http://ubuntuforums.org/showthread.php?t=97277") in the forum. 

Note: The link to the Seveas Repository in the tutorial is out of date -- [here's a mirror]("http://free.linux.hp.com/~brett/seveas/freenx/").

---

### Post by ditikos on 2006-03-23
Yes you are correct. In the linux box, there is Greek support and everything. Only in the remote things come garbled.

I have just installed FreeNX but it seems a little bit slower in performance than vnc. And also the xkeyb service that switches keys is not present. I guess I'll have to check the win32 client again.

---

