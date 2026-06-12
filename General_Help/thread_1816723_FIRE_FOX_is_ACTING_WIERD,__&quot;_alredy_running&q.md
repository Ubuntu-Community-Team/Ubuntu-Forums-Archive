---
title: "FIRE FOX is ACTING WIERD,  &quot; alredy running&quot;"
date: 2011-08-02
forum: General Help
---

### Post by donut123 on 2011-08-02
My Firefox is running and it wont let me go to the net. It gives me  a message " Firefox is already running..and it does it a lot now.
I either have to restat my machine, or end process..its happening a lot now. I am using firefox 3.6..Oskar skin..

---

### Post by glene77is on 2011-08-02
> **donut123 said:**
> My Firefox is running and it wont let me go to the net. It gives me  a message " Firefox is already running..and it does it a lot now.
I either have to restat my machine, or end process..its happening a lot now. I am using firefox 3.6..Oskar skin..

I have had that happen when a MalWare program runs something in RAM, trying to lock me onto that website.
I have been successful in Un-Loading (Un-Installing) FireFox, and then Re-Installing FireFox.  
From Puppy and TinyCore, I just shutdown the OS and restart (Everything is pulled from the Squash Files Fresh!
From Ubuntu, I had to Un-Install FF. 

You might try a FireWall, after you clean up this problem.   :)

---

### Post by dj722000 on 2011-08-02
I gave up on firefox when google chrome came out.

---

### Post by raja.genupula on 2011-08-02
i got that problem in my college systems(Xp). i never get the problem like that in ubuntu . better to go for new installation .

---

### Post by uRock on 2011-08-02
> **donut123 said:**
> My Firefox is running and it wont let me go to the net. It gives me  a message " Firefox is already running..and it does it a lot now.
I either have to restat my machine, or end process..its happening a lot now. I am using firefox 3.6..Oskar skin..

If you run the **top** command in a terminal after getting the massage, does it show Firefox running.

---

### Post by raja.genupula on 2011-08-02
> **uRock said:**
> If you run the **top** command in a terminal after getting the massage, does it show Firefox running.
i  am sure it will be

---

### Post by Gyokuro on 2011-08-02
you can also enter in your terminal:

ps -A | grep firefox

and it will show you at first the process id which you can kill via:

kill -9 firefoxprocessid

and later you can restart firefox

---

### Post by raja.genupula on 2011-08-02
> **Gyokuro said:**
> you can also enter in your terminal:

ps -A | grep firefox

and it will show you at first the process id which you can kill via:

kill -9 firefoxprocessid

and later you can restart firefox


but everytime doing as like that is some what irritating job , we need a solution to this

---

### Post by uRock on 2011-08-02
> **raja.genupula said:**
> but everytime doing as like that is some what irritating job , we need a solution to this

Please do not derail the thread. You have already stated that you have had this problem in Windows XP and not in ubuntu.

Thank you,
uRock

---

### Post by Sylos on 2011-08-02
Also experiencing this in Ubuntu 10.04.

I have been killing the process from the System Monitor.

Would be good to know why it happens but I lack the knowledge and understanding to debug.

---

### Post by uRock on 2011-08-02
> **Sylos said:**
> Also experiencing this in Ubuntu 10.04.

I have been killing the process from the System Monitor.

Would be good to know why it happens but I lack the knowledge and understanding to debug.

Back up your .mozilla folder by renaming it to .mozilla.bak, then fire up Firefox and see if the problem persists. If not, then something has changed in your settings, such as clicking a link running a harmful script.

To find the .mozilla folder, open the Home folder, then hit Ctrl+H to show hidden folders.

If the problem persists, then reinstall Firefox via the Ubuntu Software Center.

---

### Post by bodhi.zazen on 2011-08-02
> **donut123 said:**
> My Firefox is running and it wont let me go to the net. It gives me  a message " Firefox is already running..and it does it a lot now.
I either have to restat my machine, or end process..its happening a lot now. I am using firefox 3.6..Oskar skin..

This can also occur if the permissions of ~/.mozilla (or sub directories) are incorrect or if you are running apparmor.

Make sure your user owns and can read/writhe the files and directories in ~/.mozilla and check your logs for apparmor errors.

---

### Post by Sylos on 2011-08-02
> **uRock said:**
> Back up your .mozilla folder by renaming it to .mozilla.bak, then fire up Firefox and see if the problem persists. If not, then something has changed in your settings, such as clicking a link running a harmful script.

To find the .mozilla folder, open the Home folder, then hit Ctrl+H to show hidden folders.

If the problem persists, then reinstall Firefox via the Ubuntu Software Center.

Thanks for the advice. It doesnt seem to be doing it at the moment (typical) but when it next occurs I will give it a shot.

Thanks

---

### Post by donut123 on 2011-08-02
I think I will try uninstall...reinstall...I will try it..and be back with the results

---

### Post by donut123 on 2011-08-02
OK this is what I found out..I uninstalled it reinstalled it..and it seems like it was ok..but it seems about 10 minutes of running it does the same thing..I dont know

---

### Post by donut123 on 2011-08-02
ok heres whats happening..its firefox-bin..and monitor says its sleeping..but i click end process..then it works again..it dosent do it right away it takes  a few times on the net and then I get..:Firefox is already running

---

### Post by lovinglinux on 2011-08-03
> **glene77is said:**
> I have had that happen when a MalWare program runs something in RAM, trying to lock me onto that website.
I have been successful in Un-Loading (Un-Installing) FireFox, and then Re-Installing FireFox.  
From Puppy and TinyCore, I just shutdown the OS and restart (Everything is pulled from the Squash Files Fresh!
From Ubuntu, I had to Un-Install FF. 

You might try a FireWall, after you clean up this problem.   :)

Try Firefox in safe mode from terminal (need to close it first) then check if the problem persists:

```
firefox -safe-mode
```

---

### Post by glene77is on 2011-08-03
> **lovinglinux said:**
> 
Try Firefox in safe mode from terminal (need to close it first) then check if the problem persists:
```
firefox -safe-mode
```

LovingLinux,
Thanks.  
When the occasion arises in Ubuntu, I will do it. 
Normally I boot into Puppy for internet access.

---

### Post by donut123 on 2011-08-03
My Firefox seems to be working ok now its been a while and it hasent  done  already running..I dont know what it did or I did exactly to fix it...maybe it fixed itself..or firefox had  a glitch for  a couple of days. Its a mystery to me. Thank you for your support!

---

