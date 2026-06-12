---
title: "Downloads not opening?!"
date: 2009-12-11
forum: General Help
---

### Post by Toshiba1972 on 2009-12-11
Hi there...I am new to ubunto...but not new to firefox. I have downloaded a few apps and none of which are opening. The following it the message I get when i try to open a file that I download.

Archive:  /home/toshiba/Downloads/dap93_bros(2).exe
[/home/toshiba/Downloads/dap93_bros(2).exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/toshiba/Downloads/dap93_bros(2).exe or
          /home/toshiba/Downloads/dap93_bros(2).exe.zip, and cannot find /home/toshiba/Downloads/dap93_bros(2).exe.ZIP, period.


If anyone can provide me with a reason as to why I cannot open any files...that would be greatly appreciated.

Thank you

---

### Post by edwin_cheung88 on 2009-12-11
I thiunk thats an .exe, ubuntu works differently from a windows as in it usually doesn't run .exe-s

---

### Post by Physical Hook on 2009-12-11
Linux doesn't know what EXE means and how to work with it. Check Wine - might solve your problem.

---

### Post by Leppie on 2009-12-11
> **Toshiba1972 said:**
> Archive:  /home/toshiba/Downloads/dap93_bros(2).exe
[/home/toshiba/Downloads/dap93_bros(2).exe]

Why are you trying to open a windoze executable on a linux system? If there's only the windoze version, you might want to look into [Wine]("https://help.ubuntu.com/community/Wine") (windoze emulator).

---

### Post by Toshiba1972 on 2009-12-11
I have never used linux based OS before. I just assumed .exe wasn't a windows standard extension...but was for any OS. Thanks for the enlightenment. 

So with this in mind...is there any other extensions I should know about that are windows specific?

---

### Post by ScrewdriverClock on 2009-12-12
> **Leppie said:**
> I regret to inform you that running .exe executables is only possible in Windows natively, and in a few cases a Linux based alterative is obtainable. However If there's only the Windows executable, you might want to look into [Wine]("https://help.ubuntu.com/community/Wine") (Windows API).
Fixed both your smarmy attitude and you calling WINE an emulator. (Wine Is Not an Emulator)
> **Toshiba1972 said:**
> I have never used linux based OS before. I just assumed .exe wasn't a windows standard extension...but was for any OS. Thanks for the enlightenment. 

So with this in mind...is there any other extensions I should know about that are windows specific?
Hrm IIRC .dll is normally (though LMMS uses it for my audio plugins still) as is .ico which is replaced by .pngs and .svgs

---

### Post by lisati on 2009-12-12
> **Toshiba1972 said:**
> I have never used linux based OS before. I just assumed .exe wasn't a windows standard extension...but was for any OS. Thanks for the enlightenment. 

So with this in mind...is there any other extensions I should know about that are windows specific?

Other than ["Self-extracting archives"]("http://en.wikipedia.org/wiki/Self-extracting_archive"), I've only ever seen ".EXE" used with Windows and MS-DOS. As others have suggested, you can check out [Wine]("https://help.ubuntu.com/community/Wine").

If it's a self-extracting archive, you can either use Wine or treat it like a zip file. Going by the error message, however, this scenario seems unlikely.

---

### Post by Leppie on 2009-12-12
> **ScrewdriverClock said:**
> Fixed both your smarmy attitude...

so who is really being smarmy here?!

---

### Post by mkvnmtr on 2009-12-12
If you need apps look first in the package manager or Ubuntu Software center.They will have another name but will probably do the same thing you need. Downloading from the internet is seldom required.

---

### Post by Leppie on 2009-12-12
If you do want to download applications from the internet, look for .deb packages first as they can be installed using gdebi (just "open" the download once completed) or synaptic, which both allow for easy removal later on.

---

### Post by 73ckn797 on 2009-12-12
Google will also help you to find apps that are Window equivalents. 
Best source will be from System/Administration/Synaptic Package Manager or the Applications/Software Center .

What are you looking for in particular?

---

### Post by Ylon on 2009-12-12
Welcome to Ubuntu then!

Btw: I did notice that the "dap93_bros.exe" file stand for Download Accellerator software in windows. This can be a good time to pratice the way software for linux are delivered.

There are many way to do such things, mostly like is looking for a "*.deb*" file package. But a more comfort way to do this, is (firstly) to see if such kind of software is already disposable in Ubuntu's defaul repository. Before do that you need to "tune" your synaptic application (you can just star search from now... but if you do "tune" your Synaptic first it will be more easy to get your software (more fast, more software to browse)


Open Synapic:
*Menu "System" > Administrator > Synaptic Package Manager

Now about the tune:
then [settings](http://winff.org/images/screenshots/synaptic_setting_repo.png) > Repositories > enable everything except the sources (you need them only if you are a programmer and want to *engineering* over your preferred application).

Change:
Download From: [blablabla] to > Other.

Now click on "select the best server".. and Synaptic will perform a test to find the fastest repository near you (software will download more faster)

Confirm/Ok/Apply on everything.
Now click on Blue "reload" icon.

Finish.


now you can go in the search field of Synaptic and input what do you need ("download accelerator", "first person shooter", chrome...whatever do you need).

Enjoy.

---

