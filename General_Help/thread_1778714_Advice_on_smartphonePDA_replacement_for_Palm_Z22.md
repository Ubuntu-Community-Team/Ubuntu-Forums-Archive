---
title: "Advice on smartphone/PDA replacement for Palm Z22"
date: 2011-06-09
forum: General Help
---

### Post by ceperman on 2011-06-09
I have a Palm Z22 PDA for which I use JPilot to sync to my Ubuntu desktop. I've used this for many years, and use the calendar, contacts (phone book) and notes features most. The sync to the desktop is not just for backup - I can bulk enter data faster through the desktop when necessary.

The battery has died on this trusty PDA and I need to find a replacement. I know that PDAs have pretty much been replaced by smart phones now, but this is OK for me as my aging Nokia phone is probably due for replacement also (you can tell that this is technology I've not kept up with!).

So, I need advice on a suitable replacement that will still give me the same sort of PDA features and PDA-sync capability in Ubuntu. Some sort of security (password or otherwise) for the device is essential. Suggestions?

---

### Post by sanderd17 on 2011-06-09
All android phones offer support to sync with a google account (contacts, mail, calendar). The support is activated from the first time that you enter your login details, and on it's turn, most other mail/calendar/contact clients can sync with Google too.

If you don't like Google, you can do without it, but it's most of all web centred (so you need to use another web service as Yahoo or so).

I've written two blog posts about Android without Google (in fact, with only open-source apps), just to check if I could be independent from Google.

[http://ossandod.blogspot.com/2011/06/my-android-and-pure-aosp.html](http://ossandod.blogspot.com/2011/06/my-android-and-pure-aosp.html)

iPhone does only offers syncing through iTunes (which cannot be installed in Ubuntu) and I don't know anything about other smartphones.

---

### Post by ceperman on 2011-06-18
I keep passwords in the memo facility of my current PDA, which is why some form of security in the device is essential, and also why I need it to sync (backup/replicate or whatever) to my PC and not into the cloud where security is outside my control.

---

### Post by sanderd17 on 2011-06-19
Do you store it in plain text?

An Android phone presents itself as an external storage device on your computer. So you could use an Ubuntu sync program to download the files from your phone.

As an alternative, you could use the ADB (Android Debugging Bridge, used by developers to control their phone with their computer) and a note taking app. You can write a bash script for ADB that exports notes from the note taking app.

This app can take private notes (protected with a pwd): [https://market.android.com/details?id=com.flufflydelusions.app.notesclassiclite&feature=search_result](https://market.android.com/details?id=com.flufflydelusions.app.notesclassiclite&feature=search_result) . And this is the developer of that app: [http://ubuntuforums.org/member.php?u=14859](http://ubuntuforums.org/member.php?u=14859) .

---

### Post by christopher.wortman on 2011-06-19
If you use Linux, I agree use Android.

iPhones don't tend to get along with Linux.

Android syncs perfectly with Kaddressbook, Kontacts, and KDE's calendar. I suppose it works with Google services too ;)

On a side note, Windows Phone 7 works well with Ubuntu. Surprisingly enough, it syncs with Thunderbird with no hassle at all. I know I might catch some phlak for this, but WP7 is a decent way to go because every device has to meet some standards so you will be getting a decent device. Much less than I can say for Android, also they have a very Apple way of dealing with their App market, which is kind of good in a way. You wont run into viruses, trojans, and worms. Android has a few.

I really like my Android phone, and I like the Windows Phone 7 (any of them suffice) one even has 4 channel surround sound. (played with one at work)

Stay as far away from iPhone as possible unless you own a Mac. iTunes and Windows don't get along and updating an iPhone's iOS in an unstable environment seems scary, and unless you live near an Apple store, you might be driving a bit if you mess up the upgrade.

---

### Post by ceperman on 2011-06-22
Thanks guys - useful stuff in here.

FYI I've no intention of going near an iPhone!

---

