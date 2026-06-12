---
title: "CheckGmail"
date: 2009-09-17
forum: General Help
---

### Post by Buschbarber on 2009-09-17
I have been using the app CheckGmail, from checkgmail.sf.net, to monitor my Gmail account and notify me, via an audible warning, when new messages have been received.

It has been working very well, until this week. Now, when I launch it, it displays my Gmail Login Credentials and says "Error - Incorrect Username and Password".

I tried reinstalling it and running "checkgmail -update" as specified on the checkgmail site.

Here is the output when I run checkgmail in Terminal

ich@UE23:~$ checkgmail
Perl exited with active threads:
	1 running and unjoined
	0 finished and unjoined
	0 running and detached
rich@UE23:~$ 

This is the reference to the 401 error I am receiving


401 Unauthorised Fix

Gmail recently changed the login procedure, resulting in this error. To fix this issue, please use the latest version from SVN -- the easiest way to do this is to run checkgmail -update from the commandline and follow the prompts. 

Any idea where I go from here?

---

### Post by llamabr on 2009-09-17
Just to be sure, you ran this command:

```
checkgmail -update
```

in the terminal, right?

---

### Post by Buschbarber on 2009-09-17
> **llamabr said:**
> Just to be sure, you ran this command:

```
checkgmail -update
```

in the terminal, right?

Yes!! I also Uninstalled CheckGmail, Reinstalled it, and applied the Update.

I am not having any other Login problems with either Direct Login from Firefox or with Gmail Screenlet.

---

### Post by Buschbarber on 2009-09-17
rich@UE23:~$ sudo checkgmail -update
[sudo] password for rich: 
Downloading latest version of checkgmail from SVN ...

Warning: wildcards not supported in HTTP.
--2009-09-17 22:43:07--  [http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail](http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail)
Resolving checkgmail.svn.sourceforge.net... 216.34.181.65
Connecting to checkgmail.svn.sourceforge.net|216.34.181.65|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: /viewvc/checkgmail/checkgmail [following]
--2009-09-17 22:43:07--  [http://checkgmail.svn.sourceforge.net/viewvc/checkgmail/checkgmail](http://checkgmail.svn.sourceforge.net/viewvc/checkgmail/checkgmail)
Connecting to checkgmail.svn.sourceforge.net|216.34.181.65|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/plain]
Saving to: `checkgmail'

    [  <=>                                  ] 196,280      541K/s   in 0.4s    

2009-09-17 22:43:08 (541 KB/s) - `checkgmail' saved [196280]



Differences between old and new versions:
diff -urN checkgmail /usr/bin/checkgmail
--- checkgmail	2009-09-17 22:43:08.000000000 -0400
+++ /usr/bin/checkgmail	2008-12-22 12:07:43.000000000 -0500
@@ -467,7 +467,7 @@
 	if (-e "$prefs_dir") {
 		print "Moving ~/.checkgmail to ~/.checkgmail/prefs ...\n\n";
 		rename("$HOME/.checkgmail", "$HOME/.checkgmailbak");
-		mkdir($prefs_dir, 0777);
+		mkdir($prefs_dir, 0700);
 		rename("$HOME/.checkgmailbak", "$prefs_dir/prefs");
 	} else {
 		# User hasn't run an old version, just create the dir
@@ -3490,8 +3490,8 @@
             login_title="Autentificando en Gmail ..."
             mail_archive="Archivar"
             mail_archiving="Archivando ..."
-            mail_delete="Delete"
-            mail_deleting="Deleting ..."
+            mail_delete="Borrar"
+            mail_deleting="Borrando ..."
             mail_mark="Marcar como leído"
             mail_mark_all="Marcar todos como leído"
             mail_marking="Marcando como leído ..."




OK to update to new version via 'sudo mv checkgmail /usr/bin/'?(Y/n)> y
Update NOT performed ...
Deleting temp file ...
Continuing with application startup ...

Creating translations file at /root/.checkgmail/lang.xml ...
Updating translations file ...
Wide character in print at /usr/bin/checkgmail line 5036.
 ... done!
Perl exited with active threads:
	1 running and unjoined
	0 finished and unjoined
	0 running and detached
rich@UE23:~$

---

### Post by giancaldo on 2009-09-18
I have exactly the same problem. I keep getting "Error: Incorrect username or password".

---

### Post by kerry_s on 2009-09-18
have you tried mail-notification instead?
it's not a pig on memory like checkgmail.

---

### Post by giancaldo on 2009-09-18
I found a solution on another forum. start checkgmail with the -no_cookies option

```
checkgmail -no_cookies
```

---

### Post by Buschbarber on 2009-09-18
> **kerry_s said:**
> have you tried mail-notification instead?
it's not a pig on memory like checkgmail.

Thanks!! I forgot why I did not like mail-notification, but I will try it again.

---

### Post by Buschbarber on 2009-09-18
> **giancaldo said:**
> I found a solution on another forum. start checkgmail with the -no_cookies option

```
checkgmail -no_cookies
```

This worked fine for me!! Thanks!!

---

### Post by kerry_s on 2009-09-18
> **Buschbarber said:**
> Thanks!! I forgot why I did not like mail-notification, but I will try it again.

you probably forgot to disable the password, so you probably had to keep typing the password on startup.
:lolflag:

it took me awhile to figure that one out. that was the main annoying thing for me, but now it's all good.

---

### Post by chrisamiller on 2009-09-18
The -no_cookies flag lets checkgmail notify me of new mail, but eliminates the option to archive, delete, etc.  I've filed a bug here:

[http://sourceforge.net/tracker/?func=detail&aid=2861960&group_id=137480&atid=738663](http://sourceforge.net/tracker/?func=detail&aid=2861960&group_id=137480&atid=738663)

The maintainer is usually pretty quick about dealing with bugs, so check back there for fixes.

---

### Post by Rasheeke on 2009-09-20
Same issue, Checkgmail has been working without incident ever since I first downloaded it, turned off computer last night, woke up to turn it on and now it keeps saying 'Error: Incorrect username or password'.  

Tried updating, tried uninstalling and reinstalling, tried updating again, none of that works, worked fine last night before turning off.

---

### Post by chiccoch on 2009-09-24
same problem in my case. running on jaunty x64, kernel 2.6.31.

no luck with reinstalls or new SVN versions.

[http://ubuntuforums.org/showthread.php?t=1268721&page=2](http://ubuntuforums.org/showthread.php?t=1268721&page=2)

[https://bugs.launchpad.net/ubuntu/+source/checkgmail/+bug/433497](https://bugs.launchpad.net/ubuntu/+source/checkgmail/+bug/433497)

---

### Post by dearingj on 2009-09-24
@Rasheeke & chicoch:
A few days ago I started getting the "incorrect username or password" message in all my multiple email programs, despite them all having successfully logged in before. One of my programs (the Mail app that comes with Mac OS X) popped up a message saying something to the effect of "The server says: 'Please log in using the web interface'." So, I went to gmail.com and logged in there, then logged back out and closed my browser, and now all my mail programs are able to connect again. I don't know why Gmail required me to log in on their site, but could that be the same problem you're having?

---

### Post by chiccoch on 2009-09-25
@ dearingj: no luck at all. since gmailchecker is not running im loggin in through gmail.com all the time. 

i also had no luck with reinstalling or trying wired/unwired networks rebooting or using the newest svn version. just doesn't work no more.

i guess its time to look for a new app. its now almost a weak since it doesn't work no more! an there's not even a single clue on the internet on what it could be.

i don't know if it is smart to try through solutions that have benn poste in 2006!

---

### Post by carniola on 2009-09-25
The creator seems to be aware of the problem and thinks it has to do with Google rolling out changes across some accounts. Here's what he wrote a few days ago [**here**]("http://sourceforge.net/projects/checkgmail/forums/forum/463626/topic/3405947"):

> Yes, it seems that some accounts are now using a new login process. It hasn't happened to any of my accounts yet, so it's currently impossible for me to fix, but I'm hoping that they'll be changed over soon... Sorry I can't be more help at the moment; I'll post again when this is fixed.

In the meantime, he's recommending
```
checkgmail - no_cookies
```

as a temporary fix.

---

### Post by hayim on 2009-09-26
OK! this sucks.

So I can confirm that this issue is **NOT account specific** (probably).

I started getting these 401's a couple days ago after i installed xubuntu 9.04 amd64 - but I just checked now and checkgmail on my DreamLinux3.5 laptop (jaunty based) *logs in fine* .

SO.. who else with this problem is running x64?

---

### Post by Buschbarber on 2009-09-26
> **hayim said:**
> OK! this sucks.

So I can confirm that this issue is **NOT account specific** (probably).

I started getting a couple days ago on my new Xubuntu jaunty amd64 system - but I just checked at checkgmail *logs in fine* on my DreamLinux3.5 laptop (jaunty based).

SO.. who else with this problem is running x64?

I am running 64bit. I have been using the -no_cookies for the time being.

---

### Post by ajdrew06 on 2009-09-28
I am running Ubuntu 9.04 32 bit.  I have been getting the login error for a couple of weeks now.  The last OS upgrade I performed was a few months ago.

---

### Post by hayim on 2009-09-28
> **ajdrew06 said:**
> I am running Ubuntu 9.04 32 bit.  I have been getting the login error for a couple of weeks now.  The last OS upgrade I performed was a few months ago.

Right then. So i guess it's more complicated than that. Can you log in from anywhere else?

Is it something else about our setups that is interfering with the cookies? 

:'(

---

### Post by Buschbarber on 2009-09-28
> **hayim said:**
> Right then. So i guess it's more complicated than that. Can you log in from anywhere else?

Is it something else about our setups that is interfering with the cookies? 

:'(

I currently use the Gmail Screenlet. It logs in to my Gmail account and displays the number of new messages as a number on the face of the icon.

I use CheckGmail because it plays a sound when new messages arrive.

I use my HDTV as a monitor and when I am watching tv and I receive a message, I can hear the prompt and switch over to the PC display.

I can also login successfully by launching Firefox and navigating to Gmail.

---

### Post by PumpkinSonnema on 2009-09-29
Having the same issue here, but just started this morning.  Busch, I noticed that in your upgrade output, it didn't actually update.  When it asks you need an uppercase Y to have it complete the upgrade.  Not that it matters at this point since the upgrade doesn't fix it.

Really want to see a fix to this, as it's a really great app.  Do any of the other gmail checkers execute custom commands on new mail?

---

### Post by Buschbarber on 2009-09-29
> **PumpkinSonnema said:**
> Having the same issue here, but just started this morning.  Busch, I noticed that in your upgrade output, it didn't actually update.  When it asks you need an uppercase Y to have it complete the upgrade.  Not that it matters at this point since the upgrade doesn't fix it.

Really want to see a fix to this, as it's a really great app.  Do any of the other gmail checkers execute custom commands on new mail?

Mail Notification - Monitors your mailboxes for new mail.
Updated by FastRunner on Thursday, May 22nd 2008.Mail Notification Screenshot

Mail Notification monitors your mailboxes for new mail. When new mail arrives, Mail Notification alerts you by displaying an icon in the notification area. Moreover, a mail summary can be displayed in the icon tooltip, a sound can be played, and notifications containing useful action buttons can be popped up.

Mail Notification can monitor multiple mailboxes concurrently, and supports Evolution, Gmail, IMAP, Maildir, mbox, MH, Mozilla products (Mozilla, SeaMonkey, Thunderbird, …), POP3, Sylpheed, Windows Live Hotmail and Yahoo! Mail mailboxes.

Moreover, since Mail Notification uses GnomeVFS, it transparently supports remote (SSH, HTTP, …) and compressed mailboxes.POP3 and IMAP features

Mail Notification supports advanced POP3 and IMAP features such as SSL/TLS connections (in-band or on separate port), SASL and APOP authentication, and the IMAP IDLE extension.
Licence : GPL

Version : 5.4 [Stable]

---

### Post by Gawains Green Knight on 2009-09-29
Mines on the blink too - started this morning.

It doesn't seem to be able to log in.... might be google have changed something?

---

### Post by karlmp on 2009-09-29
me too

using "checkgmail -no_cookies" now

---

### Post by vgrisham on 2009-09-29
I'm AMD64 too. This problem popped up on both of my computers today. Yesterday, they both worked fine. I don't think I installed any updates on either. I wonder if Google didn't tweek something on their end.

---

### Post by vgrisham on 2009-09-29
To those on this thread trying to get folks to switch to Mail Notification, checkgmail is simply a better tool for my needs; I love being able to manage stuff without launching a browser (Mark As Read, Archive, Report Spam). It's a real time saver.

---

### Post by uchari on 2009-09-29
Yes the same this is happening with my checkgmail app... does anyone has an idea how to fix that instead of using the screenlet app?

---

### Post by chrisamiller on 2009-09-29
FYI to everyone in this thread: 

The author is aware of the problem and is working on it. To stay posted on the bugfix progress, watch this thread on the sourceforge page:
[http://sourceforge.net/projects/checkgmail/forums/forum/463626/topic/3405947/index/page/1](http://sourceforge.net/projects/checkgmail/forums/forum/463626/topic/3405947/index/page/1)

---

### Post by Buschbarber on 2009-09-29
> **vgrisham said:**
> To those on this thread trying to get folks to switch to Mail Notification, checkgmail is simply a better tool for my needs; I love being able to manage stuff without launching a browser (Mark As Read, Archive, Report Spam). It's a real time saver.

I like CheckGmail, as well. I was just posting info on Mail Notification as a temporary option until the problem with CheckGmail has been resolved.

It appears not everyone's Gmail account was affected at the same time, so whatever Google did, it has been over a period of time. For me, it seems only CheckGmail was affected

---

### Post by Gawains Green Knight on 2009-09-30
Yeah mine works at home, but not in work. 

Both running xubuntu 9.04....

---

### Post by Buschbarber on 2009-09-30
One thing I don't like about the program Mail Notification is that while it's icon does display a number indicating how many new messages you have received, it seems to max out at 20. I think that is why I abandoned it when I first tried it months ago.

---

### Post by carniola on 2009-09-30
Bizarre-o fix that worked for me: Reboot your DSL modem. (Seems to have worked for the creator, and at least a few other people) My checkgmail fired up again on the second reset.

---

### Post by Phlinux on 2009-10-01
> **carniola said:**
> Bizarre-o fix that worked for me: Reboot your DSL modem. (Seems to have worked for the creator, and at least a few other people) My checkgmail fired up again on the second reset.

Yup - me too. Rebooted the ADSL modem (and the wireless AP connected to it for good measure, although I'm not sure if that would've had any bearing) and now everything is fine... some kinda caching issue?

---

### Post by vgrisham on 2009-10-01
It sure didin't work for me (AT&T DSL); not only that, this also doesn't solve the problem for those of us on corporate/school networks away from home.

---

### Post by dootzky on 2009-10-02
> **giancaldo said:**
> I found a solution on another forum. start checkgmail with the -no_cookies option

```
checkgmail -no_cookies
```

thanks, this worked for me as well. 
cheers,
dootzky

---

### Post by mybunche on 2009-10-03
> **giancaldo said:**
> I found a solution on another forum. start checkgmail with the -no_cookies option

```
checkgmail -no_cookies
```
Thank you very much.

---

### Post by carniola on 2009-10-05
There's now a fix in SVN...

```
checkgmail -update
```

(You'll need subversion installed) It worked for me.

---

### Post by baleks on 2009-10-11
> **Buschbarber said:**
> 
OK to update to new version via 'sudo mv checkgmail /usr/bin/'?(Y/n)> y
Update NOT performed ...
Deleting temp file ...
Continuing with application startup ...
rich@UE23:~$

Of course, you need to say "Y" but not "y" to perform an update!

But it seems updating dont fully solve this problem....

p.s. strange, but -no_cookies only work for @gmail.com email, but hosted email started working only after $ checkgmail -profile=... -update, and telling "Y", even if there is no difference in current and update files, and after "restarting checkgmail" it started working not asking for password again!

---

### Post by vgrisham on 2009-10-11
> **baleks said:**
> Of course, you need to say "Y" but not "y" to perform an update!

But it seems updating dont fully solve this problem....

p.s. strange, but -no_cookies only work for @gmail.com email, but hosted email started working only after $ checkgmail -profile=... -update, and telling "Y", even if there is no difference in current and update files, and after "restarting checkgmail" it started working not asking for password again!

Baleks, 

If you have installed subversion and have run the update command, it should install the latest revision (svn 40) and you won't need the no cookies option. However, it won't yet work with hosted domains; the developers are still working on that. Here's the [thread]("http://sourceforge.net/projects/checkgmail/forums/forum/463626/topic/3405947/index/page/2") where you can follow their progress.

---

### Post by hayim on 2009-10-24
awesome!! its working again (after update!)

my single favourite program, lol. phew.

thank you Mr Checkgmail!

---

### Post by vgrisham on 2009-10-24
For those experiencing the annoyance of being asked to log in each time you left click on the checkgmail icon (or when you open a message via checkgmail), launch checkgmail as: 

checkgmail --no-login

---

### Post by Johnny B on 2009-10-24
> **Buschbarber said:**
> 
OK to update to new version via 'sudo mv checkgmail /usr/bin/'?(Y/n)> y
Update NOT performed ...


you have to be sure to USE A CAPITAL Y !!!!!

---

### Post by Buschbarber on 2009-10-24
I just reinstalled Ubuntu 9.10 and CheckGmail only works if you use the -no_cookies setting. --no-login does not eliminate the problem, either.

I have been experimenting with 9.10 so I have had to reinstall it a number of times. It is always the same when it comes to checkgmail -no_cookies

---

