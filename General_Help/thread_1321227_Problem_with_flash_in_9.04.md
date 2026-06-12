---
title: "Problem with flash in 9.04"
date: 2009-11-09
forum: General Help
---

### Post by giyad on 2009-11-09
I just installed Ubuntu Jaunty, this is my first time installing a Linux distro.  I was looking up the best apps to install and in a list I read to install the flash player by

```
sudo apt-get install flashplugin-nonfree

```


I did that, but when I go to sites now to watch video, such as youtube, most videos won't play.... the weird thing is, its not all videos, its just most.  I was able to play some.  Whats going on here?


I heard ubuntu was going to be an easy switch, its not turning out to be so easy...

---

### Post by pilorama on 2009-11-09
You must associate flash plugin whith your browser. In firefox, as far as I remember, you should add something like FIREFOX_DSP="aoss" to "firefoxrc" file

---

### Post by giyad on 2009-11-09
> **pilorama said:**
> You must associate flash plugin whith your browser. In firefox, as far as I remember, you should add something like FIREFOX_DSP="aoss" to "firefoxrc" file
I'm sorry, as I said I'm a noobie in Linux...  How do i add that to firefoxrc file?  Are you sure about it, you said "add something like" haha...

---

### Post by MelDJ on 2009-11-09
try downloading and installing the flash package from here: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by giyad on 2009-11-09
> **MelDJ said:**
> try downloading and installing the flash package from here: [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
I get this when I run the deb, it seems its because Im on the 64 bit version...

> dpkg: error processing install_flash_player_10_linux.deb (--install):
 package architecture (i386) does not match system (amd64)
Errors were encountered while processing:
 install_flash_player_10_linux.deb

---

### Post by MelDJ on 2009-11-09
just double click the package and install it

---

### Post by giyad on 2009-11-09
> **MelDJ said:**
> just double click the package and install it
Ok, not solving it.  It still says Status:  "Error: Wrong architecture 'i386'"

---

### Post by MelDJ on 2009-11-09
download the 32-bit version of flash and see if it works. ]

---

### Post by giyad on 2009-11-09
> **MelDJ said:**
> download the 32-bit version of flash and see if it works. ]
that was the 32 bit version... thats why its not working ;-) theres no option on adobe flash to download the 64 bit version, so i don't think they make one...

---

### Post by MelDJ on 2009-11-09
whoops. my bad :p
try this: [http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html)

---

### Post by giyad on 2009-11-10
> **MelDJ said:**
> whoops. my bad :p
try this: [http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html)
Thanks, that page didn't actually work but it led me to [this page]("http://meandubuntu.wordpress.com/2008/11/18/real-64-bit-flash-on-amd64/") which did :D

---

### Post by PB_G3 on 2009-11-10
There is a newer one here: [http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")

---

### Post by giyad on 2009-11-10
> **PB_G3 said:**
> There is a newer one here: [http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")
it links to the same download page, but my URL has the instructions on how to install it as well :), thanks though, where were you two hours ago??? :p

---

### Post by lidex on 2009-11-10
Another fix [here]("http://ukanth.in/blog/?p=48")
[here]("http://ubuntuforums.org/showthread.php?t=891458&page=3") and [here]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html")

---

### Post by adamn on 2009-11-10
> **lidex said:**
> Another fix [here]("http://ukanth.in/blog/?p=48")
[here]("http://ubuntuforums.org/showthread.php?t=891458&page=3") and [here]("http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html")

I tried this (linked to from above post)

Just execute this commands in the console:

# 1. delete installed:
sudo apt-get remove mozilla-plugin-gnash swfdec-mozilla flashplugin-nonfree

# 2. create new folder for Flashplayer:
sudo mkdir /usr/lib/flashplugin-nonfree/

# 3. copy the new Flashplayer in the just created folder. change the first
# term to the unpacked path.
# if you unpacked to your Desktop, replace YourDownloadPath with
# /home/YourLoginName/Desktop

sudo cp YourDownloadPath/libflashplayer.so /usr/lib/flashplugin-nonfree/

# 4. give Firefox the Flashplayer as Plugin , by creating a symbolic Link
# to the path of the Flashplayers in Plugin-folder from Firefox:
sudo ln -s /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so

Now my FF crashes when I go to flash sites.

How can i delete all flash (system wide) and start over?

Thanks

---

### Post by giyad on 2009-11-10
> **adamn said:**
> I tried this (linked to from above post)

Just execute this commands in the console:

# 1. delete installed:
sudo apt-get remove mozilla-plugin-gnash swfdec-mozilla flashplugin-nonfree

# 2. create new folder for Flashplayer:
sudo mkdir /usr/lib/flashplugin-nonfree/

# 3. copy the new Flashplayer in the just created folder. change the first
# term to the unpacked path.
# if you unpacked to your Desktop, replace YourDownloadPath with
# /home/YourLoginName/Desktop

sudo cp YourDownloadPath/libflashplayer.so /usr/lib/flashplugin-nonfree/

# 4. give Firefox the Flashplayer as Plugin , by creating a symbolic Link
# to the path of the Flashplayers in Plugin-folder from Firefox:
sudo ln -s /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so

Now my FF crashes when I go to flash sites.

How can i delete all flash (system wide) and start over?

Thanks
Follow the instructions on [this site]("http://www.myscienceisbetter.info/install-adobe-flash-player-10-on-ubuntu-64bit.html"), at step 3 where it tells you to "wget" that link is broken.  So, just download the file from [here]("http://labs.adobe.com/downloads/flashplayer10.html") and continue to follow the instructions on the first site with the appropriate changes.

You only need to change these lines to account for the file that you downloaded
> tar zxvf flashplayer10_install_linux_051508.tar.gz
sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins/
rm -rf ~/install_flash_player_10_linux/

---

### Post by lidex on 2009-11-10
Using this tutorial for x64 you'll want to also remove flashplugin-installer. So make this line:
```
# delete installed:
sudo apt-get remove mozilla-plugin-gnash swfdec-mozilla flashplugin-nonfree
```

look like this:
```
# delete installed:
sudo apt-get remove mozilla-plugin-gnash swfdec-mozilla flashplugin-nonfree flashplugin-installer

```

---

### Post by adamn on 2009-11-10
> **giyad said:**
> Follow the instructions on [this site]("http://www.myscienceisbetter.info/install-adobe-flash-player-10-on-ubuntu-64bit.html"), at step 3 where it tells you to "wget" that link is broken.  So, just download the file from [here]("http://labs.adobe.com/downloads/flashplayer10.html") and continue to follow the instructions on the first site with the appropriate changes.

You only need to change these lines to account for the file that you downloaded

On Step 4 I got an error 
Step 4: sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

Here is the 'error' I got:
nspluginwrapper: no appropriate viewer found for /usr/lib/mozilla/plugins/libflashplayer.so

---

### Post by adamn on 2009-11-10
PS. This is in Firefox (about plugins)

File name:  libflashplayer.so 
Shockwave Flash 10.0 r32

 application/x-shockwave-flash Shockwave Flash swf Yes
 application/futuresplash FutureSplash Player spl Yes

---

### Post by giyad on 2009-11-10
make sure firefox is closed while you're doing all this.

Run all 3 commands in that step, even if it throws the error at you.  Then start up firefox and type in "about:plugins", you should see flash installed.

Go try it out on youtube or something.

I got that error as well, not sure if running the other two steps changed anything, but in the end it works for me, so i don't care about that error haha... if someone can tell me what that error means I'd probably try to fix it, but if it ain't broke don't fix it...

---

### Post by giyad on 2009-11-10
> **adamn said:**
> PS. This is in Firefox (about plugins)

File name:  libflashplayer.so 
Shockwave Flash 10.0 r32

 application/x-shockwave-flash Shockwave Flash swf Yes
 application/futuresplash FutureSplash Player spl Yes
sounds like everythings good to go for you as well... go test it out

---

### Post by adamn on 2009-11-10
Sorry, let me be more clear.

I did close firefox before running the commands.
I did run all 3 commands in that order, regardless of the fact that the first one threw an error.
I restarted firefox and it says that flash is installed

Yet, everytime I open a website that uses flash, it crashes. (Firefox)

---

### Post by adamn on 2009-11-10
Anyone else have any ideas?

---

### Post by adamn on 2009-11-10
I installed Arora web browser and it also crashes on youtube, pandora, etc., any website that use flash i guess.

---

### Post by adamn on 2009-11-10
Even after running the following, I still have flash installed in Firefox. I ran it, restarted, and checked the firefox plugins page and I still have it installed. 

sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper

---

### Post by adamn on 2009-11-10
Figured it out. 

First I went to the directory in which flash was upacked (Downloads), and then ran cp from there using:

sudo cp libflashplayer.so /usr/lib/mozilla/plugins/

Bamb! No more browser crashing

---

