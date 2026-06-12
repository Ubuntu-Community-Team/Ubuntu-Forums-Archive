---
title: "Can't activate LanguageTool in Open Office"
date: 2010-10-17
forum: General Help
---

### Post by jadu on 2010-10-17
hello,

I have Ubuntu 10.4.
I can't activate the Language Tool grammar checker for Open Office. 
I added the extension to Open Office in Tools-Extension Manager. But the grammar check still doesn't seem to be working.
I have "check grammar" checked in the spelling-grammar options. 
I also already installed the openoffice.org-java-common package, as I saw on this page:
[http://nancib.wordpress.com/2008/05/03/fixing-the-openofficeorg-grammar-glitch-in-ubuntu-hardy/](http://nancib.wordpress.com/2008/05/03/fixing-the-openofficeorg-grammar-glitch-in-ubuntu-hardy/)

I also tried the advise on this post:
[http://ubuntuforums.org/showthread.php?t=797761&highlight=languagetool](http://ubuntuforums.org/showthread.php?t=797761&highlight=languagetool)
> 
I found this helped with other OOo extensions. The current Ubuntu (8.04) ships with a stripped down install of OOo. First, remove the extension your talking about in the extensions manager. Shut down OOo. Then, to get the full install just go to synaptic and install the package called openoffice.org (it will say in the description that it is a meta package). Ignore all the other packages that show up when you search. When you install it, you'll see it's adding a bunch of other files to the OpenOffice install. Restart and reinstall the extension and see if it works.

But that didn't work either.
I think it might be that I can't activate the extension. When I look at Open Office Help, it says I need to activate it. But there's no activate button on the extension when I go to the extension list. Though the other extension I have does have a deactivate button.

I'm not at all an advanced user, I might be missing something obvious here.
Any ideas?
thanks

---

### Post by jadu on 2010-10-21
I'd like to bump this, to see if anyone has an idea on it.

---

### Post by Mukoi on 2010-10-21
Hi,

I also had a problem with the Language Tool, but was able to solve my problem.  Refer:[ http://ubuntuforums.org/showthread.php?t=1589209]("http://ubuntuforums.org/showthread.php?t=1589209") .

Don't know if this will help you.

You have probably heard that OpenOffice.org suite is being developed  further by The Document Foundation with a Beta2 release available  (LibreOffice) - [http://www.documentfoundation.org](http://www.documentfoundation.org) .

Ubuntu has given its  support.

Am looking forward to an even better product.

---

### Post by jadu on 2010-10-21
thanks, I had seen your post, and so I had already installed openoffice.org-java-common. I think my problem is a different one.
I had heard about the LibreOffice project, but hadn't seen the web site, it looks good, thanks for pointing that out.

---

### Post by Hagar Delest on 2010-10-22
Try the vanilla version, it seems to work fine: [Spell checker and capitalized words](http://user.services.openoffice.org/en/forum/viewtopic.php?f=7&t=34883).

See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by jadu on 2010-10-25
hello, thank you for your reply, sorry about my delay in answering.

I had forgot to specify, I have Open Office 3.2.0.

I'm afraid I don't know what the vanilla version is-- does that mean the newest version of open office?

I realized more in detail what my problem is-- I seem to have installed the extension, but it doesn't appear in the tools menu. Of course I tried exiting open office and restarting it.

I see on the language tools forum that others have had this problem, but I didn't see a clear answer.

I tried the solution listed for "issue 3" here:
[http://extensions.services.openoffice.org/en/project/languagetool#comment-2009](http://extensions.services.openoffice.org/en/project/languagetool#comment-2009)

But it just created another file by the same name when I reopened OOo. 

The only other clear suggestion I saw was here:
[http://extensions.services.openoffice.org/en/project/languagetool#comment-1461](http://extensions.services.openoffice.org/en/project/languagetool#comment-1461)

But the first two don't seem relevant. The third one: I followed the instructions and did not find the indicated open office file in the uno_packages folder. But I don't know which uno_packages folder I should therefore delete: user/lib/openoffice/share/uno_packages? Or user/lib/openoffice/share/uno_packages/cache/uno_packages?

Or do you suggest that I try to upgrade Open Office using the instructions on your second link? It seems quite complicated and with more chance of messing something up, so I was hoping to find an alternative...

If noone here has any ideas maybe I'll try to Language tool page on the open office extensions site.

thank you!

---

### Post by Hagar Delest on 2010-10-25
Yes, try to upgrade to the Sun version. Nothing really complicated, don't worry. It's just a little different from the graphical interface.

---

### Post by jadu on 2010-10-25
hey thanks.
I'm trying that. Not understanding much of what I'm doing, but I think I'm following the steps as indicated.
I also looked at the wiki page with about the same tutorial.

I did the first few steps.
I'm hung up on this step: 
cd desktop-integration

It tells me: No such file or directory

I did a search in "file system" and it didn't find it.

Any idea?
thanks

---

### Post by Hagar Delest on 2010-10-26
Have you extracted the debs and installed them with dpkg?

---

### Post by jadu on 2010-10-26
I believe I did. But I just tried it again, to look more carefully at the output message. It turns out there was an error:

(Reading database ... 165118 files and directories currently installed.)
Preparing to replace ooobasis3.2-sdk 3.2.1-18 (using ooobasis3.2-sdk_3.2.1-18_i386.deb) ...
Unpacking replacement ooobasis3.2-sdk ...
dpkg: dependency problems prevent configuration of ooobasis3.2-sdk:
 ooobasis3.2-sdk depends on ooobasis3.2-core01; however:
  Package ooobasis3.2-core01 is not installed.
dpkg: error processing ooobasis3.2-sdk (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ooobasis3.2-sdk

I did try to be sure that all packages with open office in the name, and with "ubuntu" in the installed version, were removed. I also deleted the folders that were left in my home folder.

When I open Synaptic now, it tells me that I have two broken packages: ooobasis3.2-sdk and w32codecs. I would guess that maybe I just should completely remove these 2 packages? Could you confirm that for me, I don't want to remove them if they're important-- the codecs one gives me the option of upgrading, though the ooobasis only gives me the option of removing.

thanks!!!

---

### Post by Hagar Delest on 2010-10-27
I'm rather surprised by the 'sdk' string in the name. Are yo usure you haven't downloaded the Software Development Kit?

Check you've downloaded from [this page]("http://download.openoffice.org/other.html#tested-full").

---

### Post by jadu on 2010-10-28
Hello, 

I realized what my mistake was and I believe I fixed one step; still not working, though. 
The instructions said to download the tarball. So I had gone to the part of that page that says tarball, and I downloaded:
OOo-SDK_3.2.1_Linux_x86_install-deb_en-US

But now I tried again. I removed the ooobasis file that was listed as "damaged" in my synaptic manager. I deleted the folder that I had downloaded and extracted before. And I downloaded:
OOO320_m18_native_packed-1_en-US.9502

I got the following ouput:

> ~/OOO320_m18_native_packed-1_en-US.9502/DEBS$ sudo dpkg -i *.deb


Selecting previously deselected package ooobasis3.2-en-us.
(Reading database ... 150247 files and directories currently installed.)
Unpacking ooobasis3.2-en-us (from ooobasis3.2-en-us_3.2.1-18_i386.deb) ...
Selecting previously deselected package ooobasis3.2-en-us-base.
Unpacking ooobasis3.2-en-us-base (from ooobasis3.2-en-us-base_3.2.1-18_i386.deb) ...
Selecting previously deselected package ooobasis3.2-en-us-binfilter.
Unpacking ooobasis3.2-en-us-binfilter (from ooobasis3.2-en-us-binfilter_3.2.1-18_i386.deb) ...
Selecting previously deselected package ooobasis3.2-en-us-calc.
Unpacking ooobasis3.2-en-us-calc (from ooobasis3.2-en-us-calc_3.2.1-18_i386.deb) ...
Selecting previously deselected package ooobasis3.2-en-us-draw.
Unpacking ooobasis3.2-en-us-draw (from ooobasis3.2-en-us-draw_3.2.1-18_i386.deb) ...
Selecting previously deselected package ooobasis3.2-en-us-help.
Unpacking ooobasis3.2-en-us-help (from ooobasis3.2-en-us-help_3.2.1-18_i386.deb) ...
Selecting previously deselected package ooobasis3.2-en-us-impress.
Unpacking ooobasis3.2-en-us-impress (from ooobasis3.2-en-us-impress_3.2.1-18_i386.deb) ...
Selecting previously deselected package ooobasis3.2-en-us-math.
Unpacking ooobasis3.2-en-us-math (from ooobasis3.2-en-us-math_3.2.1-18_i386.deb) ...
Selecting previously deselected package ooobasis3.2-en-us-res.
Unpacking ooobasis3.2-en-us-res (from ooobasis3.2-en-us-res_3.2.1-18_i386.deb) ...
Selecting previously deselected package ooobasis3.2-en-us-writer.
Unpacking ooobasis3.2-en-us-writer (from ooobasis3.2-en-us-writer_3.2.1-18_i386.deb) ...
Selecting previously deselected package openoffice.org3-dict-en.
Unpacking openoffice.org3-dict-en (from openoffice.org3-dict-en_3.2.1-18_i386.deb) ...
Selecting previously deselected package openoffice.org3-en-us.
Unpacking openoffice.org3-en-us (from openoffice.org3-en-us_3.2.1-18_i386.deb) ...
dpkg: dependency problems prevent configuration of ooobasis3.2-en-us:
 ooobasis3.2-en-us depends on ooobasis3.2-core01; however:
  Package ooobasis3.2-core01 is not installed.
dpkg: error processing ooobasis3.2-en-us (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ooobasis3.2-en-us-base:
 ooobasis3.2-en-us-base depends on ooobasis3.2-en-us; however:
  Package ooobasis3.2-en-us is not configured yet.
dpkg: error processing ooobasis3.2-en-us-base (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ooobasis3.2-en-us-binfilter:
 ooobasis3.2-en-us-binfilter depends on ooobasis3.2-en-us; however:
  Package ooobasis3.2-en-us is not configured yet.
dpkg: error processing ooobasis3.2-en-us-binfilter (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ooobasis3.2-en-us-calc:
 ooobasis3.2-en-us-calc depends on ooobasis3.2-en-us; however:
  Package ooobasis3.2-en-us is not configured yet.
dpkg: error processing ooobasis3.2-en-us-calc (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ooobasis3.2-en-us-draw:
 ooobasis3.2-en-us-draw depends on ooobasis3.2-en-us; however:
  Package ooobasis3.2-en-us is not configured yet.
dpkg: error processing ooobasis3.2-en-us-draw (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ooobasis3.2-en-us-help:
 ooobasis3.2-en-us-help depends on ooobasis3.2-en-us; however:
  Package ooobasis3.2-en-us is not configured yet.
dpkg: error processing ooobasis3.2-en-us-help (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ooobasis3.2-en-us-impress:
 ooobasis3.2-en-us-impress depends on ooobasis3.2-en-us; however:
  Package ooobasis3.2-en-us is not configured yet.
dpkg: error processing ooobasis3.2-en-us-impress (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ooobasis3.2-en-us-math:
 ooobasis3.2-en-us-math depends on ooobasis3.2-en-us; however:
  Package ooobasis3.2-en-us is not configured yet.
dpkg: error processing ooobasis3.2-en-us-math (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ooobasis3.2-en-us-res:
 ooobasis3.2-en-us-res depends on ooobasis3.2-en-us; however:
  Package ooobasis3.2-en-us is not configured yet.
dpkg: error processing ooobasis3.2-en-us-res (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ooobasis3.2-en-us-writer:
 ooobasis3.2-en-us-writer depends on ooobasis3.2-en-us; however:
  Package ooobasis3.2-en-us is not configured yet.
dpkg: error processing ooobasis3.2-en-us-writer (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org3-dict-en:
 openoffice.org3-dict-en depends on openoffice.org-ure; however:
  Package openoffice.org-ure is not installed.
 openoffice.org3-dict-en depends on ooobasis3.2-core01; however:
  Package ooobasis3.2-core01 is not installed.
 openoffice.org3-dict-en depends on ooobasis3.2-core02; however:
  Package ooobasis3.2-core02 is not installed.
 openoffice.org3-dict-en depends on ooobasis3.2-core03; however:
  Package ooobasis3.2-core03 is not installed.
 openoffice.org3-dict-en depends on ooobasis3.2-core04; however:
  Package ooobasis3.2-core04 is not installed.
 openoffice.org3-dict-en depends on ooobasis3.2-core05; however:
  Package ooobasis3.2-core05 is not installed.
 openoffice.org3-dict-en depends on ooobasis3.2-core06; however:
  Package ooobasis3.2-core06 is not installed.
 openoffice.org3-dict-en depends on ooobasis3.2-core07; however:
  Package ooobasis3.2-core07 is not installed.
 openoffice.org3-dict-en depends on openoffice.org3; however:
  Package openoffice.org3 is not installed.
dpkg: error processing openoffice.org3-dict-en (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openoffice.org3-en-us:
 openoffice.org3-en-us depends on openoffice.org3; however:
  Package openoffice.org3 is not installed.
 openoffice.org3-en-us depends on ooobasis3.2-en-us; however:
  Package ooobasis3.2-en-us is not configured yet.
 openoffice.org3-en-us depends on ooobasis3.2-en-us-base; however:
  Package ooobasis3.2-en-us-base is not configured yet.
 openoffice.org3-en-us depends on ooobasis3.2-en-us-calc; however:
  Package ooobasis3.2-en-us-calc is not configured yet.
 openoffice.org3-en-us depends on ooobasis3.2-en-us-draw; however:
  Package ooobasis3.2-en-us-draw is not configured yet.
 openoffice.org3-en-us depends on ooobasis3.2-en-us-help; however:
  Package ooobasis3.2-en-us-help is not configured yet.
 openoffice.org3-en-us depends on ooobasis3.2-en-us-impress; however:
  Package ooobasis3.2-en-us-impress is not configured yet.
 openoffice.org3-en-us depends on ooobasis3.2-en-us-math; however:
  Package ooobasis3.2-en-us-math is not configured yet.
 openoffice.org3-en-us depends on ooobasis3.2-en-us-res; however:
  Package ooobasis3.2-en-us-res is not configured yet.
 openoffice.org3-en-us depends on ooobasis3.2-en-us-writer; however:
  Package ooobasis3.2-en-us-writer is not configured yet.
dpkg: error processing openoffice.org3-en-us (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ooobasis3.2-en-us
 ooobasis3.2-en-us-base
 ooobasis3.2-en-us-binfilter
 ooobasis3.2-en-us-calc
 ooobasis3.2-en-us-draw
 ooobasis3.2-en-us-help
 ooobasis3.2-en-us-impress
 ooobasis3.2-en-us-math
 ooobasis3.2-en-us-res
 ooobasis3.2-en-us-writer
 openoffice.org3-dict-en
 openoffice.org3-en-us


For the next step, I got the following output:
> XXXXXXX-laptop:~/OOO320_m18_native_packed-1_en-US.9502/DEBS$ cd desktop-integration
bash: cd: desktop-integration: No such file or directory


Now when I go to synaptic package manager, it tells me that I have 3 broken packages: ooobasis3.2-en-us, openoffice.org3-dict-en, and openoffice.org3-en-us

Any idea on what I'm doing wrong?

thank you!!

---

### Post by Hagar Delest on 2010-10-28
As said, no need to download the SDK version!

In Synaptic, removed all the OOo packages, download the correct tarball (for example the 3.3 RC, it is "OOo_3.3.0rc2_20101021_Linux_x86_install-deb_en-US.tar.gz", no SDK!) and install.

---

### Post by jadu on 2010-10-28
thanks much, my last try did it. I had again downloaded the incorrect file.
I'll have to reinstall a couple of languages, but will look on other posts for how to do that, I'd imagine it's not hard.
But with the grammar checker, I'm back where I started-- I can add the language tool to the list of extensions, but it doesn't show up in the tools menu. And the "activate" button in the extensions list for language tool is not visible to click on, just the "remove" button. Any other ideas?

---

### Post by Hagar Delest on 2010-10-29
See that one perhaps: [[Solved] 3.2.1 (Oracle) on Ubuntu - Language Tools Questions](http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=31579).

---

### Post by jadu on 2010-11-02
I wanted to let you know how this ended. The newly installed version of Open Office still didn't let me effectively install Language Tool, and the top tool bar was a simpler, uglier version than what I had had in the Ubuntu version. In the most recently posted link, I didn't see anything that would help me fix Language tool. Since except for Language tool the Ubuntu version had worked fine for me, I decided to just reinstall the Ubuntu Open Office. I'll just use my Windows partition to do grammar check. Still, thank you very much for all your efforts to help me.

---

