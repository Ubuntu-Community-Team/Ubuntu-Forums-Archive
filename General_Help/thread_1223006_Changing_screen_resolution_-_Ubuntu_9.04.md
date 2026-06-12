---
title: "Changing screen resolution - Ubuntu 9.04"
date: 2009-07-25
forum: General Help
---

### Post by angerball on 2009-07-25
Hi,

Very much a beginner here, and need some help.

I have just installed Ubuntu 9.04, but can't change the screen resolution to other than 640 x 480 or 800 x 600.

I have updated NVidia driver, but it keeps giving me an error that I am not using the NVidia X driver. I have gone into the Terminal and under the device section, beside Driver it says "nvidia". What should I be doing here??

Totally lost, and frustrated here. ](*,)

I have googled it, and read some of the solutions, but to be honest, they are all assuming a lot of basic knowledge about Ubuntu, and it is completely over my head.

Can anyone please point me in the right direction?

many thanks,
angerball

---

### Post by apb2390 on 2009-07-25
This should be in "Absolute Beginner Talk", but setting that aside, I had the same problem.
You fix it by opening a terminal window and typing 
```
gksudo displayconfig-gtk
```Click on the monitor box, and select your monitor manufacturer and model. If it's not on there, or you don't know it, just select "Generic". Then, select if it's widescreen or not. After that, reboot and you should be good to go.

Infromation from [this thread...]("http://ubuntuforums.org/archive/index.php/t-887021.html")

---

### Post by angerball on 2009-07-25
Hi, and thanks for replying.

I typed that into the Terminal, but no Monitor Box came up. However I went into the Display menu again, and it still gives me the NVidia driver error. When I select Yes to use the graphic driver vendor's tool, it now brings up a window where I can change the resolution.
But I can't save it to the X Configuration File. I get an error message, "Unable to remove old x config backup file". Is there any way around this?

Thanks,
angerball

---

### Post by apb2390 on 2009-07-25
After some Googling I found this...

[http://www.linuxquestions.org/questions/linux-newbie-8/screen-resolution-problem-in-ubuntu-362160/](http://www.linuxquestions.org/questions/linux-newbie-8/screen-resolution-problem-in-ubuntu-362160/)

Also, you might want to download an nvidia driver first and install that. 
[URL="http://www.nvidia.com/Download/index.aspx?lang=en-us"]
http://www.nvidia.com/Download/index.aspx?lang=en-us[/URL]

---

### Post by rudnisty on 2009-07-25
> **apb2390 said:**
> This should be in "Absolute Beginner Talk", but setting that aside, I had the same problem.
You fix it by opening a terminal window and typing 
```
gksudo displayconfig-gtk
```Click on the monitor box, and select your monitor manufacturer and model. If it's not on there, or you don't know it, just select "Generic". Then, select if it's widescreen or not. After that, reboot and you should be good to go.

Infromation from [this thread...]("http://ubuntuforums.org/archive/index.php/t-887021.html")
5 star quote. I have got the same problem with 8.04 LTS , it helped as well. Thanks a lot again. Best regards - Rudnisty.

---

