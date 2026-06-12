---
title: "LibreOffice Writer 3.5 ?"
date: 2012-03-27
forum: General Help
---

### Post by writebunny on 2012-03-27
There's a new feature in LibreOffice Writer version 3.5, from what I've read, that allows a LIVE word count to appear on the screen at all times. I've been searching high and low for a word processor that would allow this. When I check repositories, only 3.4.4 is available to Ubuntu/Xubuntu. 

So, I went to Libre's web site and found this: 
[http://www.libre-software.net/how-to-install-libreoffice-on-ubuntu-linux-mint](http://www.libre-software.net/how-to-install-libreoffice-on-ubuntu-linux-mint)

Although I followed all the directions, terminal kept finding fault and I gave up. 

Is there some reason that 3.5 isn't in the repositories for easier installation? I really REALLY need live word count, desperately. (I don't need the whole suite - just the word processor part.)

---

### Post by uRock on 2012-03-27
It will be in the repository for ubuntu 12.04. Generally, the repos do not get newer versions of software unless there is a security issue.

What is the error the terminal is giving you?

---

### Post by vasa1 on 2012-03-27
> **uRock said:**
> It will be in the repository for ubuntu 12.04. **Generally, the repos do not get newer versions of software unless there is a security issue.**

What is the error the terminal is giving you?

I'm on another PC now, but I think LibO (from the Software) is at 3.4.4. Apparently, there's been a [security fix in 3.4.6]("http://nabble.documentfoundation.org/Security-Advisories-td3850415.html").

---

### Post by uRock on 2012-03-27
> **vasa1 said:**
> I'm on another PC now, but I think LibO (from the Software) is at 3.4.4. Apparently, there's been a [security fix in 3.4.6]("http://nabble.documentfoundation.org/Security-Advisories-td3850415.html").

Then I am sure it will be coming in as an update in the near future. Please do not derail the thread.

---

### Post by writebunny on 2012-03-27
Thanks for helping. 

I'm sorry that I didn't keep the exact dialog. I should have. 

Part of the problem was that the instructions page noted to write the name of the program one certain way, but the download actually had extra letters after the version number. Although I updated the command to include those numbers, it only was partially successful. It found the package at first but on the second step it told me there was no such package, or something similar to that. I shouldn't have been so hasty, but I deleted everything figuring it was bad information. (Newbie lacking patience = a nightmare to help. I'm sorry about that.) 

When will Ubuntu 12.04 be released? (I've only been a Linux user for about a week)

If Ubuntu/Xubuntu 12.04 isn't coming in the next week or so, is there a way I can get Libre 3.5 to work? (Word count is my holy grail feature.)

---

### Post by uRock on 2012-03-27
**[SIZE="3"]Method A[/SIZE]**,
Since you already have the folder extracted, use the cd command to navigate to the package. Since the folder has a long name you can use the tab command to auto complete, so if it is in the **Downloads** folder, the type **cd ~/Downloads/Li** then hit the **tab** key to have it auto complete, but don't hit enter yet. After hitting the tab you will need to type **DEB** on the end, then hit enter, It should look like this in the end,```
cd ~/Downloads/LibO_3.5.2rc1_Linux_x86_install-deb_en-US/DEBS/
```
Next you need to tell the terminal to install LibreOffice with the following command,```
sudo dpkg -i *.deb
```

**[SIZE="3"]Method B[/SIZE]** for starting from scratch,

1. Copy and paste all of the commands for removing the packages listed in the link.

2. Download the Linux  package for your 32 or 64 bit system. Be sure to select the .deb, not the RPM file.

3. Navigate Nautilus(file viewer) to the DOwnloads folder, if that is where your downloads go, then right click the package and select to **extract here**.

4. That new folder with the long ugly name, rename it to something easy, like 123.

5. Use the cd command to navigate the terminal to the folder full of debs. Replace my 123 with whichever rename you used.
```
cd ~/Downloads/123/DEBS/
```Install the debs with the command listed on the linked page,```
sudo dpkg -i *.deb
```

If you get any errors, please copy and paste them here.

---

### Post by writebunny on 2012-03-28
Thanks for all the detailed steps. This makes it much easier to understand. 

I may not be able to write my results for 24-48 hours - but I will be back. This is an important piece of software for me. Thanks for helping!

---

### Post by ccrs8 on 2012-03-28
> **writebunny said:**
> When will Ubuntu 12.04 be released? (I've only been a Linux user for about a week)

Ubuntu 12.04 (and Xubuntu 12.04) will be released April 26th.  The first number in the release number is the year of the release, while the second number is the month of the release.  So 11.10 was released in October of 2011 and 12.04 will be released in April of 2012.  So you have more than a week or two to wait for live word count in the repos, but not that much longer.

---

### Post by LewisTM on 2012-03-28
If you want to have 3.5 appear in a repository, just add the LibreOffice PPA (Personal Package Archives).
Instructions [here]("http://www.webupd8.org/2012/02/install-to-libreoffice-350-in-ubuntu.html").
You'll get the most recent LO version and automatic updates.
And yes, 3.5 provides some useful improvements. Live word counting is a welcome addition.

Cheers!

---

### Post by GreatDanton on 2012-03-28
I also tried to install libre office. The software manager didn't find the package, so i downloaded it manually. 

When i extracted the downloaded folder i got this: 
LibO_3.5.1rc1_Linux_x86_install-deb_en-US (i renamed it to 123)

when i tried to install this, using their readme file (there is the same solution like you provide), the terminal did not install it because i got this:

jan@jan-laptop:~/Downloads/123$ sudo dpkg -i *
dpkg-split: error reading readmes: Is a directory
dpkg: error processing readmes (--install):
 subprocess dpkg-split returned error exit status 2
dpkg-split: error reading RPMS: Is a directory
dpkg: error processing RPMS (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 readmes
 RPMS


What to do now. (I dont have a folder DEB inside 123)
this does not work for me: sudo dpkg -i *.deb
(no such file or directory)

Iam using linux xubuntu
Any solutions?

---

### Post by uRock on 2012-03-28
> **GreatDanton said:**
> I also tried to install libre office. The software manager didn't find the package, so i downloaded it manually. 

When i extracted the downloaded folder i got this: 
LibO_3.5.1rc1_Linux_x86_install-deb_en-US (i renamed it to 123)

when i tried to install this, using their readme file (there is the same solution like you provide), the terminal did not install it because i got this:

jan@jan-laptop:~/Downloads/123$ sudo dpkg -i *
dpkg-split: error reading readmes: Is a directory
dpkg: error processing readmes (--install):
 subprocess dpkg-split returned error exit status 2
dpkg-split: error reading RPMS: Is a directory
dpkg: error processing RPMS (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 readmes
 RPMS


What to do now. (I dont have a folder DEB inside 123)
this does not work for me: sudo dpkg -i *.deb
(no such file or directory)

Iam using linux xubuntu
Any solutions?
What is listed when you open the "123" folder?

---

### Post by kurt18947 on 2012-03-28
I'm no expert on this -- I have installed LibreOffice manually in the past with no issues.  I'm confused by this:
[INDENT]dpkg-split: error reading RPMS: Is a directory
dpkg: error processing RPMS (--install):
 subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
 readmes
 RPMS
[/INDENT]RPMs?  In Ubuntu?  I thought RPMs were the equivalent of .debs in Fedora and other distros but won't work with Ubuntu without processing with alien.  If I'm mistaken please excuse my intrusion.

---

### Post by GreatDanton on 2012-03-28
> **uRock said:**
> What is listed when you open the "123" folder?

when i open 123 folder i have two folders:
-readmes
-RPMS

---

### Post by uRock on 2012-03-28
> **GreatDanton said:**
> when i open 123 folder i have two folders:
-readmes
-RPMS

You have downloaded the wrong packages. Do you have 32 or 64bit system?

I see in your post that you typed x86, which makes me think you are running 32bit. Here is the link to the 32bit DEBs, [http://download.documentfoundation.org/libreoffice/testing/3.5.2/deb/x86/LibO_3.5.2rc1_Linux_x86_install-deb_en-US.tar.gz](http://download.documentfoundation.org/libreoffice/testing/3.5.2/deb/x86/LibO_3.5.2rc1_Linux_x86_install-deb_en-US.tar.gz)

I have downloaded this twice and both times it had the DEBs folder.

---

### Post by timgood on 2012-03-29
Use the ppa because then you will get automatic updates without having to go through the whole install procedure every time LO is updated. Having said that, there are a number of reversion bugs in the new version of LO, but as far as I am aware the wordprocessing features work OK.

Hope this helps.

---

### Post by GreatDanton on 2012-03-29
Urocks your right. I have 32-bit system.

Iam wondering why there is no libre office installation in software manager.

---

### Post by writebunny on 2012-03-29
I appreciate all the help on this. Presently I'm fighting something that's wrong with my xubuntu installation, so I have to wait to dabble with installing libre again. 

Some security update in xubuntu seems to have thrown a whammy on my computer's behavior and I can't get things straightened out. (I'm too much a newbie to understand how to do anything yet - so frustrating). If anyone feels able to help, I have a topic started on this here: 

[http://ubuntuforums.org/showthread.php?p=11803565#post11803565](http://ubuntuforums.org/showthread.php?p=11803565#post11803565)

---

### Post by timgood on 2012-03-29
Try this in a terminal (you will need to input your password:


sudo add-apt-repository ppa:libreoffice/ppa

sudo apt-get update && sudo apt-get install libreoffice


This will get you the latest version of LibreOffice, and will keep you updated when updates become available.

---

### Post by writebunny on 2012-03-30
Thanks for the help everyone. 

My other computer problem resolved, so I could tackle Libre again. Because of your help, I was able to install via Terminal the easy way. It did install. It does open. Having said that, it is just a tad buggy and maybe not doing exactly what I'd hoped for re: displaying the word count. When I go into preferences etc, I can only read half lines of text (like the upper half of a sentence, or the lower half). I guess that's the price for running it pre-Xubuntu-version-12. 

When I click for the word count, it does appear in a floating box, which will stay up on the screen as I type. It's a bit clunky and in the way, however. Plus, it disappears when I go to fullscreen mode. 

Ah well. It was worth a try. Maybe when the new Ubuntu comes out, it will be more fun to use. 

To solve my word count need, I've finally figured out how to properly use Focuswriter. While the count isn't constantly live on screen, moving the mouse to the bottom of the page activates it. That will be good enough for now. (Sure wish I could find a way to make it stay permanently on display - maybe I can find the author?)

Thanks again all for helping me. I sure am learning a lot about Linux this week!

---

### Post by timgood on 2012-03-30
I am glad you got it sorted. You can mark this thread solved, so other people will know you found a solution.

I'm finding LO 3.5 very buggy as well, and I have reverted to using OpenOffice because, for all its faults and lack of development, it is stable and usable. I don't think that the inclusion of LibreOffice as the default office suite in Ubuntu does it any favours, and certainly does not allow for Ubuntu to be used as an out-of-box replacement for Windows or Microsoft Office.

There is a thread on this that you may find interesting here: [http://ubuntuforums.org/showthread.php?t=1946643](http://ubuntuforums.org/showthread.php?t=1946643)

Hope this helps.

---

