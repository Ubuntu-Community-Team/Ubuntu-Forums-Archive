---
title: "Unity 3D failed"
date: 2011-06-14
forum: General Help
---

### Post by grndnl on 2011-06-14
Hello every one, I installed Ubuntu 11.04 on an Asus, and when I type in the terminal "unity" in order to install it, the process goes on for some time, but then I get an error message. I will attach a JPEG with the error I get in the terminal. Being new here, I don't understand any of it, but I also should tell you that I have the necessary graphics cards installed, and I also have Unity 2D currently installed. At the point where it stops, the computer also freezes.
Thanks for your help in advance, and sorry for the long thread.

**Look at the attachment!**

---

### Post by sikander3786 on 2011-06-14
If you installed 11.04, Unity got installed by default and you don't need to install it individually unless it is the worst user case.

We can't see the attachment.

Here is a link to troubleshoot Unity.

[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

Or if that doesn't help, please provide some more details on what you are experiencing.

---

### Post by grndnl on 2011-06-14
Hi,
I followed the tutorial that you posted. Here are the results:

WHEN I RUN ```
unity --reset
```

----------------------------------------------------------------
Traceback (most recent call last):
  File "/usr/bin/unity", line 198, in <module>
    reset_unity_compiz_profile ()
  File "/usr/bin/unity", line 83, in reset_unity_compiz_profile
    if current_profile_gconfvalue.get_string() == 'unity':
AttributeError: 'str' object has no attribute 'get_string'
----------------------------------------------------------------
----------------------------------------------------------------


wHEN I RUN ```
/usr/lib/nux/unity_support_test -p
```
----------------------------------------------------------------
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce Go 7300/PCI/SSE2
OpenGL version string:  2.1.2 NVIDIA 270.41.06

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity supported:          no
----------------------------------------------------------------
----------------------------------------------------------------



I now understand why unity is not starting... so what can I do to solve that? My card is black listed, but when I removed it, another driver showed up, I can't remember the name but it was something like 'experimental 3D support driver'. I also found this: [http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity](http://askubuntu.com/questions/37629/geforce-go-7300-7400-blacklisted-can-i-still-run-unity)

Do you think it is a good idea to use the bypass described in the link?

---

### Post by sikander3786 on 2011-06-14
First, you need to run 'unity --reset' when Unity is actually running. If you stopped GDM before executing that command, it would have no effect.

And yes, you can try bypassing the Unity check, many users were able to run Unity on blacklisted cards. It is explained further here.

[http://ubuntu4beginners.blogspot.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html](http://ubuntu4beginners.blogspot.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html)

---

### Post by grndnl on 2011-06-14
Thanks.

---

