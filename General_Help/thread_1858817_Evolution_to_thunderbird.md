---
title: "Evolution to thunderbird"
date: 2011-10-13
forum: General Help
---

### Post by johnnie1uk on 2011-10-13
i see the 11.10 will have thunderbird instead of evolution as the email client.
after download will all my evolution settings be transferred to thunderbird seamlessly or will i have to make some adjustments

---

### Post by mastablasta on 2011-10-13
try it. as i remember Thunderbird finds most things usually by itself. maybe oyu iwll need to type in password and username.

---

### Post by johnnie1uk on 2011-10-13
thanks for your reply

---

### Post by MarjaE on 2011-10-17
I just switched from Ubuntu 11.04 to Xubuntu 11.10 and I can't get Thunderbird to import from my backup of my Evolution settings.

---

### Post by MarjaE on 2011-10-17
And the documentation here: [http://support.mozillamessaging.com/en-US/kb/switching-thunderbird?s=import&as=s](http://support.mozillamessaging.com/en-US/kb/switching-thunderbird?s=import&as=s) doesn't match what I'm seeing in my Evolution backup archive.

---

### Post by Buster95 on 2011-10-17
I also attempted the conversion from Evolution to Thunderbird following the "Switching from Evolution" guide on the Thunderbird site.

I found the files in ~/.local/share/evolution/mail/local and copied just one of my stored mail folders in accordance with the instructions (to test the process - I'm a bit wary).

I pasted it in ~/.thunderbird/53qkey89.default/Mail/Local Folders, which, although slightly different to the file name in the guide, is what my Thunderbird file seems to be named.

I checked that the paste worked - it did.

I then started up Thunderbird hoping to see my copied folder staring back at me in all its glory - but it wasn't!

I'm now a bit lost. I had also previously backed up my Evolution files before upgrading to 11.10, but have no idea how I might use the backup to gain access to my files in Thunderbird.

Any suggestions on what I should do next, would be welcome.

---

### Post by MarjaE on 2011-10-17
Now Thunderbird has stopped working. It asks if it is to be the default email application - yes - and then disappears. At one point, it seems to have forced Firefox and Thunar to quit too.

---

### Post by haqking on 2011-10-17
you can all install evolution if you prefer it.

there is no requirement to use thunderbird just because it is installed by default.

---

### Post by MarjaE on 2011-10-17
Well, Evolution is moving away from the .mbox format. I've had very bad problems with getting locked into single-application formats, and getting locked into older unsupported software with no way to transfer to any other software, and I switched to Ubuntu and Xubuntu to get away from single-application formats.

---

### Post by haqking on 2011-10-17
> **MarjaE said:**
> Well, Evolution is moving away from the .mbox format. I've had very bad problems with getting locked into single-application formats, and getting locked into older unsupported software with no way to transfer to any other software, and I switched to Ubuntu and Xubuntu to get away from single-application formats.

you can import and export as a .tar.gz as always.

it is 3.20 in 11.10 currently and still supports mbox

---

### Post by MarjaE on 2011-10-17
> **haqking said:**
> you can import and export as a .tar.gz as always.

it is 3.20 in 11.10 currently and still supports mbox

Thunderbird will not import. At this point, it won't do anything; it's become a virtual brick.

---

### Post by haqking on 2011-10-17
> **MarjaE said:**
> Thunderbird will not import. At this point, it won't do anything; it's become a virtual brick.

I am not talking about thunderbird.

Everyone in this thread is asking about exporting to thunderbird from evolution.

However what i am saying is you dont have to, you can remove thunderbird and install evolution if you wish and then restore from your previous backup.

It is all choice, no requirement to use thunderbird thats what i mean

Evolutions supports mbox and tar.gz as well as import from csv if you so desire.

---

### Post by Carborundum on 2011-10-17
> **MarjaE said:**
> Thunderbird will not import. At this point, it won't do anything; it's become a virtual brick.
Try
```
sudo apt-get purge thunderbird; apt-get install thunderbird
```

---

### Post by MarjaE on 2011-10-17
Well, I used the software center to remove and reinstall, but Thunderbird [u]still[/s] crashes when I attempt to start it.

---

### Post by Carborundum on 2011-10-17
> **MarjaE said:**
> Well, I used the software center to remove and reinstall, but Thunderbird [u]still[/s] crashes when I attempt to start it.
Uninstalling through Software Center is equivalent to 'apt-get remove', which doesn't remove configuration files. Try it with 'purge'.

---

### Post by MarjaE on 2011-10-17
> **Carborundum said:**
> Uninstalling through Software Center is equivalent to 'apt-get remove', which doesn't remove configuration files. Try it with 'purge'.

Okay, thanks. I now have a working copy again; now to figure out how to import from Evolution without breaking Thunderbird.

---

### Post by MarjaE on 2011-10-17
I got them over there... got Thunderbird to run... but Thunderbird will not read the mailboxes. I'm going to have to wait until it can actually import mailboxes before I can use Thunderbird.

---

### Post by fritz269 on 2011-10-17
When I upgraded, Evolution was still installed. I had to uninstall it. So you should still be able to use evolution.

---

### Post by MarjaE on 2011-10-17
> **fritz269 said:**
> When I upgraded, Evolution was still installed. I had to uninstall it. So you should still be able to use evolution.

When I installed, Evolution was not included. I had to reinstall it. I finally unistalled Thunderbird because it will not import from Evolution. And because the official instructions on the Mozilla site can break Thunderbird. It should not be included at installation until it is at least minimally able to import from the other common Ubuntu mail software, and from the backups thereof without quitting or crashing the file manager.

---

### Post by fritz269 on 2011-10-17
Oh, you musta done a clean install. I did an upgrade

---

### Post by Buster95 on 2011-10-17
> **haqking said:**
> you can all install evolution if you prefer it.

there is no requirement to use thunderbird just because it is installed by default.

I chose to transition to Thunderbird because, after using Evolution for a while, I formed the view that it was "too much club" for my particular game.

Canonicals change of recommended client to Thunderbird was only a factor to the extent that (perhaps naively), I expected that when there is a change from one recommended email client to another, there would also be a mechanism provided to support the necessary migration of mail and folders from the old to the new client.

I will probably continue to use Evolution NOT because I prefer it, but because I cannot transition away from it and still maintain my records.

Unless, of course, some bright spark on this forum can guide me through it.

---

### Post by MarjaE on 2011-10-17
> **Buster95 said:**
> I expected that when there is a change from one recommended email client to another, there would also be a mechanism provided to support the necessary migration of mail and folders from the old to the new client.

Word.

---

### Post by haqking on 2011-10-18
[http://www.ubuntugeek.com/how-to-export-your-mails-from-evolution-to-thunderbird.html](http://www.ubuntugeek.com/how-to-export-your-mails-from-evolution-to-thunderbird.html)

[http://ubuntuforums.org/showthread.php?t=1790177](http://ubuntuforums.org/showthread.php?t=1790177)

[https://help.ubuntu.com/community/MigrateEvolutionToThunderbird](https://help.ubuntu.com/community/MigrateEvolutionToThunderbird)

---

