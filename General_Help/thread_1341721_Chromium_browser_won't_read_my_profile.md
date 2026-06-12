---
title: "Chromium browser won't read my profile?"
date: 2009-11-30
forum: General Help
---

### Post by rxfwilliams on 2009-11-30
so i've been using chromium for a couple of months now with no issues. however, with no apparent cause, it give me this:

when i launch it, i get the message "Your profile could not be opened correctly.
Some features may be unavailable.  Please check that the profile exists and you have permission to read and write its contents."

and although my bookmarks, passwords, etc are intact, my most-visited eight sites on the opening page are no longer there, instead replaced by "welcome to chromium" and "chromium themes" sites, which were the default when i first got the program. 

i tried reinstalling through aptitude (reinstalled with no change to problem), and i tried and failed to hunt down some sort of profile-type file. i'm certain this is a problem with a straightforward solution, but my linux-fu is still at the yellow belt level...

---

### Post by Dougie187 on 2009-12-02
I had the same problem. I fixed it by this.

Open a terminal, type this
```
mv ~/.config/chromium/Default ~/.config/chromium/Backup
```

Now run chromium, and it should work. Then close it, and type this in your terminal.
```
rm -rf ~/.config/chromium/Default
cp -R ~/.config/chromium/Backup ~/.config/chromium/Default
```

Then when you open it all of your preferences should be back, and everything should be good.

EDIT:
If you want an easier way and don't care about your bookmarks and preferences or anything, you could close it and type this.
```
rm -rf ~/.config/chromium/Default
```
Then when you open it you should be able to start from scratch.

---

### Post by lexfati on 2009-12-02
I had also been running Chromium with no issues for a while, until about two weeks ago when I discovered that Google does have a .deb package of the [Chrome early release]("http://dev.chromium.org/getting-involved/dev-channel") (The link is near the bottom of the page; there are x32 and x64 .debs)

Its still considered an unstable package, but I've not experienced any issues at all, and it has in fact become my browser of choice on both my Kubuntu desktop and Debian macbook.

---

### Post by Dougie187 on 2009-12-03
> **lexfati said:**
> I had also been running Chromium with no issues for a while, until about two weeks ago when I discovered that Google does have a .deb package of the [Chrome early release]("http://dev.chromium.org/getting-involved/dev-channel") (The link is near the bottom of the page; there are x32 and x64 .debs)

Its still considered an unstable package, but I've not experienced any issues at all, and it has in fact become my browser of choice on both my Kubuntu desktop and Debian macbook.

If I remember correctly, this .deb is an older version. If you want to keep up to date you are probably better off using the daily builds from the chromium ppa. 
[https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)

Either way, it does work very well.

---

### Post by rxfwilliams on 2009-12-03
Dougie187- Thanks! Worked like a charm, no problems now.

Incidentally I am also running the dev version of chrome, but I have this unshakable feeling that Chromium is a little faster (and certainly is a bit more up-to-date).

---

### Post by Dougie187 on 2009-12-04
I would imagine it is more up-to-date. Especially since they update it every day.

---

### Post by FAJALOU on 2010-02-16
I have created a script to fix this error:
```
#!/bin/bash
mv -f ~/.config/chromium/Default/* ~/.config/chromium/Backup/
rm -rf ~/.config/chromium/Default
cp -R ~/.config/chromium/Backup/ ~/.config/chromium/Default/

```

Put that in a text doc, make it executable, and there we go.  Frustrating bug, but meh it works for now.
Maybe it's an extension error?

---

### Post by Dougle on 2010-02-17
> **FAJALOU said:**
> I have created a script to fix this error:
```
#!/bin/bash
mv -f ~/.config/chromium/Default/* ~/.config/chromium/Backup/
rm -rf ~/.config/chromium/Default
cp -R ~/.config/chromium/Backup/ ~/.config/chromium/Default/

```

Put that in a text doc, make it executable, and there we go.  Frustrating bug, but meh it works for now.
Maybe it's an extension error?

WTF! argh! noooooooo, fool me for copying and pasting.

```
[~] &#10132; mv -f ~/.config/chromium/Default/* ~/.config/chromium/Backup/
mv: target `/home/dougle/.config/chromium/Backup/' is not a directory
[~] &#10132; rm -rf ~/.config/chromium/Default
[~] &#10132; cp -R ~/.config/chromium/Backup/ ~/.config/chromium/Default/
cp: cannot stat `/home/dougle/.config/chromium/Backup/': No such file or directory
```

Needs a mkdir -p in there.

---

### Post by HobbitTR on 2010-02-24
I use Ubuntu 9.10 Karmic and Google Chrome 5.0.307.9 beta
After an unexpected shutdown of my laptop I got the "Your profile could not be opened correctly." message.
I had no chrome processes running after I shut Chrome down. 
I then found this thread, however, something did not make sense, the mv command should have been cp (mv in Linux changes the name, cp makes a copy)
I tried the cp command and the file "History-journal" gave up an input-output error.
I checked the permissions of the directory where my chrome data is located: ~/.config/google-chrome/Default
All was OK BUT the permissions of the History-journal file were different.
I deleted the History-journal file and no longer got the message: "Your profile could not be opened correctly."
I have had no previous problems with Google Chrome 5.0.307.9 beta.
If I have this problem again I will post an update.

---

### Post by wesley.jordan on 2010-03-02
Thank You Dougie187!  I have no clue what happened to break my profile all of a sudden but I was so grateful for your post that saved the day.

One thing that was different was that I was having problems with Google Chrome and not Chromium but the fix you provided worked perfectly when I changed the directories to:
~/.config/google-chrome/Backup
~/.config/google-chrome/Default

---

### Post by huygens on 2010-04-18
Thanks Dougie! It worked like a charm :)

---

### Post by fleamour on 2010-05-01
Seems to work for same error message in Google Chrome Beta.

```
rm -rf ~/.config/google-chrome/Default
```

Hope that helps someone.  Code nuke option though, I have bookmarks synced to GMail account.

---

### Post by fleamour on 2010-05-02
Had to re-visit as Google Chrome thrown up same error again.

---

### Post by knidsrok on 2010-05-07
The new Chrome beta started giving me this error.  

Dougie's fix, with the directory name changes accordingly, worked like a charm.

Three cheers for dougie!

---

### Post by mordak13 on 2010-05-13
Thanks Dougie for the fix. I got my Chromium back!!!:guitar:

---

### Post by Joliea on 2010-05-21
> **fleamour said:**
> Seems to work for same error message in Google Chrome Beta.

```
rm -rf ~/.config/google-chrome/Default
```

Hope that helps someone.  Code nuke option though, I have bookmarks synced to GMail account.
Thank You Thank You Thank You !!!!!

This DEFINITELY worked for me! YAY!!

p.s. i aint much of an ubuntu geek tho :cool:

---

### Post by Ertavf on 2010-05-22
```
rm -rf ~/.config/google-chrome/Default
```

Worked for me too. I used Sync function to get my Bookmarks again.

---

### Post by danbh on 2010-06-05
this did not quite work for me.  Deleting Default would work, but restoring would always bring it back. I had to:

rm ~/.config/chromium/Default/Web\ Data*

---

### Post by randumnumber on 2010-06-18
NOTE:

I had this issue with 10.04 ubuntu and used the "easy" method just deleting the Default folder, but it didn't solve the problem at first, the trick was that I had to remake the directory so chrome could find it again to create its default profile.

---

### Post by podlak on 2010-06-24
Hey lads,

I've done exactly what you were saying (I understand process) but it's still gives me the same error. 
**randumnumber**: what do you mean by > to remake the directory so chrome could find it again to create its default profile?

Thank you! :)

---

### Post by danbh on 2010-06-29
podlak, did you try just deleting Web Data?

---

### Post by jorok_tupur on 2010-07-05
> **Dougie187 said:**
> If you want an easier way and don't care about your bookmarks and preferences or anything, you could close it and type this.
```
rm -rf ~/.config/chromium/Default
```
Then when you open it you should be able to start from scratch.

This works for me. Thank you.

I remember that the problem showed up after the battery on my notebook died while I was browsing using chromium.

---

### Post by jason74 on 2010-07-12
> **Dougie187 said:**
> I had the same problem. I fixed it by this.

Open a terminal, type this
```
mv ~/.config/chromium/Default ~/.config/chromium/Backup
```

Now run chromium, and it should work. Then close it, and type this in your terminal.
```
rm -rf ~/.config/chromium/Default
cp -R ~/.config/chromium/Backup ~/.config/chromium/Default
```

Then when you open it all of your preferences should be back, and everything should be good.

EDIT:
If you want an easier way and don't care about your bookmarks and preferences or anything, you could close it and type this.
```
rm -rf ~/.config/chromium/Default
```
Then when you open it you should be able to start from scratch.

Please explain to me what you mean by enter this code into your terminal?? What do you mean by terminal? where do i imput this exactly? thanks

---

### Post by kombipom on 2010-07-13
> **jason74 said:**
> Please explain to me what you mean by enter this code into your terminal?? What do you mean by terminal? where do i imput this exactly? thanks

In your main Applications menu, go into the Accessories menu and select Terminal.  This will open a "terminal window".  This is the command line interface where typed commands can be entered. Similar to the DOS prompt (if you are old enough to remember that ;) ).  

It is well worth finding out what the most common commands are and how to use them.  A quick Google should bring up some help, just search for "linux command line cheatsheet" or something similar.

---

### Post by jason74 on 2010-07-13
This only began happening to me a couple of days ago after I uninstall-ed some programs with revo-uninstaller and so I went back a couple of days and did a system restore so obviously I uninstalled something that I shouldn't have becuase now everything is back to normal. Hope this helps some people.

---

### Post by jason74 on 2010-07-13
> **kombipom said:**
> In your main Applications menu, go into the Accessories menu and select Terminal.  This will open a "terminal window".  This is the command line interface where typed commands can be entered. Similar to the DOS prompt (if you are old enough to remember that ;) ).  

It is well worth finding out what the most common commands are and how to use them.  A quick Google should bring up some help, just search for "linux command line cheatsheet" or something similar.

Thanks friend:)

---

### Post by web032009 on 2010-07-18
> **wesley.jordan said:**
> 
~/.config/google-chrome/Backup
~/.config/google-chrome/Default

thanks this one works for me..

---

### Post by @dministrator on 2010-07-26
the Web Data file under the Default folder was the problem for me. Deleted this file and wala.. fixed

---

### Post by cmccullough on 2010-07-28
Starting from scratch was easy, especially, if you sync your bookmarks with you Google account. I absolutely love this feature in Chrome/Chromium.

---

### Post by myth01 on 2010-08-04
> **Dougie187 said:**
> 
EDIT:
If you want an easier way and don't care about your bookmarks and preferences or anything, you could close it and type this.
```
rm -rf ~/.config/chromium/Default
```
Then when you open it you should be able to start from scratch.

+1

The first method just re-created the error for me.  Wasn't bothered about bookmarks etc so just followed the above.

Cheers, it was remarkably frustrating for 1 message box.

---

### Post by fleachy on 2010-08-06
Hi guys,

If you are keen on using the terminal, a simple command should fix it. At least it worked for me. Conf: Ubuntu 10.04, Chrome 5.0.357.125.

Close your chrome and then, after opening your terminal just enter:

>.config/google-chrome/Default/Web\ Data

It will empty the contents of Web Data file.

Start chrome again and enjoy the music.:KS

---

### Post by FirstByté on 2010-08-12
since I made success with this

```

mv ~/.config/chromium/Default ~/.config/chromium/Backup
```
relaunch &
```

rm -rf ~/.config/chromium/Default
```

but got it broke again with this
```

cp -R ~/.config/chromium/Backup ~/.config/chromium/Default 
```

I decided to find the 'culprit' file by 'restoring' each file from the

> ~/.config/chromium/Backup

to
> ~/.config/chromium/Default

one after the other and figured out the culprit was 
> ~/.config/chromium/Default/**[COLOR="Red"]History[/COLOR]** 
Thus I just renamed it. and moved on with life
```
mv ~/.config/chromium/Default/History ~/.config/chromium/Default/History__old
```

Hope this helps someone. ;)

---

### Post by thiyagi on 2010-08-17
thanks man, it really worked though....

---

### Post by daygan on 2010-08-25
Strange. The aforementioned solutions didn't work for me. But when I deleted  > ~/.config/chromium/First Run and restarted Chromium it worked just fine. It seems that while the problem seems to be "the same" for each of us, the solution may differ slightly. hmm..

---

### Post by Cicer on 2010-08-25
Changing the name of the History file worked for me, too. But it was located at ~/.config/google-chrome/Default/History

---

### Post by daygan on 2010-08-25
I take back what I said previously. Deleting the "First Run" file only worked once. After closing chromium and starting again, the problem was back.

So then I deleted everything in the "Default" directory and systematically restored files one by one to find the problem file. For me, it turned out to be "Web Data".

---

### Post by syed.rakib.al.hasan on 2010-09-10
Removing WEB DATA did not work for me...........


> **Dougie187 said:**
> I had the same problem. I fixed it by this.

Open a terminal, type this
```
mv ~/.config/chromium/Default ~/.config/chromium/Backup
```Now run chromium, and it should work. Then close it, and type this in your terminal.
```
rm -rf ~/.config/chromium/Default
cp -R ~/.config/chromium/Backup ~/.config/chromium/Default
```Then when you open it all of your preferences should be back, and everything should be good.

EDIT:
If you want an easier way and don't care about your bookmarks and preferences or anything, you could close it and type this.
```
rm -rf ~/.config/chromium/Default
```Then when you open it you should be able to start from scratch.

when everything was moved from default to backup..... chromium worked fine with no error (without all the extensions and configurations of course)........ but once the contents from Backup were copied recursively back to Default, the same problem prevailed.

---

### Post by CydonianTR on 2010-09-14
FINAL & WORKING SOLUTION for "Your profile could not be opened correctly" error in Google Chrome 
(Tested on Windows XP Home with Google Chrome v6.0.472.55)

I have found that this error comes out because of corrupted history file (a file which holds record of old visited web sites) in Google Chrome so when you try to delete old history files within Google Chrome settings/preferences, Chrome keeps giving an error and it keeps crashing !

So here is the solution:

Go to this link
[http://www.hotcleaner.com/clickclean_chrome.html](http://www.hotcleaner.com/clickclean_chrome.html)

On that page, click on "Add Click&Clean to Chrome" icon and it installs "Click&Clean" add-on.
Then on the right bottom of your screen you will see a blue icon of it, you can choose what to delete in add-on's settings.
Be sure to choose "history files" for deleting. After cleaning, Google Chrome works NORMAL without any error!

Peace!
CydonianTR (Istanbul, Turkey)

---

### Post by damipereira on 2010-09-24
I can't believe no one tried changing permissions.
I fixed simply by doing:

```

sudo chmod 770 -R ~/.config/chromium
sudo chown USER:USER -R ~/.config/chromium (replace USER with your own user)

```

I think this error comes when chromium/chrome it's opened with sudo (it happened just after I did that) so the folder changes it's permissions to root and only lets read permission.
Firs I tried the other solution, but copying back Default folder caused it to come back, that is because the command that everyone uses has sudo, so the Backup folder is created with root permissions.

---

### Post by joebrueske on 2010-09-29
> **fleachy said:**
> Hi guys,

If you are keen on using the terminal, a simple command should fix it. At least it worked for me. Conf: Ubuntu 10.04, Chrome 5.0.357.125.

Close your chrome and then, after opening your terminal just enter:
```
>.config/google-chrome/Default/Web\ Data
```

It will empty the contents of Web Data file.

Start chrome again and enjoy the music.:KS

This worked for me using running 6.0 from the ppa. For those of you who love copy paste, please note the directory difference. It's different between version.

[quote=CydonianTR]FINAL & WORKING SOLUTION for "Your profile could not be opened correctly" error in Google Chrome 
(Tested on Windows XP Home with Google Chrome v6.0.472.55)

Go to this link
[http://www.hotcleaner.com/clickclean_chrome.html](http://www.hotcleaner.com/clickclean_chrome.html)
[/quote]

Version 6 of Click & Clean is **only available for Windows**. :confused: This isn't a Windows forum silly. Though it's interesting that you found a corrupt history.

---

### Post by belligerent_bill on 2010-10-09
I'm using the latest Google Chrome stable in Lucid Lynx 32 bit.  I tried a number of suggestions here to no avail.  After getting frustrated I tried a more dramatic approach and it worked.  I first performed a complete removal of Chrome with Synaptic.  I then opened terminal and changed directories to /.config. I then removed the google-chrome directory and all it's contents. 

From ~/.config$sudo rm -rf google-chrome

I re-installed Google Chrome and I've got a fresh start without the problem.

NOTE: Only proceed with this method if you want a quick solution and are OK with a fresh start.  You will loose all of your CHrome profile settings, bookmarks, etc.

---

### Post by Zealoct on 2010-12-17
> **Dougie187 said:**
> I had the same problem. I fixed it by this.

Open a terminal, type this
```
mv ~/.config/chromium/Default ~/.config/chromium/Backup
```Now run chromium, and it should work. Then close it, and type this in your terminal.
```
rm -rf ~/.config/chromium/Default
cp -R ~/.config/chromium/Backup ~/.config/chromium/Default
```Then when you open it all of your preferences should be back, and everything should be good.

EDIT:
If you want an easier way and don't care about your bookmarks and preferences or anything, you could close it and type this.
```
rm -rf ~/.config/chromium/Default
```Then when you open it you should be able to start from scratch.

this error is cause by that some of the configure files in "~/.config/google-chrome/" is owned by root
all you need to do is check files under that directory and change files that owned by root to yourself

for me, two files "google-chrome/Local State" and "google-chrome/Default/Preference" are owned by root
all i need to do is
```
sudo chown Zealoct ~/.config/google-chrome/Local\ State
sudo chgrp Zealoct ~/.config/google-chrome/Local\ State
sudo chown Zealoct ~/.config/google-chrome/Default/Preference
sudo chgrp Zealoct ~/.config/google-chrome/Default/Preference
```

---

### Post by budakmanga on 2011-01-03
hi everyone.

i came acroos your threads about google chrome profile not functioning well. I`m wondering if you could help me.

You see,I`m newbie in tech world. I`m not familiar with tech words.

My first questions. Where is the so call terminal?

I cant find it everywhere. I even use the "search" still cant find it.

therefore,i am truly happy and appreciate it if you could help me step by step.

Please.

regard,
budakmanga

---

### Post by Hilko on 2011-03-13
Hi Budakmanga,

You've probably find the terminal by now. But just in case; go to the menu on the top left corner of your screen
Applications -> Accessoires -> Terminal.

---

### Post by filosofic on 2011-04-29
Didn't work for me -- kept getting the same error.  Then checked ls -alh and found that chromium didn't have full permission for my username so I sudo chmod 755 -R the chromium config folder and now all ok.  Perhaps that's because I'm using Iron which is built on Chromium.

---

### Post by desmane on 2011-06-01
sudo rm .config/chromium/Default/History-journal

fixed it for me

---

### Post by Tybear241083 on 2011-06-30
I know this is marked as solved but I don't think I found what worked for me.

Essentially the problem with me was that the Local State file had somehow become owned by root.

I fixed the problem as follows:
```

sudo chown -R username:username ~/.config/chromium/Local\ State

```

Closed and reopened Chromium and notification was gone. 

Hope this helps someone.

---

### Post by eayoungs on 2011-11-19
> **wesley.jordan said:**
> Thank You Dougie187!  I have no clue what happened to break my profile all of a sudden but I was so grateful for your post that saved the day.

One thing that was different was that I was having problems with Google Chrome and not Chromium but the fix you provided worked perfectly when I changed the directories to:
~/.config/google-chrome/Backup
~/.config/google-chrome/Default

This worked like a charm for me too! Strange that it just stopped out of no where, then simply copying the files back makes it work again? Not sure why but it does.

E

---

### Post by colobix on 2011-11-26
Are there any actual fix for this?
I don't want to remove my settings or anything.

---

### Post by kayncz on 2011-12-19
> **danbh said:**
> this did not quite work for me.  Deleting Default would work, but restoring would always bring it back. I had to:

rm ~/.config/chromium/Default/Web\ Data*

It works for me, thx ;-)

---

### Post by kachar136 on 2012-05-18
The problem sometimes is that some files inside ~/.config/google-crhome/ are owned by root or different user. You can easily chown them back to your user and you don't have to delete them.
[HTML]sudo chown -R <username> ~/.config/google-crhome/[/HTML]Hope this helps someone.

---

### Post by donaldp on 2012-12-30
> **Zealoct said:**
> this error is cause by that some of the configure files in "~/.config/google-chrome/" is owned by root
all you need to do is check files under that directory and change files that owned by root to yourself


Glad to find out how to fix it, but..

If I've been using Chrome for quite a while with no problem, how did this happen?

---

### Post by rrich1974 on 2012-12-30
the same thing can happen to chrome too. i had the issue. i simply delete the google-chrome folder in the .config, there was no problem for me since i had all my bookmarks stored in the gmail.

---

