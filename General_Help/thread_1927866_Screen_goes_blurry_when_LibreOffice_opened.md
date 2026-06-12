---
title: "Screen goes blurry when LibreOffice opened"
date: 2012-02-18
forum: General Help
---

### Post by Crimson_Tider on 2012-02-18
I posted this in the Multimedia & Video forum about 2 weeks ago and never got any responses. So here it is again to see if it works here:

Hello, I am having a problem, seemingly with my NVIDIA onboard video. When I open any LibreOffice application, my whole screen goes blurry; see the attached screenshot. I am using 11.10 Oneiric 64-bit with NVIDIA GeForce 7025.

Thanks.

---

### Post by Ms. Daisy on 2012-02-19
I can't say I know for sure, but seeing that your previous post got ignored I'll offer you something.

It kinda seems like a driver issue. Have you tried running "additional drivers"? 

I googled drivers for your particular graphics card and came up with a bug that may or may not apply to you:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/859979](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/859979)

---

### Post by Crimson_Tider on 2012-02-19
> **Ms. Daisy said:**
> I can't say I know for sure, but seeing that your previous post got ignored I'll offer you something.

It kinda seems like a driver issue. Have you tried running "additional drivers"? 

I googled drivers for your particular graphics card and came up with a bug that may or may not apply to you:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/859979](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/859979)

Thanks for answering! I thought I might never get any help on this! This bug doesn't look like it would pertain to my problem (though I understand that sometimes fixing one bug can inadvertently fix others). Maybe I should submit it as a bug. I was hoping to get help on here first, but there may not be anything that anyone on here can do.

---

### Post by Ms. Daisy on 2012-02-19
It's weird that it only happens with LibreOffice.  You haven't had any luck updating or finding new drivers?

---

### Post by Ms. Daisy on 2012-02-19
I found a LibreOffice forum, maybe if the problem is truly confined to only that application you can get some answers over there.  If it were me I would open up every installed application to see if anything else is affected first. 

[http://en.libreofficeforum.org/](http://en.libreofficeforum.org/)

---

### Post by Crimson_Tider on 2012-02-19
> **Ms. Daisy said:**
> It's weird that it only happens with LibreOffice.  You haven't had any luck updating or finding new drivers?

Back when I first bought this motherboard, I had to work on it for weeks off and on before I finally found a driver and OS version that would work. I tried every one of the listed drivers in Additional Drivers one at a time, and each one had a different problem. I had various other problems in the process as well. You can read about it in [my other post]("http://ubuntuforums.org/showthread.php?t=1882790") if you really want to know. I ended up having to install 64-bit Oneiric and then had go to the NVIDIA website and downloading the latest driver for it. No drivers for 32-bit and no drivers for 64-bit worked normally at all except for this one (as I'm typing, I realize I'm not totally sure I tried the 32-bit driver from the NVIDIA site, but I'd rather not go through the process of re-installing Ubuntu yet again to try that one).

---

### Post by Crimson_Tider on 2012-02-19
> **Ms. Daisy said:**
> I found a LibreOffice forum, maybe if the problem is truly confined to only that application you can get some answers over there.  If it were me I would open up every installed application to see if anything else is affected first. 

[http://en.libreofficeforum.org/](http://en.libreofficeforum.org/)

Thanks, that gives me something to try. I'll post again once I've tried all that.

---

### Post by irwan4all on 2012-11-03
This is the same problem as I did.Is there any solution of the problem?
btw, I installed ubuntu 12.10 on MCP6P3 Biostar Motherboard with NVIDIA Geforce 6150 GPU integrated video and AMD Phenom II X2 Processor.[[IMG]http://img849.imageshack.us/img849/4193/screenshotfrom201211040.png[/IMG]](http://imageshack.us/photo/my-images/849/screenshotfrom201211040.png/)

---

### Post by cariboo on 2012-11-04
> **irwan4all said:**
> This is the same problem as I did.Is there any solution of the problem?
btw, I installed ubuntu 12.10 on MCP6P3 Biostar Motherboard with NVIDIA Geforce 6150 GPU integrated video and AMD Phenom II X2 Processor.<snip>

It looks like you have a graphics driver problem, what driver are you using?

If you aren't sure what driver you are using, open a terminal, open the dash and type "ter", and click the terminal icon, once the terminal is open, copy/paste the following command:

```
/usr/lib/nux/unity_support_test -p -f
```

and paste the output into your next post.

---

### Post by irwan4all on 2012-11-16
This is the result for  /usr/lib/nux/unity_support_test -p -f

```

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 6150SE nForce 430/integrated/SSE2/3DNOW!
OpenGL version string:  2.1.2 NVIDIA 304.64

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

```It's still blurry, but Thx b4.:)

---

