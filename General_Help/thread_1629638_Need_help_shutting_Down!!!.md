---
title: "Need help shutting Down!!!"
date: 2010-11-24
forum: General Help
---

### Post by Glen Montanaro on 2010-11-24
I've installed Ubuntu 10.10 and must I say when it works, its great.

But i've had some problems during shutdown.
When i shutdown it does its normal thing but then the screen simply goes black but the machine stays on. And it stays like that forever. And when i decide to pull the plug the next time i start ubuntu it runs a disk checking and also finds some errors. Once it found an error in / and another time in /tmp/  
Also during booting it mentions some error about CWAP I don't know what it is.

Please help!!!!

Tnks,
Glen Montanaro.

---

### Post by nl4m on 2010-11-24
Tell me what happens when you punch in this (I have to worn you that this code will shutdown your company. If you need to save something please do it before type this code):
```
sudo shutdown -h now
```

Did you check the /var/log messages? What's the error's given?

---

### Post by Swagman on 2010-11-24
or Alt + F2 sudo halt

---

### Post by WorMzy on 2010-11-24
> **Swagman said:**
> or Alt + F2 sudo halt

You'll need to check "run in terminal" for that to work.

---

### Post by Soul-Sing on 2010-11-24
```
sudo poweroff
```

---

### Post by Glen Montanaro on 2010-11-24
First of all thanks to the replies.

@nl4m
I tried what you said but it did nothing different than what the shutdown button does. Here's part of the log file i found in /var/log 
Nov 24 15:26:13 glen-A6U kernel: [   18.848978] asus_laptop: Asus Laptop Support version 0.42
Nov 24 15:26:13 glen-A6U kernel: [   18.852222] asus_laptop: Error calling CWAP(1)

@Swagman and @Wormzy
It worked and it made a proper shutdown.
Now does that mean that every time i want to shutdown i have to go to terminal or is there a different way???

Thanks A lot :D

---

### Post by rajadain on 2010-11-24
I'm having the same problem. Haven't tried "halt" so far, but sudo shutdown and sudo poweroff both don't work. At first I (for some reason that I can't remember) thought that it was because of the shell, so I installed both the Ubuntu Netbook edition (Unity?) and Gnome 3, but same problem exists across all three versions.

Will try halting next.

---

### Post by I'mGeorge on 2010-11-24
> **leoquant said:**
> ```
sudo poweroff
```

don't use poweroff , 'cause it's similar to pressing the poweroff button, try the "shutdown -h now" command. If it works you can make your own shutdown button out of it.

---

### Post by Glen Montanaro on 2010-11-24
For some reason right after i post with the one where i say that it worked i went to shut down using sudo halt and it went to the same problem i had at the very beginning. Please help!!!!

---

### Post by rajadain on 2010-11-24
Tried halt, and sudo shutdown -h now. Both don't work.
I did some custom settings for NetworkManager but I've reversed them now. Also, I use some commands for the VGA switcheroo so that I don't burn both cards. Have disabled that too. Nothing works!

However, when my system was last updated, and it said "restart before these updates can be applied. Restart now?" and I said yes, it restarted fine. What command does that installer use?
(I was having this problem both before and after that update)

---

### Post by Penguin=) on 2010-11-24
I think you may have a error in your / directory. 

You mensioned that when that error ran, it said that there was a error in your /tmp/ file, this is the temporary folder where random things get stored from most websites.

I think you may have shutdown virus from one of these websites.
Usally the file in the /tmp/ folder would dissapeer when you visit somewhere else, but if its a virus it will stay there. 

To get rid of it go to the /tmp/ folder, (go to your home folder then go to file, open location and type /tmp/)
and find something that either has alot of numbers on it OR it has a name related to the website (e.g 63examplevirus.org) 

Try this, BUT DO NOT delete anything that is not suspicoius.

---

### Post by Glen Montanaro on 2010-11-25
On my machine normal restarts are always successful yet only shut down keeps the machine on.

---

### Post by Glen Montanaro on 2010-11-25
On my machine normal restarts are always successful yet only shut down keeps the machine on.

---

### Post by Glen Montanaro on 2010-11-25
The thing is that i have had ubuntu for not more than 4 days and i haven't browsed any websites except youtube ubuntuforums blender blenderartists and google. Neither have i downloaded anything except Blender 2.55 and blender 2.49(as a package from synaptics).
so i guess its very unlikely that i got a virus.

btw it only was one time where it found an error in  /tmp/ 
the majority of the time it found the error in / but always have managed to fix all errors.

---

### Post by wilee-nilee on 2010-11-25
hold down ctrl-alt-prtsc and slowly type reisuo. If you want a reboot use a b rather then a o at the end.
[http://en.wikipedia.org/wiki/Reisub](http://en.wikipedia.org/wiki/Reisub)

---

### Post by zealibib slaughter on 2010-11-25
You could be experiencing an IO error with your hard drive during shutdown.  I would check the smart values using disk utility under the administration tab to make sure this wasn't the problem.

---

### Post by Glen Montanaro on 2010-11-26
Sry but i accidentally corrupted the partition when I skipped disk checking, gave up and installed puppy

---

