---
title: "Firefox not starting"
date: 2012-05-13
forum: General Help
---

### Post by poloivan on 2012-05-13
Hello Ubuntu Users.


I'm having problems with Firefox and any kind Mozilla related products. They just don't start!

I already tried reinstalling, purge, removing profiles, removing .mozilla, removing /usr/lib/firefox...

Whatever try to fix doesn't work.
What else should I try to make this work? I click the applications and they "seem" to run but nothing appears, no errors, even from running it from Terminal won't give errors (as root too).

I'm really in trouble with this, not even Thunderbird is starting, it happens the same as explained.

I'm running Ubuntu 12.04 on AMD FX 8150 @ 4.4 Ghz, 16 GB RAM. Packages are up-to-date.


Any tip accepted, please!
Thanks in advance.

With best regards,
Ivan.

---

### Post by poloivan on 2012-05-13
Anyone, please?

Thanks in advance.

---

### Post by poloivan on 2012-05-14
Seriously nobody knows about this?

---

### Post by steeldriver on 2012-05-14
when they "seem" to run, do any processes actually start (ps -ef | grep firefox)?

---

### Post by roelforg on 2012-05-14
First run:
```

sudo apt-get install --reinstall firefox

```
as you said you removed some ff special files.
And then follow steeldriver's suggestion.

---

### Post by poloivan on 2012-05-14
> **roelforg said:**
> First run:
```

sudo apt-get install --reinstall firefox

```
as you said you removed some ff special files.
And then follow steeldriver's suggestion.

Thank you both for answering.

I did that process many times and still the same thing! It is not only happening with Firefox, it also happens with Thunderbird.

This came all since the last update that Ubuntu made on my software. It installed Firefox 12 and since this it isn't working. I already tried with Firefox 13 and still the same!

Is there a way of installing Firefox 11 again to see if it's working?

What could I do? I tried purge too with no way...

---

### Post by wilee-nilee on 2012-05-14
Might just be they are not closing any popups about them already running?

Start FF and Thunderbird from the terminal with just their names and see what errors you see.

---

### Post by poloivan on 2012-05-14
> **wilee-nilee said:**
> Might just be they are not closing any popups about them already running?

Start FF and Thunderbird from the terminal with just their names and see what errors you see.


Nothing, no errors.

prosaca@UBIEE-Ivan:~$ firefox
prosaca@UBIEE-Ivan:~$ thunderbird
prosaca@UBIEE-Ivan:~$

What the hell is going on? lol.. I don't want to reinstall my computer.

---

### Post by wilee-nilee on 2012-05-14
> **poloivan said:**
> Nothing, no errors.

prosaca@UBIEE-Ivan:~$ firefox
prosaca@UBIEE-Ivan:~$ thunderbird
prosaca@UBIEE-Ivan:~$

Very strange.

---

### Post by steeldriver on 2012-05-14
can you try

```
which firefox
```and then ls -al the result (just want to see nothing got messed up with $PATH and/or symlinks)

same for tbird

---

### Post by poloivan on 2012-05-14
> **wilee-nilee said:**
> Very strange.


Indeed, but this is real happening...

Would someone who is trusted and knows about this come into Remote Desktop (like via Teamviewer) and try to help me with this issue?

Thanks for the answers.

With best regards,
Ivan.

---

### Post by ckop64 on 2012-05-14
If this only affects mozilla-related products this might as well be a XUL runner issue. I'm just guessing.

---

### Post by roelforg on 2012-05-14
Run this in a terminal:
```

DISPLAY=:0 firefox &
ps ax | grep firefox
pkill -SIGTERM firefox
pkill -SIGKILL firefox

```
and post the output.

---

### Post by poloivan on 2012-05-14
Thanks for the quick answers.

I don't know why but Firefox is now working, it just started lol.

Still, thunderbird doesn't open and I have all my mail there :|
There is no problems with paths or so, as which thunderbird shows /usr/bin/thunderbird, and that is ../lib/thunderbird/thunderbird.sh

Here is the oputput of it

prosaca@UBIEE-Ivan:~$ DISPLAY=:0 thunderbird &
[1] 9783
prosaca@UBIEE-Ivan:~$ ps ax | grep thunderbird
 9792 pts/1    S<+    0:00 grep --color=auto thunderbird
[1]+  Exit 1                  DISPLAY=:0 thunderbird
prosaca@UBIEE-Ivan:~$ pkill -SIGTERM thunderbird
prosaca@UBIEE-Ivan:~$ pkill -SIGKILL thunderbird
prosaca@UBIEE-Ivan:~$

---

### Post by roelforg on 2012-05-14
> **poloivan said:**
> Thanks for the quick answers.

I don't know why but Firefox is now working, it just started lol.

Still, thunderbird doesn't open and I have all my mail there :|
There is no problems with paths or so, as which thunderbird shows /usr/bin/thunderbird, and that is ../lib/thunderbird/thunderbird.sh

Here is the oputput of it

prosaca@UBIEE-Ivan:~$ DISPLAY=:0 thunderbird &
[1] 9783
prosaca@UBIEE-Ivan:~$ ps ax | grep thunderbird
 9792 pts/1    S<+    0:00 grep --color=auto thunderbird
[1]+  Exit 1                  DISPLAY=:0 thunderbird
prosaca@UBIEE-Ivan:~$ pkill -SIGTERM thunderbird
prosaca@UBIEE-Ivan:~$ pkill -SIGKILL thunderbird
prosaca@UBIEE-Ivan:~$

```

DISPLAY=:0 /usr/bin/thunderbird &

```
instead.
I think that the ../lib/something is wrong.

---

### Post by flemur13013 on 2012-05-14
Delete (rename) your ~/.mozilla directory?

---

### Post by poloivan on 2012-05-14
> **flemur13013 said:**
> Delete (rename) your ~/.mozilla directory?

Seriously, why do you bother even answering? Read my first post, please?


I tried with /usr/lib/thunderbird, still same. Really weird... Firefox working but still thunderbird doesn't!

Output: 
prosaca@UBIEE-Ivan:~/test$ DISPLAY=:0 /usr/bin/thunderbird &
[1] 13281

---

### Post by HiImTye on 2012-05-14
could always give
```
firefox --safe-mode
thunderbird --safe-mode
``` and loading with no addons a try, could be a problem with an extension in the repos or some mundane setting that nobody considered

---

### Post by poloivan on 2012-05-14
> **HiImTye said:**
> could always give
```
firefox --safe-mode
thunderbird --safe-mode
``` and loading with no addons a try, could be a problem with an extension in the repos or some mundane setting that nobody considered

They didn't start in safe mode too. Like I said before, my firefox is working fine but my thunderbird is not even starting... Same problem like I had in firefox still exist on my Thunderbird!

Nothing happens in I run it on safe mode too, also say that I have no plugins, it was a clean install of Ubuntu 12.04 like a week ago.


Somebody has this problem or knows how to debug to know what is causing this?
I'm dissapointed with this at the moment. On Windows if something doesn't load it normally gives you errors, but.. where are the errors here when starting my Thunderbird? It doesn't create any minidump or Crash report, just not starting without any error.

Please, if anybody knows anything else that I could do go ahead!

For those who didn't read my first thread: I tried removing all configs (.mozilla, .thunderbird), tried also with safe-mode, tried to startup the profile manager, reinstalled Thunderbird, purged thunderbird...

Whatever I do doesn't work.

Thanks for taking the time to helping me, I really appreciate what this community is doing with such good forum!

With best regards,
Ivan.

---

### Post by HiImTye on 2012-05-14
if you open it up using a terminal it will spit out info at you

---

### Post by roelforg on 2012-05-14
> **poloivan said:**
> They didn't start in safe mode too. Like I said before, my firefox is working fine but my thunderbird is not even starting... Same problem like I had in firefox still exist on my Thunderbird!

Nothing happens in I run it on safe mode too, also say that I have no plugins, it was a clean install of Ubuntu 12.04 like a week ago.


Somebody has this problem or knows how to debug to know what is causing this?
I'm dissapointed with this at the moment. On Windows if something doesn't load it normally gives you errors, but.. where are the errors here when starting my Thunderbird? It doesn't create any minidump or Crash report, just not starting without any error.

Please, if anybody knows anything else that I could do go ahead!

For those who didn't read my first thread: I tried removing all configs (.mozilla, .thunderbird), tried also with safe-mode, tried to startup the profile manager, reinstalled Thunderbird, purged thunderbird...

Whatever I do doesn't work.

Thanks for taking the time to helping me, I really appreciate what this community is doing with such good forum!

With best regards,
Ivan.

Could this help:
[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/561323](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/561323)
Same results: direct exit with errorcode 1
Several bugs are linked to from that page, most of them have fixes, see which one matches yours and try the fix.

---

### Post by poloivan on 2012-05-16
Sorry for the late answer.

Now again my firefox doesn't start.. what is going on? Why did ALL my mozilla products BREAK/BROKEN after Software Update?

What the hell is going on?

---

