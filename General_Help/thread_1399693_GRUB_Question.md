---
title: "GRUB Question"
date: 2010-02-06
forum: General Help
---

### Post by Whisp3r on 2010-02-06
I have a Dell 14, dual boot with Windows Vista/Karmic 9.10.

My Kernel has updated several times since I did the install, and all the versions of the kernel are on my grub boot menu. I have grub 1.97. How do I remove these extra kernels from the boot list?

---

### Post by yunone on 2010-02-06
read my mind...after todays kernel upgrade i noticed my GRUB menu getting very portly

---

### Post by yunone on 2010-02-06
[http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/)

[http://www.linuxquestions.org/questions/ubuntu-63/need-to-remove-old-versions-of-ubuntu-kernel-466660/](http://www.linuxquestions.org/questions/ubuntu-63/need-to-remove-old-versions-of-ubuntu-kernel-466660/)

[http://www.pendrivelinux.com/how-to-remove-old-kernel-images/](http://www.pendrivelinux.com/how-to-remove-old-kernel-images/)

---

### Post by Whisp3r on 2010-02-06
I guess I have GRUB2, even tho my grub boot screen says 1.97 beta4? It's a fresh install of 9.10? I'm confused. 

I don't have a menu.lst in my /boot/grub/ folder. I do have the grub.cfg tho.

---

### Post by tubbygweilo on 2010-02-06
I find that System > Administration > Computer Janitor does the job for me. Just make sure you unclick things you wish to keep and click the old kernel upgrade you wish to remove.

---

### Post by QIII on 2010-02-06
Beware computer janitor.  It is easy to do things you do not want to do and make yourself very unhappy.

GRUB2 is GRUB 1.97 beta4 because it's, well, a Beta.  It's a work in progress.  And it does not use menu.lst, so you can take that out of your vocabulary.  

Do NOT try to update grub.cfg directly (you will probably be told you can't anyway).  There is a whole new way of configuring GRUB2, but that is a subject that has been covered ad nauseum in other threads (do a search for RanchHand's posts.)

The easiest thing for you to do would be to use Synaptic to get rid of the old chaff.

Do a search on "linux-image", then sort everything you get back alphabetically.  You'll notice that you have (in descending order) linux-image 2.6.31-19/18(?)/17 .... (you'll have 19 if you have the latest).

I suggest keeping the current and previous kernels.  The previous as a fall-back.  Check all the older ones for removal.

Now, search for "linux-headers", sort as above, and mark as above, keeping the current and previous.

Apply the changes.

When the old ones are removed, go to the terminal

```
sudo update-grub2
```

---

### Post by switch10 on 2010-02-06
> **tubbygweilo said:**
> I find that System > Administration > Computer Janitor does the job for me. Just make sure you unclick things you wish to keep and click the old kernel upgrade you wish to remove.


I usually just use package manager.  I couldn't figure out how to do this with "computer janitor"  this is what computer janitor is showing for me:

---

### Post by Gadgetech on 2010-02-06
Check out this page: [http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/](http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/)
One reader posted this command in the comments. It removes all but the latest kernel from your system.
```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get purge
```

---

### Post by QIII on 2010-02-06
Beware long commands C&P'd from someone's post.  Many an unwitting user has done great damage to himself and his OS by pasting a command into the terminal and pressing enter, only to find that the code is either deliberately malicious or ignorantly malformed.

---

### Post by Gadgetech on 2010-02-06
You actually need to insert a **-y** before **purge** at the end of the command to force the removal. Here's what the terminal output looks like without the **-y** on my Karmic installation.
```
user@karmic:~$ dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-2.6.31-16* linux-headers-2.6.31-16-generic*
  linux-headers-2.6.31-17* linux-headers-2.6.31-17-generic*
  linux-image-2.6.31-16-generic* linux-image-2.6.31-17-generic*
0 upgraded, 0 newly installed, 6 to remove and 0 not upgraded.
After this operation, 345MB disk space will be freed.
Do you want to continue [Y/n]? Abort.

```
If you want to digest what this command is doing, break it up at the pipes and try it in steps. Like I said, to actually remove the kernels, insert a **-y** between "apt-get" and "purge" at the end of the command.

---

### Post by a person on 2010-02-07
As the poster of that comment, I'd like to point out that I had no malicious intent.  I just found it off of a bug report on launchpad and found it handy.

---

### Post by DennisFolsom on 2010-02-07
As recommended in the  [Grub 2 Guide]("http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub+menu"), and discussed here, I just used the Synaptic Package Manager to remove an old version of the Kernel from my Grub menu (and from my system). 

While following the recommended steps, I was concerned that I had both a **linux-headers-2.6.31-14** and a  **linux-headers-2.6.31-14-generic**. Since the "-generic" entry was what showed in the Grub 2 menu item that I was trying to get rid of, I deleted that one, along with the corresponding **linux-image-2.6.31-14**, leaving the installed **linux-headers-2.6.31-14** package in place.  This did accomplish the desired result of cleaning up the menu.  [COLOR=red]Should I have removed all three?[/COLOR]  I suspect that I should have.

---

### Post by Whisp3r on 2010-02-08
It worked using the synaptic manager / update-grub2 method. Thank you all for your help.

---

### Post by QIII on 2010-02-08
> **a person said:**
> As the poster of that comment, I'd like to point out that I had no malicious intent.  I just found it off of a bug report on launchpad and found it handy.

I apologize.  I didn't intend to point that at you.

---

### Post by Leppie on 2010-02-08
> **QIII said:**
> GRUB2 is GRUB 1.97 beta4 because it's, well, a Beta.  It's a work in progress.  And it does not use menu.lst, so you can take that out of your vocabulary.
i don't believe the numbering has much to do with the naming. grub (or grub 1 or grub legacy) halted at v.0.97. name and version number do not necessarily have to match... just like java 6 is actually 1.6.xx

> **QIII said:**
> Do NOT try to update grub.cfg directly (you will probably be told you can't anyway).  There is a whole new way of configuring GRUB2, but that is a subject that has been covered ad nauseum in other threads (do a search for RanchHand's posts.)
the grub warnings have always been in the configuration files. grub2 differs from grub legacy in that it offers scripts which can be modified with not too much digging into the mechanisms.

> **QIII said:**
> The easiest thing for you to do would be to use Synaptic to get rid of the old chaff.
+1, i would like to comment though that it's probably best to keep the 14 kernel version for karmic users. this is the default stock kernel and probably the least likely to give any errors. may come in handy when a later kernel version does not want to boot (anymore). it's better to hide it in the menu.

> **QIII said:**
> When the old ones are removed, go to the terminal

```
sudo update-grub2
```
this command is actually for those upgrading from grub legacy, it will still work but it's better to use the normal command:
```
sudo update-grub
```

---

### Post by Manyette on 2010-02-08
> The easiest thing for you to do would be to use Synaptic to get rid of the old chaff.

I did use synaptic to remove 2-6-31-xx, all except 19 and 20.  This worked just fine, BUT, I now find I cannot get to the grub menu using the shift key.  I've tried from a cold boot several time, after using both "update-grub" and "update-grub2".  Anyone have an idea why this shoule be so?  Appreciate any help.

---

### Post by scouser73 on 2010-02-08
Every time Ubuntu installs a new Linux kernel, the old one is left behind. This means that if you are regularly updating an Ubuntu system the Grub boot menu becomes longer and longer with kernels you don’t need anymore.

The old kernels are deliberately left installed and on the menu so you can boot a previous kernel if you have trouble with a new one. But if the new one works, you can safely uninstall the old kernel, which will also result in the Grub menu being cleaned up.

Follow these steps to identify and remove any old kernels.

**1** - Go to **Terminal** and paste the following command: **uname -r**
It will print the version of the Linux kernel you are running, this is the one you want to keep. It should look something like this: ***2.6.20-16-generic***

**2** - Go to **Synaptic Package Manager** via the **System > Administration** menus

**3** - Paste this: **linux-image-2** into the search box of **Synaptic Package Manager**

**4** - Once you have located the old kernels, **hightlight** them and **right-click** then select **Mark For Complete Removal** then click **Mark** and then click **Apply**

The results should show every available and installed kernel. A green box on the left indicates that the package is installed. The only linux-image you want installed is the latest one.

[COLOR="Red"]**Be careful of what you remove. Ensure that you don’t remove your current kernel, or anything that is not a linux-image. It is possible to break Ubuntu if you remove the wrong kernel.**[/COLOR]

Your computer and Grub menu should now be free of old kernels.

---

### Post by Leppie on 2010-02-08
> **Manyette said:**
> I did use synaptic to remove 2-6-31-xx, all except 19 and 20.  This worked just fine, BUT, I now find I cannot get to the grub menu using the shift key.  I've tried from a cold boot several time, after using both "update-grub" and "update-grub2".  Anyone have an idea why this shoule be so?  Appreciate any help.
could you post your grub defaults file:
```
cat /etc/default/grub
```

---

### Post by Manyette on 2010-02-08
> **Leppie said:**
> could you post your grub defaults file:
```
cat /etc/default/grub
```
File attached.  1.97 beta.
GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"

---

### Post by Leppie on 2010-02-08
open the grub defaults file with a text editor:
```
gksudo gedit /etc/default/grub
```
modify the following two lines like this (or set to the amount of seconds you would like for the timeout):
```
GRUB_HIDDEN_TIMEOUT="5"
```
then run update-grub:
```
sudo update-grub
```

---

### Post by Manyette on 2010-02-08
Hi Leppie, changed as suggested.  Original file was 0 without quotes, so I tried to set it to both 5 and "5", and rand update-grub after each try, but neither of those made any difference.  ( And you do seem user-friendly to me!)

---

### Post by Leppie on 2010-02-08
> **Manyette said:**
> Hi Leppie, changed as suggested.  Original file was 0 without quotes, so I tried to set it to both 5 and "5", and rand update-grub after each try, but neither of those made any difference.
i'm getting the feeling you are affected by one of the grub2 bugs. sometimes after having edited the grub defaults file, the menu won't hide or show anymore. have you ever received any updates for grub2?

> **Manyette said:**
> ( And you do seem user-friendly to me!)
there's people on this forum who'd probably disagree, but thanks :D

could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

---

### Post by Manyette on 2010-02-08
> i'm getting the feeling you are affected by one of the grub2 bugs. sometimes after having edited the grub defaults file, the menu won't hide or show anymore. have you ever received any updates for grub2?

Hi Leppie, I'm not certain.  I think there were some grub updates a few weeks ago, but there haven't been any recently to my knowledge.  I don't know if this is a bug or not.  But it did work prior to the "20" kernel update.  So it was either that, or I deleted something using synaptic that I shouldn't have, even though I did follow the instructions above as prescribed.  ( I don't know enough to vary from them, sadly )  But I thank you for the help.  It's not really a big deal.  Come april I'm going to move to Lyric, although I have to admit, right now I'm quite impressed with Karmic.  Ubuntu had sure come a long way in the past year or so. Again, my thanks for trying.
P.S. I should add that I did NOT edit anything after the kernel update to "20".  At least up until your suggestion.

---

### Post by drs305 on 2010-02-08
Manyette,

If the keystatus isn't being checked for some reason, here is a way to find out:

Add this to the end of */etc/grub.d/00_header*, update-grub and then reboot and see if you can display the menu by holding down the SHIFT key *at the very start of the boot*. Note: This section is lifted from the *30_os-prober* file.

> 
	cat <<EOF
if [ \${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep$verbose --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
EOF


---

### Post by Leppie on 2010-02-08
> **Manyette said:**
> Hi Leppie, I'm not certain.  I think there were some grub updates a few weeks ago, but there haven't been any recently to my knowledge.  I don't know if this is a bug or not.  But it did work prior to the "20" kernel update.  So it was either that, or I deleted something using synaptic that I shouldn't have, even though I did follow the instructions above as prescribed.  ( I don't know enough to vary from them, sadly )  But I thank you for the help.  It's not really a big deal.
if you want, you could try to completely remove grub2 and then re-install it. no guarantees it will work afterwards though.

> **Manyette said:**
> Come april I'm going to move to Lyric, although I have to admit, right now I'm quite impressed with Karmic.  Ubuntu had sure come a long way in the past year or so. Again, my thanks for trying.
i'm waiting for the new lts release as well, should be good ;)

> **Manyette said:**
> P.S. I should add that I did NOT edit anything after the kernel update to "20".  At least up until your suggestion.
funny that you mentioned that, i just run update manager, but my kernel version is 19... are you using the proposed repo? those are pre-releases.

---

### Post by Manyette on 2010-02-08
> **Leppie said:**
> if you want, you could try to completely remove grub2 and then re-install it. no guarantees it will work afterwards though.


i'm waiting for the new lts release as well, should be good ;)


funny that you mentioned that, i just run update manager, but my kernel version is 19... are you using the proposed repo? those are pre-releases.

Hi Leppie, Well, you are correct, because I do have the "proposed" updates enabled in the repo's, and 20 showed up this morning.  That could be the problem, certainly.  (It hasn't bitten me, at least, up until now!Q\:confused:)  Sorry, I should have mentioned that.  But yes, I am looking forward to lyric.  I've got the alpha2 on a usb stick, and it does look very impressive indeed.  Again, thanks for the  help, I do appreciate it.  And again, this is not a big deal.  I got rid of the "surplus" kernels, and that was the main intent.  Lyric isn't that far off!

---

### Post by Leppie on 2010-02-08
try drs305's suggestion ;)

---

### Post by Manyette on 2010-02-08
Hi, I did try his suggestion, and the shift key is recognized.  Now in the process of restoring everything as I found it.  But thanks.

---

### Post by Leppie on 2010-02-08
> **Manyette said:**
> Hi, I did try his suggestion, and the shift key is recognized.  Now in the process of restoring everything as I found it.  But thanks.
since you already are restoring and had not really made any personal modifications, you could try re-installing grub2:
```
sudo apt-get purge grub grub-pc grub-common
sudo rm -rf /boot/grub/
sudo apt-get install grub-pc grub-common
```
if you get messages that some package is not installed or the folder /boot/grub does not exist when trying to remove it, don't worry about that and just continue. if you did not make any modifications to your grub2 setup, you should more or less have the same setup (except that hopefully the shift key will work after this).

---

### Post by Manyette on 2010-02-08
Hi gang, well here are the results, and I (just dumb luck, I assure you) removed and restored grub one piece at a time, and I got very lucky.  the last file I upgraded to the "20" subversion was the "grub-common".  Now this was lucky because up until I restored that last file of the group, the shift key to grub menu worked just fine, After I restored the grub-common the shift key to grub menu stopped working, so it appears that that is the file which contains the bug in the "20" kernel subversion, and is why the shift to grub menu stopped working.  Hope this info will help someone else along the line.  And again, thanks to all for all the help.

---

### Post by Manyette on 2010-02-08
To finish this up, I had to downgrade grub-common down to version beta4-1ubunt3 to make the shift key work properly. So the bug is in the two latest versions.  But all is working well in subversion "20" with this change. So, all is well, and again my thanks to all.

---

### Post by Leppie on 2010-02-08
well, glad that it's working now. if you feel like it, you could report a bug for this.

---

### Post by Manyette on 2010-02-08
Hi Leppie, As a matter of fact I just finnished reporting the bug.  I suppose it's okay, even though it's a "proposed" kernel update.  Anyway, if you're interested, it's bug 519131 if you care to track it.  And again my thanks.

---

### Post by QIII on 2010-02-11
> **Leppie said:**
> i don't believe the numbering has much to do with the naming. grub (or grub 1 or grub legacy) halted at v.0.97. name and version number do not necessarily have to match... just like java 6 is actually 1.6.xx


the grub warnings have always been in the configuration files. grub2 differs from grub legacy in that it offers scripts which can be modified with not too much digging into the mechanisms.


+1, i would like to comment though that it's probably best to keep the 14 kernel version for karmic users. this is the default stock kernel and probably the least likely to give any errors. may come in handy when a later kernel version does not want to boot (anymore). it's better to hide it in the menu.


this command is actually for those upgrading from grub legacy, it will still work but it's better to use the normal command:
```
sudo update-grub
```

I like to quibble sometimes just for the fun of it, so take this as friendly banter only.  :)

grub.cfg should virtually never be updated by hand.  If a user makes edits without knowing what he is doing, he stands a better chance of getting struck by lightning than having his machine boot again.  (OK, so I exaggerate...).  And the changes would likely be overwritten after using update-grub(2) later.

Actually update-grub and update-grub2 are interchangeable in many respects. update-grub2, by default, keeps grub.cfg read only.  Updating from GRUB legacy is a bit more involved.  Either update-grub or update-grub2 will update the grub.cfg file using the preferred "non-manual" processes.

There are more than "warnings" with regard to grub.cfg.  It's a read-only file by default.  Of course, if someone is bent on changing it, they can use chmod +w as root.  But I'd recommend strongly against that.


Lucid uses 1.98, as I recall last time I looked.  And yes, I am aware that GRUB never got to "1".

---

