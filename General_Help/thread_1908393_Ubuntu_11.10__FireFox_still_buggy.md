---
title: "Ubuntu 11.10 / FireFox still buggy?"
date: 2012-01-13
forum: General Help
---

### Post by YMS_1975 on 2012-01-13
I've been keeping away from FireFox for some time. Today I reinstalled it thinking : Why did I remove it anyways? After reinstalling it, I quickly realized why I uninstalled it to begin with. Open a tab...FREEZE, type in a URL....FREEZE. Click on a link.....FREEZE. I immediately removed it thinking : Oh yeah. I forgot. This has been going on for a few months; like....6 months or so. I uninstalled it and proceeded to use Chromium, which btw is awesomeness! Just sayin'. I love FireFox but this glitchiness has got to go!  :lolflag:  I figured by now somebody would have come out with a fix for this by now, but guess not eh? Hope you're having a great day; it's freezing here in Ontario (brrrrrrrr.......)!!!!  :)

---

### Post by jerrrys on 2012-01-13
You have been running Linux for a long time and have learned nothing!  FF will not work in cold climates, thats why it freezes...

---

### Post by ajgreeny on 2012-01-13
> **jerrrys said:**
> You have been running Linux for a long time and have learned nothing!  FF will not work in cold climates, thats why it freezes...
I presume this was you making a joke?

@OP
I have been using FF all the time for the last several years and have hardly ever had any freezes when doing so.  Have you tried making a new profile or disabling the add-ons that you may have installed for FF, as there are known problems of incompatibility of add-ons, where one of them alone will be fine, but another running with it can cause big instability problems.

---

### Post by jerrrys on 2012-01-13
Yes aj, glad you picked right up on that.  I do not see a support question, thus we have a rant of sorts and I consider my reply justified...

---

### Post by ajgreeny on 2012-01-13
> **jerrrys said:**
> Yes aj, glad you picked right up on that.  I do not see a support question, thus we have a rant of sorts and I consider my reply justified...
Fair comment!

---

### Post by saneearth on 2012-01-13
I haven't had any issues with Firefox at all. When you installed, did you have your old .config files for firefox. There may be something wrong there. If you want to do a "clean" install you should delete the configuration files. This may not be your issue, but as bad as Firefox seems to be treating you I would suspect that there is something wrong there. May likely be an extension causing issues, but if you start from scratch you will know for sure if the issue is just Firefox or not. I like Chromium also, but there are a couple of things that Firefox has that it doesn't. I said I was having no issues, but this isn't completely correct. I think my Flash plugin working right, but is a recent development and I haven't tried to fix it yet.

---

### Post by YMS_1975 on 2012-01-13
Well,

I didn't have any add-ons or extensions. I believe it was a clean install (I could be wrong).

I installed it through the Ubuntu software center and immediately tried using it, but it constantly froze.

I would prefer to use FireFox; how would I delete the configuration files? I'd like to try and fix this.

---

### Post by YMS_1975 on 2012-01-13
> **jerrrys said:**
> Yes aj, glad you picked right up on that.  I do not see a support question, thus we have a rant of sorts and I consider my reply justified...

Totally justifiable.

:tongue:

---

### Post by dFlyer on 2012-01-13
> **YMS_1975 said:**
> I've been keeping away from FireFox for some time. Today I reinstalled it thinking : Why did I remove it anyways? After reinstalling it, I quickly realized why I uninstalled it to begin with. Open a tab...FREEZE, type in a URL....FREEZE. Click on a link.....FREEZE. I immediately removed it thinking : Oh yeah. I forgot. This has been going on for a few months; like....6 months or so. I uninstalled it and proceeded to use Chromium, which btw is awesomeness! Just sayin'. I love FireFox but this glitchiness has got to go!  :lolflag:  I figured by now somebody would have come out with a fix for this by now, but guess not eh? Hope you're having a great day; it's freezing here in Ontario (brrrrrrrr.......)!!!!  :)

You might want to try and remove the .mozilla folder located in your home folder on a fresh install to make sure there is nothing in it from the past that caused the problem. I've been using ff for years and haven't had any problems.

---

### Post by vasa1 on 2012-01-13
> **jerrrys said:**
> Yes aj, glad you picked right up on that.  I do not see a support question, thus we have a rant of sorts and I consider my reply justified...

+1. Either a rant or an "advertisement" for whatever reason.

---

### Post by YMS_1975 on 2012-01-13
> **vasa1 said:**
> +1. Either a rant or an "advertisement" for whatever reason.

An advertisement?

You've got to be joking. Or high. It was a rant. That's all.

---

### Post by guestolo on 2012-01-13
> **dFlyer said:**
> You might want to try and remove the .mozilla folder located in your home folder on a fresh install to make sure there is nothing in it from the past that caused the problem. I've been using ff for years and haven't had any problems.

As suggested by dFlyer, remove the hidden .mozilla folder
Also, include what Mozilla suggests

> Remove the firefox [Installation directory]("http://kb.mozillazine.org/Installation_directory"), usually: /usr/lib/firefox-<version>. For example, if using Firefox 1.0 it would be: /usr/lib/firefox-1.0

---

### Post by YMS_1975 on 2012-01-13
> **guestolo said:**
> As suggested by dFlyer, remove the hidden .mozilla folder
Also, include what Mozilla suggests

It's really odd, I've got 3 "Mozilla" folders (with a capital "M") and 2 "mozilla" folders (with a lower cases "m") & 1 "mozilla-firefox" folder. All of them but 1 has a locked icon on the folder.

It won't allow me to delete the one in the "/usr/lib/firefox-<version>" path. The "Move to Trash" option is grayed out. I also tried clicking once on the folder (to highlight it) and then pressing delete but that didn't work either.

:confused:

---

### Post by Scott Baker on 2012-01-13
I have noticed the same issues with F/F when 11.10 is installed as an *UPGRADE*. It seems to act buggy, sometimes freezing, sometimes opening *VERY* slowly. When 11.10 is installed as a fresh install though, I've not seen *any* problems with it (Firefox). I suspect that 11.10s kernal update may be causing the hiccups in your Firefox program. As has been mentioned in the past, strip out your Firefox files and start with a clean install of Firefox. That should get you back up and running. ](*,)

---

### Post by jerrrys on 2012-01-13
How many times have you upgraded?  You can gksudo nautilus and remove it/them.

Edit:  You should be able to locate your bookmarks folder and save it before you toast the .molliza(s)
folder(s).

---

### Post by YMS_1975 on 2012-01-13
> **jerrrys said:**
> How many times have you upgraded?  You can gksudo nautilus and remove it/them.

Edit:  You should be able to locate your bookmarks folder and save it before you toast the .molliza(s)
folder(s).

Thanks for the tip; I tried it though and it's still acting buggy. Constant freezing. I think what I'll do is a clean install. 

Hopefully that'll fix the problem.

---

### Post by YMS_1975 on 2012-01-13
Well I did a format of my drive and a clean install of 11.10 and _I'm still getting the same problem_. **Constant freezing**.

When I say "freezing" let me elaborate on what that means. I click on a tab, it lags for like 5 seconds before switching to that tab. Sometimes it won't switch to that new tab even after 5 seconds and if I continue to click on the tab, then the current screen goes black (you know, like when it asks you to "Force Close" ???).

I am not getting this problem with Chromium. Another factor *could* be hardware issue; and I'm starting to think that's what might be the problem. Although, my hardware hasn't changed. I've been using the same laptop (MSI GX720) for two years now.

This problem just started recently. Go figure. Oh well, for now I guess I'll have to use Chromium.

---

### Post by jerrrys on 2012-01-13
Thats bizarre.  Not running 64 bit are you?

I have pretty much good things to say about FF since version 5 came out.  But true, there are (for me) little quirks that I have noticed in the last two releases (Im running FF_8.  Example: I too am on a fresh install of 11.10 (week old) and FF was broke out of the box.  It was simple enough to fix (rm .mozilla), but yesterday it again started acting up (wouldn't remember a password).  So I again rm .mozilla and back in working order.  I would not be happy with this fix had I already customize my FF.

So 10o4 will remain my business end and 11.10 will remain my toy on this box.  I am anxious for 12o4 to come out.  Some are calling it the flagship of ubuntus.  And I think we will all see big improvements...

Good luck

---

### Post by YMS_1975 on 2012-01-13
> **jerrrys said:**
> Thats bizarre.  Not running 64 bit are you?

I have pretty much good things to say about FF since version 5 came out.  But true, there are (for me) little quirks that I have noticed in the last two releases (Im running FF_8.  Example: I too am on a fresh install of 11.10 (week old) and FF was broke out of the box.  It was simple enough to fix (rm .mozilla), but yesterday it again started acting up (wouldn't remember a password).  So I again rm .mozilla and back in working order.  I would not be happy with this fix had I already customize my FF.

So 10o4 will remain my business end and 11.10 will remain my toy on this box.  I am anxious for 12o4 to come out.  Some are calling it the flagship of ubuntus.  And I think we will all see big improvements...

Good luck

As a matter of fact I am running 64 bit. But like I said, I never had this problem before. After doing my format & re-install I'm confident it's a FF issue.

Oh well, I'm using Chromium again and I can honestly say that it's NOT a bug on my end.

Hopefully it'll clear up sooner than later. I love FireFox but right now she's just not usable.  :D

---

### Post by lovinglinux on 2012-01-20
Firefox runs perfectly on many users machines.

[LIST]
[*]make sure you have the latest Firefox installed. 
[*]make sure you have a clean profile
[*]make sure your video driver is properly installed and activated
[/LIST]

Please attach the firefox-report.txt file generated in your desktop after running the commands below:

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```

---

### Post by jerrrys on 2012-01-20
A script for trouble shooting firefox?  Im liking that, but when I run it, it hangs at:

/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Maybe this is for 64bit only?

---

### Post by lovinglinux on 2012-01-20
> **jerrrys said:**
> A script for trouble shooting firefox?  Im liking that, but when I run it, it hangs at:

/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Maybe this is for 64bit only?

Don't worry about those error messages, they are expected.

---

