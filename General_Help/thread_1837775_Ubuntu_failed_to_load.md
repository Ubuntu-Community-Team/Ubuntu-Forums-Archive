---
title: "Ubuntu failed to load?"
date: 2011-09-02
forum: General Help
---

### Post by airspoon on 2011-09-02
Last night, I rebooted my Ubuntu 11.04 and it got to the boot loader okay, but after that I just got a screen with white and black lines. It seems as if my windowing system would fail to load, log in screen and everything. 

However, instead of getting of getting a command prompt, I get these weird looking white and black lines. With that being said, it always get those lines before the windowing system kicks on. This time however, my windowing system didn't load and so my computer was just stuck on those indistinguishable lines. 

I tried to boot up in 'recovery' mode and the same thing. However, at the bootup menu, I chose the option for previous linux kernels and chose 2.6.38-8-generic, which seems to be working just fine.

Can I please get help with this, so that I can figure out what happened and hopefully move back to the updated kernel? Also, from my limited past experience with linux, I don't remember getting those squiggly white and black lines when booting up. Instead, I remember getting a legible boot up sequence, where  I can actually read what's going on at boot up. I have never had that with Ubuntu and thought nothing of it since everything else seemed to work okay. Is Ubuntu supposed to be that way?



Thanks....

---

### Post by frank4360 on 2011-09-02
This sounds remarkably like the problem I have been having over the last two days - see [http://ubuntuforums.org/showthread.php?t=1837409](http://ubuntuforums.org/showthread.php?t=1837409)

My problem has just resolved itself - I have no idea how.

---

### Post by community on 2011-09-02
Try this one..
1.On getting the grub menu highlight the normal Ubuntu generic entry(not the recovery mode).
2.Press e to edit the menu entry.
3.Move to the end of the line where "ro quiet splash" is written.
4.Add word 'text' at the end of the line.It should look like "ro quiet splash text".
5.Press ctrl+x to boot.

Most probably you get a text mode interface.Login using your username and password.Then type startx or press ctrl+F7/ctrl+F8 to get the GUI.Reply me if you get the same white lines and other things...

---

### Post by airspoon on 2011-09-02
After reading your thread, my problem seems a tad different. I'm not even getting to the Ubuntu screen and my system hasn't been freezing, at least prior to it failing to load. After the bootup screen, where it asks you which Ubuntu you want to load, I just get a bunch of black and white lines and it stays on those lines.

While I normally get those white and black lines (in lue of the boot up sequence), it has always put me at the Ubuntu log in screen, where everything has seemed to work just fine. However, it now won't get to that log in screen, and so it just stays on those white and black lines.

ETA:
Thanks "Community", I'll try that as soon as my backup is completed. I"m hoping that will work. Thanks for the quick reply and I'll post back here with whether it worked or not.

---

### Post by community on 2011-09-02
How many OS do you have???

---

### Post by airspoon on 2011-09-02
> **community said:**
> How many OS do you have???
On this machine, I just have Ubuntu 11.04. Well actually, I believe there is a Windows XP Pro installed too, though I have never booted into Windows on this machine. As soon as I got this computer, I installed Ubuntu on it and left the windows partition just in case I had problems with the Ubuntu install. So I don;t know if it matters or not, but I don't think the Windows is even set up on this machine.

---

### Post by debd on 2011-09-02
did you install a graphics driver manually? or through jokey?
maybe something has gone wrong and you'll have to recompile the driver kernel modules..
I'm not sure, but you may try that.

---

### Post by frank4360 on 2011-09-02
The "squiggly black & white lines" you mention do sound like the screen is displaying something like the text of the boot sequence but the video driver hasn't yet been invoked?

When the boot finishes normally, that isn't a problem; but the system may now be trying to display a message that you cannot decipher.

Just a guess, and I am afraid I don't have a suggestion as to how you could fix the display.

---

