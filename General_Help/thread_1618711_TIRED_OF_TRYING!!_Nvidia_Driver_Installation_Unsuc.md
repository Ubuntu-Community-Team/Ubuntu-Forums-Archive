---
title: "TIRED OF TRYING!! Nvidia Driver Installation Unsuccessful on 10.10"
date: 2010-11-10
forum: General Help
---

### Post by timetraveller85 on 2010-11-10
Hi guys,

I tried everything. I really did. I tried every possible (and applicable) scenarios in this page
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

I tried jockey.

And a host of other things but it simply won't work!

Here's the issue: After I install the driver and restart my Sony Vaio laptop, I get a purple screen with the following displayed 

                 Ubuntu
                 . . . . . .
in ultra-low resolution and then it freezes with just the purple screen visible:

I cannot CTRL+ALT+DEL my way out of it. I have to push the power button and restart it.


I have also tried reconfiguring my xorg.conf file by fetching the EDID, etc. NOTHING has worked.

PLEASE help. I really want desktop effects to work. I am not a gamer so I don't care about it. But I really need help with this. i LOVE Ubuntu but man, this is annoying me- (not to mention my track-pad doesn't work and my laptop goes into hibernate as soon as I unplug my power button)

Thanks again!!!

P.S. I couldn't find a discussion for graphics cards. Sorry If this is in the wrong place

---

### Post by fuzzyworbles on 2010-11-10
add-apt the xorg edgers ppa and apt-get nvidia-current 

works perfectly for me

---

### Post by sidzen on 2010-11-11
I take it from your post that you've looked at Ultimate and rejected it?
Try [SuperOS]("http://hacktolive.org/wiki/Super_OS#DVD-ISO_download"), just a refined ubuntu.  Hope it works for you --  that is, if fuzzywobble's suggestion doesn't!

---

### Post by timetraveller85 on 2010-11-11
> **sidzen said:**
> I take it from your post that you've looked at Ultimate and rejected it?
Try [SuperOS]("http://hacktolive.org/wiki/Super_OS#DVD-ISO_download"), just a refined ubuntu.  Hope it works for you --  that is, if fuzzywobble's suggestion doesn't!

fuzzywobble's suggestion didn't work. I may have to try super OS!

I hope it is what it's hyped up to be...

---

### Post by timetraveller85 on 2010-11-11
So how do I install nvidia from Super-OS? Is it just the usual method through jockey?

---

### Post by pqwoerituytrueiwoq on 2010-11-11
i have not tryed this on 10.10 (done this on 9.04,10.04) the nouveau driver has caused install issues on 10.04 for me (works best if you install a nvidia driver via System->Administration->Hardware Drivers first)
download the latest driver from nvidia
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
put the run file somewhere easy to get to via command line
then close the gui (write this down or you will not be able to read this while doing it (without 2 computers))
sudo service gdm stop
ctrl+alt+F1
login 
sudo sh /path/to/xxx.run
go through the installer
sudo service gdm start

---

### Post by timetraveller85 on 2010-11-11
I've tried that pqwoerituytrueiwoq.

It still didnt work. During the installation it disables nouveau but still NOTHING...

arghhh

---

### Post by Ancanus on 2010-11-11
Maybe your xorg.conf file has gone awfully wrong?

Try moving her to xorg.conf.bak

---

### Post by sidzen on 2010-11-12
One step at a time.  Has SuperOS been installed and,if so, does nVidea work out-of-box or not?
Best wishes,!  Select an Ultimate Edition repo to place in your sources.list, too, as a suggestion.

---

### Post by timetraveller85 on 2010-11-13
I tried Super OS. It didnt work out of the box. And after installing it through Jockey AND manually through an installation file, didnt work (I shut down X, installed it, then resrtarted X-server, all of it...) 

No avail. I am trying KDE at the moment. And I just say, this thing is brilliant. I guess I'll wait for the nouveau developers to come up with something.

Thanks a lot for the help guys. The Ubuntu community's amazing!

---

