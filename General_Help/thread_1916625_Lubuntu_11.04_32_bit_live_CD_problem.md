---
title: "Lubuntu 11.04 32 bit live CD problem"
date: 2012-01-28
forum: General Help
---

### Post by agough on 2012-01-28
Hi guys, :)

I've just burned meself a 11.04 Lubuntu CD and tried to give it a go.

On selecting the "try out..." option in the first menu on the CD, I run into problems...

I get stuck in a terminal sort of thing and umm... I'm kind of stuck there (serious terminal noob I'm afriad!). I tried various combinations of passwords and usernames and stuff to no avail.

I tried "sudo startx" (vague memories some some other Linux distro) which looked as if it was going to work, but then it went back to the terminal thing with a load of text, including ".xauthority does not exist".

I thought perhaps my disk/download was dodgy, but I checked the MD5 and did the Lubuntu CD's "Disk check" thing, and both were fine. Over the past few weeks, Windows has done two CHKDSKs on booting up - could this be related?

I'm not sure what's going on - any ideas?
Thanks for reading this far!
:lol:

---

### Post by sudodus on 2012-01-28
You are booting off the CD, so problems reading your hard disk drive should have no impact on the boot procedure. But if you have errors in the RAM, it might give you errors now and then. In order to check for that, use ***memtest***, that is also one option in that early menu.

But I think the problem is something else, maybe that Lubuntu and the computer hardware for graphics or power management do not cooperate as they should. If you reach the first text menu, you can press the function key #6, F6, to get several boot options. Try them out systematically. With a little bit of luck, you will find that it works with one or two of those options set.

---

### Post by ajgreeny on 2012-01-28
Did you check that the .iso file was a good one by comparing its md5sum with the md5sum that you can find at the download site?  You can also use the "Check CD Media" or similar after you poweron the CD.  At the first screen you see, hit enter, choose language, then from the menu that appears check the CD.

You can also try out the following two commands.
```
startx
```  (note that sudo is not needed for that)and if that gets you nowhere try ```
sudo service lxdm start
```  Perhaps neither will work, but it is worth a try, and as this is just a live CD you can not do any harm to your current installed OS or hardware.

---

### Post by Rex Bouwense on 2012-01-28
That was know problem with Lubuntu 11.04 that apparently was corrected in 11.10.  See this site for a work around thanks to amjjawad.
[http://ubuntuforums.org/showpost.php?p=11398602&postcount=35](http://ubuntuforums.org/showpost.php?p=11398602&postcount=35)

---

### Post by ajgreeny on 2012-01-28
> **Rex Bouwense said:**
> That was know problem with Lubuntu 11.04 that apparently was corrected in 11.10.  See this site for a work around thanks to amjjawad.
[http://ubuntuforums.org/showpost.php?p=11398602&postcount=35](http://ubuntuforums.org/showpost.php?p=11398602&postcount=35)
I think that is 11.10, not 11.04, but I do serem to remember lxdm not starting automatically, hence my post before yours.  Was this also a 11.04 problem, as in my 11.04 live lubuntu it is certainly not a difficulty, only with 11.10 live CD do I see that problem, and then only sometimes, not every time I use it.

---

### Post by agough on 2012-01-29
Thanks for the very fast responses!

Yup, went for install, then cancelled - now coming to you from a live Lubuntu CD!

Thanks for your help!

Errr... Have some popcorn on me! :popcorn:

---

