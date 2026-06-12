---
title: "Syncing Ubuntu - need to set up multiple machines"
date: 2010-05-04
forum: General Help
---

### Post by Christof999 on 2010-05-04
Hi, 

I just installed ubuntu 10.04 x64. I have installed it and set it up the way I like on my server, however I now have 3 terminals and a laptop to set it up on the exact same way. As a result Id like some advice on what can and cant be done and how. Preferably I am looking to use programs with GUIs. Thing the style of ubuntu one, software manager etc, not really too into the command line, or conf editing unless there is no other option.

1. I installed all the software from software centre I like. Now I need the same software on the other computers. I know mint has mintbackup where it just exports and imports a list if installed software. I am looking for an ubuntu equivalent.

2. Firefox and Thunderbird add-ons. I install like 20 firefox and thunderbird add ons. sometimes I can't even keep track of them. There must be a way to sync them so that each computer I install ubuntu on I can simply import the list of mozilla add ons and have it auto download them.

3. Mail Contacts and Calender Syncing. I need to sync between my 3 ubuntu machines and my windows mobile 6.5 device for calender, email/phone/name contact lists. Email is taken care of by imap, but lightnings calender isnt and neither are the contacts. If I input a contact on my phone I want it to sync to the other computers I use.

4. Ubuntu one. I have /storage/workfolder in my root directory on my personal server. I want to be able to work on documents at work on my laptop and sync them so that when I get home, they are synced on the server without causing overwrite changes etc.

These are the big ones. I also would really like...

5. Desktop settings, icon themes, preferences from ubuntu tweak etc. I know this one is a bit more of a long shot, but it takes 20 minutes each computer, to set up the little maximize minimize buttons on the other side, set up cairo dock the way I like, install the icon theme and backgrounds I like. isnt there a way to back this up so it doesnt have to be done each time or so I can make my other computers the same?

Any help is greatly appreciated
Chris

---

### Post by lovinglinux on 2010-05-05
Please read until the end before starting.

> **Christof999 said:**
> 1. I installed all the software from software centre I like. Now I need the same software on the other computers. I know mint has mintbackup where it just exports and imports a list if installed software. I am looking for an ubuntu equivalent.

Use [Umarks 2.0.0beta2](http://lovinglinux.megabyet.net/?page_id=534) (I'm the developer).

> **Christof999 said:**
> 2. Firefox and Thunderbird add-ons. I install like 20 firefox and thunderbird add ons. sometimes I can't even keep track of them. There must be a way to sync them so that each computer I install ubuntu on I can simply import the list of mozilla add ons and have it auto download them.

You can install [Add-on Collector](https://addons.mozilla.org/en-US/firefox/addon/11950) on all machines (Firefox and Thunderbird), then create an automatic list of your installed add-ons (Auto-publisher feature) on the machine with the add-ons already installed. On the other machines, [subscribe to your own collection on Mozilla](https://addons.mozilla.org/en-US/firefox/collections/mine) site. The Add-on Collector will allow to install them on the other machines and keep them in sync.

Alternatively, install [FEBE](https://addons.mozilla.org/en-US/firefox/addon/2109) and [TEBE](http://tebe.softwarebychuck.com/). Use the Quick Backup feature with the option "Create single xpi" to pack all the add-ons together into a single xpi file that can be installed as a regular extension.

I'm not sure if TEBE does that, since I never used it (I use [Simple Mail](https://addons.mozilla.org/en-US/firefox/addon/5593)). If not, then export the extensions and pack them together with [CLEO](https://addons.mozilla.org/en-US/firefox/addon/2942). You need to install CLEO on Firefox and use it to pack the Thunderbird extensions into a single xpi file, which I suppose will work, although I never tried.

> **Christof999 said:**
> 3. Mail Contacts and Calender Syncing. I need to sync between my 3 ubuntu machines and my windows mobile 6.5 device for calender, email/phone/name contact lists. Email is taken care of by imap, but lightnings calender isnt and neither are the contacts. If I input a contact on my phone I want it to sync to the other computers I use.

If you need one time sync, then simply copy the ./thunderbird folder to the other machines. If you need daily sync, then try 
[http://gcaldaemon.sourceforge.net/](http://gcaldaemon.sourceforge.net/)

> **Christof999 said:**
> 4. Ubuntu one. I have /storage/workfolder in my root directory on my personal server. I want to be able to work on documents at work on my laptop and sync them so that when I get home, they are synced on the server without causing overwrite changes etc.

I have no idea. I tried Ubuntu One, but it didn't work well for me. Perhaps [Dropbox](https://www.dropbox.com/) could be a better option for you.

> **Christof999 said:**
> 5. Desktop settings, icon themes, preferences from ubuntu tweak etc. I know this one is a bit more of a long shot, but it takes 20 minutes each computer, to set up the little maximize minimize buttons on the other side, set up cairo dock the way I like, install the icon theme and backgrounds I like. isnt there a way to back this up so it doesnt have to be done each time or so I can make my other computers the same?

You can backup all hidden folders from your home directory and copy to the other machines. Nevertheless, if you are using different user names on the other machines, then you need to manually edit or create a script to replace the original user home path with the new user home path on some files. For instance, a couple of days ago I decided to install Lucid again from scratch, since I was using it since Beta 2 and I had a few issues. I also decided to change my user name to my nickname used on the forums, to make easier for video demos. So, after the install I copied only the most important config folders and files from my old user home into the new user home. Then I run kfind (I'm using KDE) to find files containing **/home/olduser**, then I opened all the files with a text editor and replaced **/home/olduser **with **/home/lovinglinux**. Worked like a charm. Keep in mind that if the other machines are used by other people, then you might need an extra care in order to avoid copying your authentication keys, passwords, passphrases and such.

Anyway, if you need one time sync, then you could do it all with [Remastersys](http://remastersys.sourceforge.net/remastersystool.html).

---

