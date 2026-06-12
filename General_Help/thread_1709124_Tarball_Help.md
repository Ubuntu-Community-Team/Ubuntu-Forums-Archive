---
title: "Tarball Help"
date: 2011-03-17
forum: General Help
---

### Post by galacticaboy on 2011-03-17
I need some help on how to compile a Tarball file. I know that there is really no need for Tarballs anymore, but for this one there is. Ubuntu does not recognize my webcam, and the only way I can get the driver for it is to download the Tarball file, it is in tar.gz format. I have no idea how to compile it. No one will tell me, they tell me that no one has to list step by step how to do that just for "me." It is because of this rudeness that I am no longer using that OS, so I am here at Ubuntu Forums hopefull to find someone not as rude to help me out. I do not know the command or what to do. So any help would be greatly appreciated! Thanks
David

---

### Post by LowSky on 2011-03-17
Could you tell us what webcam, and give us a link to the file.

Thanks

---

### Post by galacticaboy on 2011-03-17
When I open the terminal and type lsusb it says it is a SiGma Micro USB Web Cam, and the link to this file is... [http://linuxtv.org/hg/v4l-dvb/](http://linuxtv.org/hg/v4l-dvb/) at the left hand side you can click bz2, zip, or gz, I clicked gz. Thanks!
David

---

### Post by sisco311 on 2011-03-17
Assuming that you downoaded the .tar.gz file to your ~/Desktop, open a terminal and:
[list=i]
[*] Install the tools you need to compile the code:
```

sudo apt-get update
sudo apt-get install build-essential checkinstall
```

[*] Navigate to the directory where the archive is:
```
cd ~/Desktop
```

[*] Extract the archive:
```
tar xfvz v4l-dvb-*.tar.gz
```

[*] Compile the source code:
```
cd v4l-dvb-*/
make all

```

[*] Install it:
```
sudo checkinstall
```
[/list]

If you get any error messages, please post them here.

HTH

---

### Post by galacticaboy on 2011-03-17
Alright! Thanks! So far so good, its compiling, I hope this works. Now another question before I get to post the status if it worked or not, if this is not what I need for somereason, how am I to take all of this off, will I find it in the software center under installed programs or is there something else I have to do?

---

### Post by sisco311 on 2011-03-17
> **galacticaboy said:**
> Alright! Thanks! So far so good, its compiling, I hope this works. Now another question before I get to post the status if it worked or not, if this is not what I need for somereason, how am I to take all of this off, will I find it in the software center under installed programs or is there something else I have to do?

It's not a GUI app, so I don't think it will show up in Software Center, but you should be able to uninstall via Synaptic, apt-get:
```
sudo apt-get purge v4l-dvb
```
or dpkg:
```
sudo dpkg -r v4l-dvb
```

---

### Post by galacticaboy on 2011-03-17
Alright installing that did not work... so is there a way I can remove the package I just installed... I am so aggravated right now lol...

---

### Post by galacticaboy on 2011-03-17
Okay thanks for all of your help! You were very helpful! I think I can now compile a tarball file now! I will still look around to see if I can find the correct driver! Thank you so much!!
David

---

### Post by galacticaboy on 2011-03-18
I have found the right driver... so thanks for all of your help in this!! It was much appreciated!!
David

---

