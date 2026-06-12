---
title: "Garena doesn't even start up"
date: 2009-11-23
forum: General Help
---

### Post by Corbis on 2009-11-23
Hi! So I just decided to go back Linux, for a while at least. Using 9.10 now and running WC3+TFT just fine under Wine. Sadly, I need to use Garena too. 

My problem is that Garena doesnt start up at all! No matter how many times I click on garena.exe it does nothing. I've installed it through wine and ofc start it through wine. But nothing happens.

Running Lenovo SL500
[Urgent! Thanks for any answers and tips]

---

### Post by meson2439 on 2009-11-23
Unfortunately, garena is made for MS (notice the .exe) so it cannot run natively on Linux. Using wine may make it usable but the performance is bad. Also you may have to wait for wine updates for 9.10. Wine might already execute the Garena but it takes so long to start. I have this problem once where wine only start after awhile (30+ minutes) when wine is not updated. Ubuntu 9.10 is very new might took them quite some time to issue a new patch.

---

### Post by Corbis on 2009-11-23
Well the thing is that I know it can be run in Wine. It just refuses to work for me.

---

### Post by meson2439 on 2009-11-23
Does it used to work in the previous ubuntu? I've given up fiddling with wine. Too much work, and the performance are very slow. Not to mention certain sound problem.

---

### Post by Corbis on 2009-11-23
Ok I made some progress: I updated wine and now I'm able to start it, BUT I can't literally see it. It's there, up and running but invisible, unable to login.

---

### Post by gunbladeiv on 2009-11-23
same goes with me here. i've installed and run garena. but still, no visible window of garena appear. and if i wait a litle bit longer, there will pops out an error message saying that a new bug found and no report have been made regarding this bug. 

Anyone has any solution on how to run garena on Ubuntu yet?

---

### Post by myromance123 on 2009-12-16
You have to use an older version of wine to get some functionality out of it.

 I "used" to be able to play Garena in Ubuntu 8.04 and that was using Wine 1.0 I think or maybe 1.1.09 to 1.1.13 or something on the lines of that.

If you run it via terminal, you will see a part where it gets stuck and if you press Ctrl-C it will stop that process and you will get the error message but from Garena itself (with a proper GUI running..).

 I believe it has something to do with GEngine...
Wish I knew how to program so that I could help Wine with this...

---

### Post by myromance123 on 2009-12-16
I just tried something that I never thought of before.

 It gets me to the login, login works and (although badly misplaced icons) I can select warcraft TFT, enter rooms and this is where it stops.
I can't get it to start the game but I can get it to set it to war3.exe

Here is what I did:

 1. Install PlayOnLinux (either through Ubuntu Software Center or from [www.playonlinux.com](www.playonlinux.com))
 2. After installing, open PlayOnLinux from Applications->Games->PlayOnLinux
 3. Let it update itself.
 4. Now, click Tools and then select Manage Wine Versions.
 5. From the list of available Wine versions, select version 1.1.11 and then click Add (located in the bottom right corner).
 6. Let it install itself.
 7. After that, return to the main PlayOnLinux GUI and click Install.
 8. On the bottom left corner click "Install a .pol package or unsupported application".
 9. Select Manual Installation and click Next.
 10. Click forward. Select Install a program in a new prefix and click forward again.
 11. Name it Garena.
 12. Tick assign a Wine version to a program.
 13. From the dropdown menu select 1.1.11 (NOT System).
 14. Then everything else should be a piece of cake !

Let me know if you get stuck or are like "Huh? What are you talking about?"

 Good luck :)

---

### Post by escaflowne on 2009-12-26
Today i installed Garena with the latest Wine 1.1.35.
The installation was perfect. But Garena still couldn't run. When i run Garena in the terminal, it stuck at

[B]err:ntdll:RtlpWaitForCriticalSection section 0x7bca0784 "loader.c: loader_section" wait timed out in thread 0020, blocked by 0009, retrying (60 sec)
[/B]
then i pressed ctrl+c, a error box pop-up with a message

**Logic Error(CUIPluginLoader::__LoadByConfigE:84):Error Code:317Load UI Plugin(Path:C:\Program Files\Garena\plugins\UI/GEngine.dll)Failed.**

At the back I can see the Garena interface loaded with misplaced game icons.

From this its confirm that it has something to do with Garena engine (GEngine.dll).

---

### Post by borogoves on 2010-05-31
Wohoo. I recently registered to say I love you myromance123, err. Thank you. My garena is working now. ^^



~ I'm programming language illiterate.

---

### Post by borogoves on 2010-05-31
LoL stumbled on another problem. myromance123, I notice that you also had that problem a long time ago(read 1 of your post). How did you bypass that?

---

