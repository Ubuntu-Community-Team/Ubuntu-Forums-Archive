---
title: "Plan program location?"
date: 2011-09-01
forum: General Help
---

### Post by Camilia on 2011-09-01
I downloaded plan program to have a calendar to write my schedule. I don't see it anywhere. Is there something else I need to do? I also downloaded xcal and can't find it either. 

Look via menu in every category.

---

### Post by mikewhatever on 2011-09-01
Usually, to use a program, you need to download and install it, and not just download. So, the question is, what exactly did you do. Did you use the Software Center (the right way), or did you go to a web site (as one would with Windows) and downloaded some files from there?

---

### Post by sauerpauer on 2011-09-01
How did you download the programs?  If you used a web browser, it will likely be in your home folder somewhere.

You can use the "find" command to find files, but it can be slow sometimes.  I'd recommend:
```
find /home -iname "xcalc*"
```
Or something similar.

---

### Post by Camilia on 2011-09-01
I tried find /home -iname "xcalc*" and nothing happened. 
I download via the synapse as I did thunderbird.

---

### Post by mikewhatever on 2011-09-01
'synapse'? Did you meam Synaptic Package Manager under System->Administration?

---

### Post by Camilia on 2011-09-02
[QUOTE=mikewhatever;11210597]'synapse'? Did you meam Synaptic Package Manager under System->Administration?[/QUOTE
Yes

---

### Post by oldos2er on 2011-09-02
> **Camilia said:**
> I tried find /home -iname "xcalc*" and nothing happened. 
I download via the synapse as I did thunderbird.

**xcalc** is a calculator.

What happens if you type **xcal** in a terminal?

---

### Post by Camilia on 2011-09-02
Typing xcal in the terminal brought a calendar. But it is a pain to go back and forth to type something in. Was hoping it would be a calendar that could paste info in.

Typed in plan and it came up but still have to go in and out. 

Exactly what program in the synaptic manager would give a calendar that I could type in without going in and out.

Thanks for the help!!

Deleted them and put in the calendar program vpim. Typed in the terminal and got nothing. Seems I could spend hours trying out different calendar programs.

---

### Post by oldos2er on 2011-09-02
Are you using 9.04? Its support ended some time ago.

I can't find a program in the repositories called vpim, so I can't really help you with that.

If you're using Evolution or Thunderbird, they both have calendar add-ons. Actually I think Evolution's calendar is built in. The Thunderbird add-on is called Lightning (there are other calendar add-ons too, but in my opinion Lightning is the best).

I don't really understand what you mean by "going in and out." 

Also take a look at [http://www.rainlendar.net/cms/index.php](http://www.rainlendar.net/cms/index.php)

---

### Post by coldraven on 2011-09-02
Using 10.10 if you click on the date at the top of the screen (near your user name) you get a small calender. If you double click on any day Evolution will (slowly) appear and you can add appointments etc. See the screenshot

---

### Post by Camilia on 2011-09-03
I have 10.0 program

vpim is under calendars in the synapse manager.

By going in and out I mean I click on the date and only that day is viewable. I need to view the whole calendar when making events on the day. 

Got Google calendar via ubuntu software. It works like I need but I hate that I have to log in to use. 

Evolution is a pain for me to set up. I have forgotten how to do it. 
Thunderbird lighting I can't find. Wish I could find it.

Found lighting is a library to aid in making portable programs that compile assembly code at run time.

---

### Post by oldos2er on 2011-09-03
In Thunderbird, click Tools, Add-ons, search for 'lightning'.

---

### Post by Camilia on 2011-09-04
> **oldos2er said:**
> In Thunderbird, click Tools, Add-ons, search for 'lightnint'.
It is not there. I click on browse for more Add-ons and find it. Can't figure out how to save it so that it will go into the Add-ons section. Got it saved in system files.

---

### Post by ofnuts on 2011-09-04
> **Camilia said:**
> It is not there. I click on browse for more Add-ons and find it. Can't figure out how to save it so that it will go into the Add-ons section. Got it saved in system files.

- with you web browser, download it from the Mozilla site to some folder on your disk 
- start Thunderbird, go to Tools/Add-ons
- press the "Install..." button at the bottom
- navigate to the folder where you saved the .XPI, and select it

Note: the "default/current" download of lightning if for TB v5. If you are running the version of Thunderbird installed with your Ubuntu, it is likely older and you'll have to use an earlier version of Lightning. Check there:

[https://addons.mozilla.org/en-US/thunderbird/addon/lightning/versions/](https://addons.mozilla.org/en-US/thunderbird/addon/lightning/versions/)

---

### Post by oldos2er on 2011-09-04
> **Camilia said:**
> It is not there. I click on browse for more Add-ons and find it. Can't figure out how to save it so that it will go into the Add-ons section. Got it saved in system files.

Fixed the typo in my previous post.

Which version of Thunderbird are you using?

---

### Post by Camilia on 2011-09-05
> **ofnuts said:**
> - with you web browser, download it from the Mozilla site to some folder on your disk 
- start Thunderbird, go to Tools/Add-ons
- press the "Install..." button at the bottom
- navigate to the folder where you saved the .XPI, and select it

Followed the instructions got message that lighting is not compatible with thunderbird 3.1.13 
.

---

### Post by ofnuts on 2011-09-05
> **Camilia said:**
> Followed the instructions got message that lighting is not compatible with thunderbird 3.1.13 
.See the Note in my post. If you have an old TB version, you need an old Lightning version, too.

---

### Post by Camilia on 2011-09-05
> **ofnuts said:**
> See the Note in my post. If you have an old TB version, you need an old Lightning version, too.
Well I update thus didn't know I had the old version. Would like to get the new one. Downloaded thunderbird 6.1 from web but don't know how to install it.

> **ofnuts said:**
>  If you are running the version of Thunderbird installed with your Ubuntu, it is likely older and you'll have to use an earlier version of Lightning. Check there:

[https://addons.mozilla.org/en-US/thunderbird/addon/lightning/versions/](https://addons.mozilla.org/en-US/thunderbird/addon/lightning/versions/)
Attempted to install it and got message Lightning 1.0b5 could not be installed because it is not compatible with Thunderbird 3.1.13

---

### Post by Camilia on 2011-09-05
bump

---

### Post by ofnuts on 2011-09-05
> **Camilia said:**
> Well I update thus didn't know I had the old version. Would like to get the new one. Downloaded thunderbird 6.1 from web but don't know how to install it.Don't mix problems. The TB version you have (from the Canonical repository for your Ubuntu release) is known to work with your specific Ubuntu.

> **Camilia said:**
> Attempted to install it and got message Lightning 1.0b5 could not be installed because it is not compatible with Thunderbird 3.1.13Yes, because if you read the page I gave you a link to you'll find you need Lightning 1.0B2 for your TB 3.1.*.

---

### Post by Camilia on 2011-09-05
> **ofnuts said:**
> Don't mix problems. The TB version you have (from the Canonical repository for your Ubuntu release) is known to work with your specific Ubuntu.

Yes, because if you read the page I gave you a link to you'll find you need Lightning 1.0B2 for your TB 3.1.*.
I went to the link, though. Followed instructions and got message Lightning 1.0b5 could not be installed because it is not compatible with Thunderbird 3.1.13

Downloaded Download 32-bit Lightning version 1.0b2. 
Result was:
Lightning" could not be installed because it is not compatible with your Firefox build type (Linux_x86-gcc3).

---

### Post by ofnuts on 2011-09-05
> **Camilia said:**
> I went to the link, though. Followed instructions and got message Lightning 1.0b5 could not be installed because it is not compatible with Thunderbird 3.1.13

Downloaded Download 32-bit Lightning version 1.0b2. 
Result was:
Lightning" could not be installed because it is not compatible with your Firefox build type (Linux_x86-gcc3).Worked for me... but I wonder why you get messages about Firefox when it is a Thunderbird extension? Also did you download a file called 'lightning-1.0b2-tb-linux.xpi'? I suspect that if you download it from Windows or OSX (or if your browser is spoofing its user-agent string), you get a Windows or OSX version... (yes, this add-on is opsys-dependent).

---

### Post by Camilia on 2011-09-05
Downloaded lightning.xpi from [here]("http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b2/contrib/linux-x86_64/")

---

### Post by parmstrong on 2011-09-22
Has anyone come up with a resolution for this?  I am having the exact same problem.

---

### Post by Camilia on 2011-09-23
I ended up using [calendar]("http://www.wincalendar.com/2011-Word-Calendar.htm") from outside source.

---

### Post by Azdour on 2011-09-23
Hi,

Sometimes I have found that the problem with downloading Thunderbird add-ons via Firefox is that Firefox offers to install it. It then tries to install it for Firefox which of course will fail and you will see a similar error message that your reported.

I have to right click on the link and do 'Save Link As...' to be able to save the file locally.

Then I open Thunderbird | Tools | Add-ons. Click on the Install button (bottom left). Then go browsing to where I saved the add-on.

---

### Post by parmstrong on 2011-09-23
That is exactly how I did it, downloaded the file then attempted to install from Thunderbird, with Firefox closed.  No luck.  Very frustrating.

---

### Post by Camilia on 2011-09-23
Got it to work today. 

Thanks everyone for your help.

---

### Post by parmstrong on 2011-09-26
What did you do to get it working ?

---

### Post by Camilia on 2011-09-27
> **parmstrong said:**
> What did you do to get it working ?

I embarrassed to say that I followed ofnuts previous instructions. That is looked for Lightning 1.0B2 for your TB 3.1. Saved it to disk. Clicked on install. Went to it location on disk and clicked on it. Clicked install again. Why it didn't work the first time I tried it I don't know. Having chronic sinuses and burning eyes I don't always see things clearly.

---

### Post by parmstrong on 2011-09-27
This worked for me also, thanks.  I swear I tried this a few days ago with no luck.  Anyway, just glad to have it going again.

---

### Post by ofnuts on 2011-09-28
> **Camilia said:**
> I embarrassed to say that I followed ofnuts previous instructions. That is looked for Lightning 1.0B2 for your TB 3.1. Saved it to disk. Clicked on install. Went to it location on disk and clicked on it. Clicked install again. Why it didn't work the first time I tried it I don't know. Having chronic sinuses and burning eyes I don't always see things clearly.
> **parmstrong said:**
> This worked for me also, thanks.  I swear I  tried this a few days ago with no luck.  Anyway, just glad to have it  going again.
** files his nails and whistles ** :-\"

---

