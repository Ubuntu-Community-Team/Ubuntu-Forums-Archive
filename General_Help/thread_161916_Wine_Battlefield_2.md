---
title: "Wine Battlefield 2"
date: 2006-04-18
forum: General Help
---

### Post by cowlikk on 2006-04-18
i need help installing battlefield 2!! wine wont continue with install on the second cd!!any help is appreciated or is there a better program to play battlefield 2 on/with

---

### Post by Abild on 2006-04-18
[QUOTE=cowlikk]i need help installing battlefield 2!! wine wont continue with install on the second cd!!any help is appreciated or is there a better program to play battlefield 2 on/with[/QUOTE]

I tink you'll need [cedega]("www.transgaming.com") to play bf2. Wines DirectX support is currently not very impressive. Also note that most DirectX games only works with cedega if you have a nVidia card.

---

### Post by liquidweaver on 2008-03-08
That is not a true statement about Wine - the source trees branched in 2002, and frankly, there is much the Cedega team is far behind in.
I used to use Cedega primarily for gaming, but more and more (the last 2 years especially) Wine just works better.

Anyways, I recommend you check out this page -> [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3438](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3438)

In the future, WINE's appdb is a great place to go to find out of something is compatible or if there is a way to make it work.

---

### Post by SSMethoz on 2008-06-13
Has anyone gotten Bf2 to work? I have installed it using wine, but when I load it, I see the Bf2 logo then a black screen then it exits wine. I have gotten the dll's and changed the screen resolution...what else could be the problem? I have a Nvidia 8600 GTS. 

Thanks.

---

### Post by yeaitsdark on 2008-06-22
Hey. So after a little effort I was able to play BF2 with wine 1.0. Everything works well... to put simply perfectly with 2 major issues (for me).

Firstly, to explain more in depth how I did it. I have Vista on my machine. I copied BF2 from the Program Files folder and also some dlls from /windows/system32

I copied all the d3dx9_24.dll etc. Etc meaning d3dx9_25.dll and so on. (I don't think you need to copy ALL of them, but to be honest my thinking was the more the merrier. However this could have led me to additional problems. Then (important for some reason) go into winecfg and have it emulate a virtual desktop (size not relevant).

OK anyways - the 2 issues.

Firstly - Theres no mouse cursor on in the main window - but honesty I don't even care because I can still click.

Secondy, (My MASSIVE issue atm) is theres this big black like blob when I'm in game. If I look up... it moves - things appear OVER the big black blob.... minus the actual gameplay. Very confusing.


Also, I am able to play in Ranked Multiplayer servers. (possibly due to copying direct from windows?? Not sure...

And it runs hella fast lol. Minus the BLOB. I personally think something with pixel shaders? But I'm not a real wine expert and unsure of how to fix that. 

I uploaded a video on youtube (its really horribly done and like super speed because it only captured at like 10fps but well first time i've actually done the whole capture and upload thing)

[http://youtube.com/watch?v=R7FYpwe32hw](http://youtube.com/watch?v=R7FYpwe32hw)

Hopefully you can see the "black blob" thing I am referring to.


Note: I'm going to test with Cedega right now. I suppose I actually should use the service I pay for lol. But wine is often actually better... hummm and free?? Oh life.

Another Note: This is with 1.41 BF2 (latest version, also with Booster Packs as well)

---

### Post by yeaitsdark on 2008-06-22
OOOOOOOOOOOOK!!

YAY. I'm quite happy. After well bloody hours of googlin' I discoved a solution to my "blob" effect.

[http://vostrolinux.blogspot.com/2007/11/setting-up-battlefield-2.html](http://vostrolinux.blogspot.com/2007/11/setting-up-battlefield-2.html)

(in the even this page changes - I'll post the two "Key" things for wine 1.0)

Any problems by feel free to post as well I'm sure I'm forgetting stuff.

Copy d3dx9_24.dll and d3dx9_25.dll from your windows installation to /home/YOURUSERNAME/.wine/drive_c/windows/system32


Then type 

wine regedit

Then Quote from link:

"Then I navigated to HKEY_CurrentUser>Software>Wine>Direct3D. Now I had to add a new string to enable Off screen rendering. I right clicked New>String and entered:


>OffscreenRenderingMode


To set the value, I right clicked on OffscreenRenderingMode and clicked Modify. For Value Data, I put in:


>fbo
"

So thank you very much JayT. BF2 Working like a CHARM!!

---

### Post by Jordysportracing on 2008-06-29
> **SSMethoz said:**
> Has anyone gotten Bf2 to work? I have installed it using wine, but when I load it, I see the Bf2 logo then a black screen then it exits wine. I have gotten the dll's and changed the screen resolution...what else could be the problem? I have a Nvidia 8600 GTS. 

Thanks.

Please Help me!!! I have exactly the same problem as above and i have a Nvidia 8800 GTS. but i only have Ubuntu on my PC

Thanx in advance

---

