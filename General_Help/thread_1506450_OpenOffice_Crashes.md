---
title: "OpenOffice Crashes"
date: 2010-06-10
forum: General Help
---

### Post by 3-Ball on 2010-06-10
Just installed 64-bit Ubuntu Lynx. Rebooted per directions. Checked for updates. Installed them all (151 of them).

Launched OO Writer. While checking out features, I clicked TOOLS > BIBLIOGRAPHICAL DATABASE.
Wham! OO went down like it was shot through the head. I got an error message:

"Due to an unexpected error, OpenOffice.org crashed. All the files you were working on will now be saved. The next time OpenOffice.org is launched, your files will be recovered automatically.

"The following files will be recovered: Untitled1"


OO does this repeatedly, every time I click TOOLS >BIBLIOGRAPHICAL DATABASE.

Am I doing something wrong?

Let me know, please!

Thanks for any help.

3-Ball

---

### Post by Hagar Delest on 2010-06-10
First make sure that Base is installed (it is not by default with Ubuntu).
Then check that in OOo menu Tools>Options>OOo>Java there is a version checked (wait a while so that it scans the system).
If no change, try to [reset your OOo user profile](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58403#p58403) but don't transfer your personal data during the welcome process (if you had 2.x before), configuration files from the former version might corrupt the new profile.

If still no luck, try the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by 3-Ball on 2010-06-11
I fixed it myself. What I finally did was to uninstall all OO components individually, power-down, power-up, and reinstall OO as a suite. The problem disappeared.

I don't know if my install CD is flawed or if the image I burned was flawed or what, but OO now works perfectly as far as I know at this time. :popcorn:

---

### Post by Hagar Delest on 2010-06-11
Base is not installed by default with Ubuntu, that's certainly why it couldn't work.

---

### Post by zob on 2010-07-09
I reported it as a bug here some time ago: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/588306](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/588306)

No one seemed to look into it though.
I consider it a bug because openoffice WILL crash when using a certain function on a default ubuntu installation. So either that function should be deleted from the default openoffice in ubuntu or the package needed should be installed be default. Anything else makes ubuntu look kind of bad, don't you think?

---

### Post by jtpoole99 on 2010-07-26
My openoffice.org 3.2 (build 9483) crashes after the program has been idle for a bit and I return to it to start typing.  For instance, if i open a writer file and then go away to the kitchen for a snack and then return 10 or 15 minutes later and then switch back to OOO, it crashes when I press a key, mainly the ENTER key.  I don't know what's causing this error. but it always crashes with the following error:

[INDENT][I][B]Due to an unexpected error, OpenOffice.org crashed. All the files you  were working on will now be saved. The next time OpenOffice.org is  launched, your files will be recovered automatically.
[/B][/I][/INDENT]
Is anyone else experiencing this type of error with OpenOffice.org, if so, could you please respond and tell me how you fixed it?  I need to fix this issue as soon as possible.  Thanks in advance for any help...:(

---

### Post by avocadopicker on 2010-08-29
I'm having the same problem..... after a period of inactivity I return to either swriter or scalc and ooo crashes with the message as below.  Doesn't autorestart and sometimes leaves soffice.bin running (so it won't restart even manually).  Have Lucid 10.04 with all maintenance, and ooo 3.2.0.10 ooo320m12 build:9483 on eee pc netbook.  Does anyone have any ideas - this is driving me nuts!

---

### Post by egons on 2010-09-13
Try resseting your OpenOffice profile, this helped me.
[http://user.services.openoffice.org/en/forum/viewtopic.php?p=58401#p58401](http://user.services.openoffice.org/en/forum/viewtopic.php?p=58401#p58401)

---

### Post by ahmedc on 2010-11-07
Confirmation: Tools->Bibliography crash due to OpenOffice Base not being installed by default in Ubuntu.

---

### Post by Chris B on 2010-11-09
> **avocadopicker said:**
> I'm having the same problem..... after a period of inactivity I return to either swriter or scalc and ooo crashes with the message as below...

I came across this thread while googling the error message text.  I too have the same problem: leave swriter or scalc idle and when you try to work with it again it crashes.  Yesterday was the last straw, as it crashed a spreadsheet and was unable to recover my work--I had to start all over again.  I have been resisting using CrossOver + MS Office suite, but on my machine they are rock stable compared to OpenOffice.  

This is a fresh install of Ooo under a fresh install of 10.04, started completely from scratch (no transfer of existing profile or similar).  Any solutions/advice would be great, I'm about ready to bail on this software.

---

### Post by Hagar Delest on 2010-11-09
Try the vanilla version instead of the Ubuntu version (see posts above).

---

### Post by Chris B on 2010-11-09
Thanks for the advice--I hadn't noticed your link to the openoffice forums site in my first read through the thread.  For now I've uninstalled and reinstalled Ooo (the Ubuntu version) and haven't had a crash yet; I was having one every time I stepped away from my machine for several days now.  So far so good; my next step will be the Sun .deb if I run into trouble.

---

### Post by mad_jack on 2011-04-04
> **jtpoole99 said:**
> My openoffice.org 3.2 (build 9483) crashes after the program has been idle for a bit and I return to it to start typing.  For instance, if i open a writer file and then go away to the kitchen for a snack and then return 10 or 15 minutes later and then switch back to OOO, it crashes when I press a key, mainly the ENTER key.  I don't know what's causing this error. but it always crashes with the following error:

[INDENT][I][B]Due to an unexpected error, OpenOffice.org crashed. All the files you  were working on will now be saved. The next time OpenOffice.org is  launched, your files will be recovered automatically.
[/B][/I][/INDENT]
Is anyone else experiencing this type of error with OpenOffice.org, if so, could you please respond and tell me how you fixed it?  I need to fix this issue as soon as possible.  Thanks in advance for any help...:(

*Exactly* the same symptoms here, Mint 10.10, Tried removing OOO and installing Libreoffice instead, same thing happens though.

---

### Post by scouser73 on 2011-04-04
Hi mad_jack, I think that you need to delete your OpenOffice profile by opening your home folder pressing CRTL & H which will reveal hidden files and then look for the file named **.openoffice** and place the cursor over it, right click and send it to the waste basket.

To install LibreOffice I would recommend the Libreoffice PPA [https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)

Remembering to having removed the previous **.libreoffice** profile from the home folder.

---

### Post by Hagar Delest on 2011-04-04
Have you tried to reset your profile as stated at the beginning of the topic? For most of the OOo problems, it often works.

---

