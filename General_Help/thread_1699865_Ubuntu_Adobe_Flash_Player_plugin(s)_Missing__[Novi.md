---
title: "Ubuntu Adobe Flash Player plugin(s) Missing  [Novice to linux]"
date: 2011-03-04
forum: General Help
---

### Post by Vessot on 2011-03-04
Hello,

First, my apologies if this is the wrong category to post this, I was torn between here and the x86 64-bit users.  While on the 
note of apologies, as the thread implies, I am a novice to linux, and perhaps a bit to computers in general...so don't hesitate 
to explaining it to a dummy ^_^

I'm using a Flash Drive with Ubuntu (latest version I believe due to getting it only 4-5 days ago) and I'm capable enough to 
know how to restart the computer and run the software through my flashdrive and get Ubuntu up and going.  Past this point, I 
feel a bit lost as linux runs much different then Windows software.(least from my point of view)

**To get to the point!**

I was able to get flash player to work the first time with:
sudo apt-get install flashplugin-installer

And everything seemed to work fine, yet I know running it the way I do, means everything I do gets reset back to default 
after I turn off/restart my computer running the Ubuntu on the flashdrive.

Yesterday, I tried the same function, and I get an "unable to find package/plugin" error, and this continues to be the case 
almost regardless of what flash-related programs I try to remove via tips/suggestions.  They all come up as not present.

I noted at the start of the day, when I turned my computer on in it's windows 64bit vista mode that adobe flash had a 
new version/update out - so I'm not sure if that's part of the issue.

I've gotten as far as [http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)

and downloaded what it suggested, but alas...it didn't prove useful as that download page gives no installation instructions for noobies like my self, yet kindly offers uninstall tips.  -_-

So I have a folder of sorts with what I believe to be my cure, but I'm unaware how I use it in Linux...I figured unziping 
it may be the answer, but that led me to more headaches trying to figure out 7zip in linux...so I come here to plea for aid.

And, one last apology for unneeded information/long post for perhaps a short question-short answer thread. 
(Not to mention if it's already been addressed - I've searched a good deal, and have tried many threads suggestion with no avail)

---

### Post by wojox on 2011-03-04
Open your terminal and go to the directory you downloaded the package to and copy and paste this:

```
sudo tar -xvf flashplayer10_2_p3_64bit_linux_111710.tar.gz -C /usr/lib64/mozilla/plugins
```

You could also use the Firefox addon developed by one of our forum members, lovinlinux, in my signature.

---

### Post by Vessot on 2011-03-04
ubuntu@ubuntu:~$ sudo tar -xvf flashplayer10_2_p3_64bit_linux_111710.tar.gz -c /usr/lib64/mozilla/plugins

Yields this result:

tar: You may not specify more than one `-Acdtrux' or `--test-label' option
Try `tar --help' or `tar --usage' for more information.
ubuntu@ubuntu:~$ 


Just a note, I'm understanding that you want me to open the folder the file is in, and then open my terminal and use that code, correct?

Trying your second option/advise now.

Edit:  Your second option seems to have been my fix. Thank you very much!

---

### Post by wojox on 2011-03-04
No you need to open you terminal and cd to the directory. Ex. 

```
cd Downloads
```

Or wherever you downloaded it to.

---

