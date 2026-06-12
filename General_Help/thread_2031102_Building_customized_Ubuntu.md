---
title: "Building customized Ubuntu"
date: 2012-07-21
forum: General Help
---

### Post by uzumakifahim on 2012-07-21
Hi,
I am using Ubuntu 12.04 and trying to build a customized Ubuntu, with  some changes with softwares and languages. To do this, I am using Ubuntu  Customization Kit (UCK). 

At first, I am choosing "English (en)" language pack to install.

After that, I am choosing "English (en)" language to be available at boot of live CD.

At this point I am choosing "en" from the "Select items from the list" window.

Now it lets me choosing the desktop environment for my customized CD. From KDE, Gnome and Others, I choose only "Gnome".

Here it asked me to choose the ISO find which I want to customize and I  have selected the ISO file of Ubuntu 12.04 and give a new name for my CD  and click OK.

Then it asked "Do you want to customize the CD manually during building?". I have selected "Yes".

Now it prompts "Do you want to delete all windows-related files from CD?" I have selected "Yes".

At this point it asked "Do you want to generate a hybrid image?" and I selected "Yes".

Now it said to enter my password and starting to build the new  customized CD. I have entered the password and it has started the build.

After some time it opens a window with "build failure message" and asked  me to check build.log file to check the problem. When I have checked  the file I have found the line that 

"cp: `/etc/resolv.conf' and `/home/fahim/tmp/remaster-root/etc/resolv.conf' are the same file"

I don't know why this problem is occurring again and again. Please help  me anyone. How can I solve this?  I'm in real problem. Thanks in  advance.

---

### Post by Kopkins on 2012-07-21
> **uzumakifahim said:**
> 
"cp: `/etc/resolv.conf' and `/home/fahim/tmp/remaster-root/etc/resolv.conf' are the same file"



I have tried UCK several times in the last month and still can't get it to work correctly. You should be able to move past this error by editing the build script. 
```
sudo gedit /usr/lib/uck/remaster-live-cd.sh
```Search for:
```
cp -f /etc/resolv.conf
```And change the -f to -d.

Or do it automatically: 
```
sudo sed -i "s/cp -f \/etc\/resolv.conf/cp -d \/etc\/resolv.conf/" /usr/lib/uck/remaster-live-cd.sh
```I bet you'll still run into errors before you finish the build. There was a bug that inhibited editing using a graphical package manager that was marked as 'Won't Fix'. Instead they decided not to include that option in the next version. I'm not sure if that version is out, and if it is, I'm not sure it has made it this far downstream.

Good luck.
Kopkins

---

### Post by uzumakifahim on 2012-07-22
Thanks Kopkins for your reply. But in the meantime I have found another tool to do the same task. That is "Ubuntu builder", it seems much better than UCK to me. Though I have not succeeded fully to customize any Ubuntu distribution yet, but I hope I can do that soon. Have you done any successful customization with Ubuntu distributions by UCK or any other tools? I think if you please share your knowledge in this thread, that would be great and helpful for everyone.

---

### Post by brian_mk on 2012-07-25
I used uck a couple of weeks ago. In my case I was using Ubuntu 10.04
I found the uck package in 10.04 to be buggy and ended up downloading the latest from sourceforge. This worked ok for me.

It may be that uck for 12.04 is also buggy.
Have you tried installing the latest from sourceforge?

---

### Post by uzumakifahim on 2012-07-25
@[brian_mk]("http://ubuntuforums.org/member.php?u=591201"), I haven't tried in that way yet. Your idea is good. I'll try to get the latest release from Sourceforge. But, I have a question for you, have you get success to change the default dektop environment for Ubuntu? Actually I want cinnamon as default desktop. Is that possible with UCK?  Please share your experience.

---

### Post by Liveman on 2012-07-28
Have you had any trouble with this:

Mounting ISO image...
mount: warning: /home/username/tmp/remaster-iso-mount seems to be mounted read-only.

Can I chane permission for that?

---

### Post by uzumakifahim on 2012-07-28
I don't understand your problem clearly. If you are facing any problem with remastersys. Please start a new thread, hope that will help you to solve your problem easily. Whatever, I use remastersys recently. It works fine for me. But when I am testing my customized ISO on a usb drive time & date is not showing. It is showing "TIme", just instead of date & time. Could anyone help me regarding this?

Thanks.

---

### Post by nadarockyraccoon on 2012-07-29
ubuntu 12.04 uses the indicator-datetime which doesn't display the date with the time. You can add a clock applet but you will have to uninstall indicator-datetime else you'll have two clocks. 

that being said i'm also having an issue with:

Mounting ISO image...
mount: warning: /home/username/tmp/remaster-iso-mount seems to be mounted read-only.

and changing the permissions didn't help as each time you start a build those folders are deleted and recreated as root. Not sure what the issue is, bug report claimed it was fixed, but never really stated how. After some reading I've come to uck isn't stable enough to be reliable and I've had great luck with remastersys. I just wanted to find a way to not have remastersys and it's dependencies installed on the live cd and/or the install. Any clues there would be great

---

### Post by uzumakifahim on 2012-07-30
@ [nadarockyraccoon]("http://ubuntuforums.org/member.php?u=250784"), I have found a solution for this time & date issue with remastersys. Please do the following to solve :

As root open remastersys script from [COLOR=#008080] /usr/bin/remastersys [COLOR=Black]with gedit. Find the keyword timezone using find tool of gedit.

The code will be like this :

[/COLOR][/COLOR] ```
rm -f $WORKDIR/dummysys/etc/{resolv.conf,hosts,hostname,timezone,mtab*,fstab}

```
Now remove timezone from the line above. Then the line will be like :

```
rm -f $WORKDIR/dummysys/etc/{resolv.conf,hosts,hostname,mtab*,fstab}
```

Now save the script and create your new customized Ubuntu. Hope your problem will be solve this time.

---

