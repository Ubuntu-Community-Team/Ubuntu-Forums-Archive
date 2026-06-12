---
title: "Trouble installing flash: Help, please."
date: 2010-08-07
forum: General Help
---

### Post by techiewannabe on 2010-08-07
When I try to install flash software, I get the following message:

[INDENT]Download done.
Flash Plugin installed.
update-alternatives: error: alternative link /usr/lib/iceape/plugins/flashplugin-alternative.so is already managed by iceape-flashplugin.before_restore_2009-11-29_18.11.11.638241.
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 ttf-wqy-zenhei
 ttf-dejavu-extra
 ttf-dejavu
 libprojectm2
 audacious-plugins-extra
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
tom@Compaq:~$ 
[/INDENT]
In the meantime, without flash installed, I can't view and hear streaming, such as YouTube, on the Internet.

Can someone help me manage this problem? I'm afraid that I don't understand it. Even though I've used Ubuntu for most of this year, I consider myself very much a newbie.

Thanks in advance.

techiewannabe

---

### Post by Ozymandias_117 on 2010-08-07
> **techiewannabe said:**
> When I try to install flash software, I get the following message:

[INDENT]Download done.
Flash Plugin installed.
update-alternatives: error: alternative link /usr/lib/iceape/plugins/flashplugin-alternative.so is already managed by iceape-flashplugin.before_restore_2009-11-29_18.11.11.638241.
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 ttf-wqy-zenhei
 ttf-dejavu-extra
 ttf-dejavu
 libprojectm2
 audacious-plugins-extra
 flashplugin-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
tom@Compaq:~$ 
[/INDENT]
In the meantime, without flash installed, I can't view and hear streaming, such as YouTube, on the Internet.

Can someone help me manage this problem? I'm afraid that I don't understand it. Even though I've used Ubuntu for most of this year, I consider myself very much a newbie.

Thanks in advance.

techiewannabe

What do you get with ```
ls -l /etc/alternatives/iceape-flashplugin 
```

---

### Post by clhsharky on 2010-08-07
techiewannabe

FLASH-AID by lovinglinux

[http://feedproxy.google.com/~r/lovinglinuxtut/~3/j7idaxv11dM/flash-issues-solutions.html](http://feedproxy.google.com/~r/lovinglinuxtut/~3/j7idaxv11dM/flash-issues-solutions.html)
[https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

Sharky

---

### Post by techiewannabe on 2010-08-07
Ozymandias_117:

With the command you suggested, I get the following message:
[INDENT]tom@Compaq:~$ ls -l /etc/alternatives/iceape-flashplugin
ls: cannot access /etc/alternatives/iceape-flashplugin: No such file or directory
tom@Compaq:~$ 
[/INDENT]Thanks for your willingness to help with this.

---

### Post by bprins on 2010-08-07
Maybe this is completely useless, but which internet browser are you using? firefox? 

what you could try, if you havent, is install chrome. google ubuntu chrome and you'll have it quickly. 

i know, not rly a solution, but it might at least give you the ability to watch movies etc.

---

### Post by techiewannabe on 2010-08-07
bprins:
I'm using Firefox but considered trying Chrome. I wasn't sure how to install  it. I don't believe it is in Synaptic, is it? If not, can you suggest a tutorial for me?
Thanks.

---

### Post by bprins on 2010-08-07
that might become easier then you would expect.

its not in the default repositories, but, if you go to this page:
[http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb](http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb)

then you can download the .deb file which will install both the new repository and chrome at once. can't make it easier then that :)

good luck

---

### Post by Ozymandias_117 on 2010-08-07
> **techiewannabe said:**
> bprins:
I'm using Firefox but considered trying Chrome. I wasn't sure how to install  it. I don't believe it is in Synaptic, is it? If not, can you suggest a tutorial for me?
Thanks.

The open source edition of Chrome is in the repositories. It's chromium-browser. It is the exact same as Google chrome, except it doesn't have the stuff that sends usage statistics back to Google.

```
sudo aptitude install chromium-browser
```

---

### Post by Ozymandias_117 on 2010-08-07
The only thing I can suggest then, is to install it manually... (Please note, these commands will only work if you have a 32-Bit system! If you don't, or are unsure, let me know!)

```
wget "http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz" && tar -xvzf ./install_flash_player_10_linux.tar.gz && sudo cp ./libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so && rm ./install_flash_player_10_linux.tar.gz
```

---

### Post by techiewannabe on 2010-08-07
bprins
You weren't' kidding! It was much easier to install Chrome than I ever would have imagined! Very cool!
Thanks for the help.
Nonetheless, I would still like to fix the problems with Firefox.

---

### Post by techiewannabe on 2010-08-07
Ozymandias_117:
Thanks for your suggestion. I'm afraid that it didn't do the trick. My system is 32 bit.
I can use Chrome, if need be, but would like to get Firefox working....
I'm certainly open to other ideas.
Thanks.

---

### Post by Ozymandias_117 on 2010-08-07
> **techiewannabe said:**
> Ozymandias_117:
Thanks for your suggestion. I'm afraid that it didn't do the trick. My system is 32 bit.
I can use Chrome, if need be, but would like to get Firefox working....
I'm certainly open to other ideas.
Thanks.

Do ```
ls /usr/lib/mozilla/plugins | grep libflash
``` to confirm the libflashplayer.so is there. If it is, open Firefox, and click "Tools -> Addons" and click the Plugins tab. See if by any chance Shockwave Flash is just disabled.

---

### Post by techiewannabe on 2010-08-07
Ozymandias_117:

Thanks for your suggestion. Here is the "reply" when I typed in the command you suggested. 

tom@Compaq:~$ ls /usr/lib/mozilla/plugins | grep libflash
libflashplayer.so

I checked to see whether flash was disabled. It was not. However, I tried to disable, then enable it to see if it made a difference. It did not.

Do you think that I should simply uninstall Firefox, then reinstall?

Thanks.

---

### Post by deserthowler on 2010-08-07
Did you try the Adobe Flash Installer in the repositories?  It is also in the software center.

Earl

---

### Post by Ozymandias_117 on 2010-08-07
> **techiewannabe said:**
> Ozymandias_117:

Thanks for your suggestion. Here is the "reply" when I typed in the command you suggested. 

tom@Compaq:~$ ls /usr/lib/mozilla/plugins | grep libflash
libflashplayer.so

I checked to see whether flash was disabled. It was not. However, I tried to disable, then enable it to see if it made a difference. It did not.

Do you think that I should simply uninstall Firefox, then reinstall?

Thanks.

So, according to the "plugins" page, you have flash, and it's enabled, but when you go to a site, it says you don't?

---

### Post by techiewannabe on 2010-08-08
Thanks deserthowler and Ozymandias_117:

My system shows that Adobe Flash plugin is installed. However, if I try to view a video such as one on YouTube, I usually can't see the video. A moment ago, for example, I went to YouTube. I clicked on a video. At first I got an error message asking me to search for installer. However, sometimes all I see is a black rectangle where the video is supposed to be. This morning, quite unexpectedly, I was able to see the images but unable to hear any sound.

Very confusing because the problem description changes from time to time. 

I appreciate your persistence with this.

---

### Post by Ozymandias_117 on 2010-08-08
> **techiewannabe said:**
> Thanks deserthowler and Ozymandias_117:

My system shows that Adobe Flash plugin is installed. However, if I try to view a video such as one on YouTube, I usually can't see the video. A moment ago, for example, I went to YouTube. I clicked on a video. At first I got an error message asking me to search for installer. However, sometimes all I see is a black rectangle where the video is supposed to be. This morning, quite unexpectedly, I was able to see the images but unable to hear any sound.

Very confusing because the problem description changes from time to time. 

I appreciate your persistence with this.

What version of firefox are you using?

---

### Post by techiewannabe on 2010-08-08
Firefox version is 3.6.8. (Screenshot is attached.)

Thanks.

---

### Post by Ozymandias_117 on 2010-08-08
Try ```
mv ~/.mozilla ~/.mozilla-bak
```

then run ```
firefox -safe-mode
``` and press continue in safe mode. See if either of those fixes the problem.

---

### Post by techiewannabe on 2010-08-08
Here is the message I get when I try the first command: 


tom@Compaq:~$ mv ~/.mozilla ~/.mozilla-bak
mv: cannot stat `/home/tom/.mozilla': No such file or directory
tom@Compaq:~$ 


Thanks for your patience.

---

### Post by Ozymandias_117 on 2010-08-08
> **techiewannabe said:**
> Here is the message I get when I try the first command: 


tom@Compaq:~$ mv ~/.mozilla ~/.mozilla-bak
mv: cannot stat `/home/tom/.mozilla': No such file or directory
tom@Compaq:~$ 


Thanks for your patience.

That's odd... I'm not sure why you wouldn't have a preferences folder... I guess you can still try the second one, but you may want to try reinstalling firefox.

---

### Post by techiewannabe on 2010-08-08
I did reinstall but problems persist. Here are the error messages I received during the uninstall/reinstall process using Synaptic.


Here is the error message I got when I uninstalled Firefox:

E: ttf-wqy-zenhei: subprocess installed post-installation script returned error exit status 1
E: ttf-dejavu-extra: subprocess installed post-installation script returned error exit status 1
E: ttf-dejavu: dependency problems - leaving unconfigured
E: libprojectm2: dependency problems - leaving unconfigured
E: audacious-plugins-extra: dependency problems - leaving unconfigured
E: flashplugin-installer: subprocess installed post-installation script returned error exit status 2


Here is the message when I tried to reinstall Firefox:

E: ttf-wqy-zenhei: subprocess installed post-installation script returned error exit status 1
E: ttf-dejavu-extra: subprocess installed post-installation script returned error exit status 1
E: ttf-dejavu: dependency problems - leaving unconfigured
E: libprojectm2: dependency problems - leaving unconfigured
E: audacious-plugins-extra: dependency problems - leaving unconfigured

Here is the message I got when I tried to reload Adobe flash plug-in

E: ttf-wqy-zenhei: subprocess installed post-installation script returned error exit status 1
E: ttf-dejavu-extra: subprocess installed post-installation script returned error exit status 1
E: ttf-dejavu: dependency problems - leaving unconfigured
E: libprojectm2: dependency problems - leaving unconfigured
E: audacious-plugins-extra: dependency problems - leaving unconfigured
E: flashplugin-installer: subprocess installed post-installation script returned error exit status 2


Again, thanks for your patience.

---

### Post by bprins on 2010-08-08
might give this a try. sounds like similar problem -> solution.

[http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/](http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/)

---

### Post by deserthowler on 2010-08-08
> **techiewannabe said:**
> Here is the message I get when I try the first command: 


tom@Compaq:~$ mv ~/.mozilla ~/.mozilla-bak
mv: cannot stat `/home/tom/.mozilla': No such file or directory
tom@Compaq:~$ 


Thanks for your patience.

No ~/.mozilla?  Maybe you need to reinstall Firefox?

Earl

---

### Post by techiewannabe on 2010-08-09
Thanks deserthowler and bprins for your suggestions. 

Deserthowler, I did reinstall Mozilla, but got several error messages during the process. 

Bprins, I will try the suggestions from the link that you sent me, but it will take some time. In the first place, I'm not very confident in the use of the terminal. (I need to get a better grasp of it.) Secondly, I am going on vacation shortly and may not be able to find time to mess with this problem. (I'll either get it in the next 24 hours or it will be over a week from now.)

I really do want to fix this problem! The only good part of this problem is that it made me get familiar with Chrome; it is quite a good browser.

Thanks for your patience with me on this.

Tom

---

### Post by bprins on 2010-08-10
You'll have to get more confident in using terminal sooner or later, so better start right away. And don't be afraid of destroying stuff. You can't make it much worse then it already is. :-).

---

### Post by techiewannabe on 2010-08-11
Thanks, bprins.

I'll just keep working on the command line....

Tom

---

