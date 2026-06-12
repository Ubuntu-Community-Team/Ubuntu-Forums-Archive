---
title: "Thunderbird keeps crashing"
date: 2012-06-17
forum: General Help
---

### Post by eadwacer on 2012-06-17
My summary of what I think went wrong and what works is in my [Solution Summary] message at the end of this thread.

Running an OEM (Sys76) install of 12.04 for my wife's new PC. Been using Thunderbird as the mailer successfully for almost a month. 

Today, Thunderbird started crashing. It will open for about 3 seconds, then close with a Mozilla crash report window. 

While it's up it works -- it got a message, and I've deleted a couple of messages, and the Reporter says it sent the report OK.

Watching the system monitor, I see two Thunderbird bins pop up, then one goes away, then the other goes away, and takes Thunderbird with it.

Can't find anything similar on the forums.

Part of the report reads:
Add-ons: [email]langpack-en-GB@thunderbird.mozilla.org:12.0.1,globalmenu@ubuntu.com:3.2.3,edsintegration@mozilla.com:0.3.9,messagingmenu@mozilla.com[/email]:0.9.3,{972ce4c6-7e08-4474-a285-3208198ce6fd}:12.0.1
BuildID: 20120430060637
CrashTime: 1339957418
EMCheckCompatibility: true

---

### Post by SeijiSensei on 2012-06-17
Is there another version of Thunderbird on the system other than the one from the repositories?  Like perhaps a version installed directly from Mozilla?

Try this from a Terminal window:

First, move your Thunderbird settings to a safe place

```
cd ~
mv .thunderbird .thunderbird.old
```

Next remove the existing repository version of Thunderbird:

```
sudo apt-get purge thunderbird
```

Now try running Thunderbird by typing "thunderbird" at the terminal prompt.  If the only copy is the one from the repositories, this shouldn't work.  If, for some reason, a Thunderbird window does appear, then you must have a second copy installed somewhere.  Try running:

```
sudo updatedb
locate thunderbird

```

and see what appears.  If you see something with  "bin/thunderbird" in it that's the copy you need to delete.

If you only had the repository version, then I'd next reinstall Thunderbird from the repositories with

```
sudo apt-get update
sudo apt-get install thunderbird
```

Now try running Thunderbird again.  Since you moved your .thunderbird directory at the outset, you should be greeted with a brand-new configuration asking you to set up your mail account.  If you can do that successfully and reach your mail, then the settings in the directory that you renamed to .thunderbird.old was somehow corrupted.

---

### Post by eadwacer on 2012-06-17
SeijiSensei

Thanks for the quick response. I'm not sure how a second copy might have gotten installed, but stranger things have happened...

I will report back on how it went. Thanks.


> **SeijiSensei said:**
> Is there another version of Thunderbird on the system other than the one from the repositories?  Like perhaps a version installed directly from Mozilla?

Try this from a Terminal window:

First, move your Thunderbird settings to a safe place

```
cd ~
mv .thunderbird .thunderbird.old
```

Next remove the existing repository version of Thunderbird:

```
sudo apt-get purge thunderbird
```

Now try running Thunderbird by typing "thunderbird" at the terminal prompt.  If the only copy is the one from the repositories, this shouldn't work.  If, for some reason, a Thunderbird window does appear, then you must have a second copy installed somewhere.  Try running:

```
sudo updatedb
locate thunderbird

```

and see what appears.  If you see something with  "bin/thunderbird" in it that's the copy you need to delete.

If you only had the repository version, then I'd next reinstall Thunderbird from the repositories with

```
sudo apt-get update
sudo apt-get install thunderbird
```

Now try running Thunderbird again.  Since you moved your .thunderbird directory at the outset, you should be greeted with a brand-new configuration asking you to set up your mail account.  If you can do that successfully and reach your mail, then the settings in the directory that you renamed to .thunderbird.old was somehow corrupted.

---

### Post by eadwacer on 2012-06-17
I'm going to have to wait until tomorrow AM to try this. I didn't write down the new centurylink account config data, so I'll have to call them. They were surprisingly helpful last time.

---

### Post by eadwacer on 2012-06-18
That was it. I did not actually see any other version (a lot of archived files), but a reinstall solve the crashing problem. Thank you sensei.

I might be back, if I can't figure out how to migrate my old mailboxes to the new install.

---

### Post by eadwacer on 2012-06-19
I had two problems. (1) How to keep TB from crashing, and (2) how to recover my old emails.

Following the instructions in the current thread solved (1). I did not actually see any bin files. Here's everything that wasn't in .thunderbird.old:

/usr/lib/firefox-addons/extensions/globalmenu@ubuntu.com/chrome/globalmenu/content/thunderbirdMenu.js
/usr/lib/firefox-addons/extensions/globalmenu@ubuntu.com/chrome/globalmenu/content/thunderbirdOverlay.xul
/usr/share/app-install/desktop/thunderbird:thunderbird.desktop
/usr/share/app-install/icons/thunderbird.png
/usr/share/icons/HighContrast/scalable/apps-extra/thunderbird-icon.svg
/var/cache/apt/archives/thunderbird-globalmenu_12.0.1+build1-0ubuntu0.12.04.1_amd64.deb
/var/cache/apt/archives/thunderbird-gnome-support_12.0.1+build1-0ubuntu0.12.04.1_amd64.deb
/var/cache/apt/archives/thunderbird-locale-en-us_1%3a12.0.1+build1-0ubuntu0.12.04.1_all.deb
/var/cache/apt/archives/thunderbird-locale-en_1%3a12.0.1+build1-0ubuntu0.12.04.1_amd64.deb
/var/cache/apt/archives/thunderbird_12.0.1+build1-0ubuntu0.12.04.1_amd64.deb

Since nothing looked like an executable, I left all alone, and just reinstalled TB. 

On to problem (2)
Fought with this for a while, during which TB was stable but uncooperative, due to my ineptness.

Finally, based on advice on another question I asked about recovering the files, I deleted the old account, created a new one, and deleted the Mail folder under the .thunderbird/garble/Mail copied over the .old Mail folder, went inside, and renamed the mailserver folder to match the new mailserver name. Fired up TB, and I saw all the messages.

Thirty seconds later, TB crashed, and returned to its original behavior.

I suspect it may have to do with a corrupt .mbox file or such, but I'd like to salvage as much as possible. Any suggestions?

---

### Post by eadwacer on 2012-06-19
I'm going to close this one out also, because I think we've learned everything we can here.

1. Constant Thunderbird crashes can be due to it colliding with another copy of itself every time it opens. OR

2. Constant Thunderbird crashes can be due to it attempting to open a corrupt mail file every time it opens.

3. The solution to (1) is as stated above. Back up TB, remove the known copy, locate any other copies and remove them, reinstall TB.
3A. Retrieve old mail by deleting the newly installed Mail folder and copying the old Mail folder in its place. Note that you have to make sure that the server-named folder inside Mail has the correct server name. See my thread on migrating TB mail.

4. If you follow (3), you also solve (2), except that you won't find an extra copy of TB to delete before the new install. However, if you have corrupted files in your old Mail folder, you don't want to bring it over, so don't do (3A). 

5. I have not validated a solution to this, but my next approach would be to move one mail subfolder at a time from the old to the new. Close TB, copy all .mbox, .sbd files with identical names (one name only) to the equivalent location in the new TB Mail folder. Open TB and look at your mail. If it doesn't crash, go back and try another file. If it does crash, delete what you've just moved, and cry a little.

I'd be happy to see any corrections/comments to this.

---

