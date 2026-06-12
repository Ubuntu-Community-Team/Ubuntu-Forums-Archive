---
title: "thunderbird"
date: 2012-05-13
forum: General Help
---

### Post by fredRansom on 2012-05-13
I have 4 e-mail addresses. Thunderbird can connect to 3 of them on Windows, however on Ubuntu it cannot connect to any of them. What gives?

---

### Post by 73ckn797 on 2012-05-13
Need a bit more information than what you have said. Are settings correct for each address? What version Ubuntu are you using? Many other questions but little info to help with.

---

### Post by Rodney9 on 2012-05-13
These may help --

[http://kb.mozillazine.org/Multiple_SMTP_servers_-_Thunderbird](http://kb.mozillazine.org/Multiple_SMTP_servers_-_Thunderbird)

[http://www.makeuseof.com/tag/how-to-set-up-mozilla-thunderbird-3-multiple-email/](http://www.makeuseof.com/tag/how-to-set-up-mozilla-thunderbird-3-multiple-email/)

---

### Post by fredRansom on 2012-05-16
I have 12.04. The settings for both MS Windows Thunderbird and Ubuntu Thunderbird are exactly the same. Thunderbird works for 3 addresses on MS Windows, but for no address at all on Ubunto. If it would work for just 1 address I'd use it. Otherwise I'll just dump it.

---

### Post by pqwoerituytrueiwoq on 2012-05-16
did you upgrade a from a older version or Thunderbird when you went to 12.04
i have all 4 of my email accounts in thunderbird on ubuntu no problem

---

### Post by traditionalist on 2012-05-16
> **fredRansom said:**
> I have 12.04. The settings for both MS Windows Thunderbird and Ubuntu Thunderbird are exactly the same. Thunderbird works for 3 addresses on MS Windows, but for no address at all on Ubunto. If it would work for just 1 address I'd use it. Otherwise I'll just dump it.

It works fine for me on 12.04.  What settings are you using?

---

### Post by traditionalist on 2012-05-16
If you want to use the same addresses in your Ubuntu thunderbird, then  copy the profile from your windows thunderbird. You can use mozbackup for  that;

**[http://mozbackup.jasnapaka.com/](http://mozbackup.jasnapaka.com/)**

Make a FULL backup with that.

The files that mozback creates are just zip files with a different extension.

Copy  the profile you backed up to your ubuntu machine change the file  extension to .zip  and extract it, then  copy the contents to ;

/home/your-name/.thunderbird/xyz.default

You  then have the identical settings and all your data,  mails, etc,  on  your ubuntu machine.  You must start thunderbird at least once for it to  create a profile. The profiles are given random names. You just overwrite the default profile it creates with your existing profile which you copied from your windows machine.

---

### Post by traditionalist on 2012-05-16
The same trick works for Firefox as well if you want to keep your settings extensions etc, 

The default folder in firefox is;

/home/your-name/.mozilla/firefox/11jfidkj.default

---

### Post by rickwright67 on 2012-05-18
I have had the same experience as the OP. Fresh install of Xubuntu 12.04. Therefore fresh install of Thunderbird 12.01. Started it up. Tried to create email account (Gmail) just as I have done dozens of times on my other computers. 

Did not work. Could not authenticate the server settings. Tried manual. Copies settings from Gmail help. Nope. Nothing worked. Strange - I've done this many times so can't imagine what's different or wrong.

The one and only thing that *did* work was using Mozbackup to copy settings from a Windows XP machine where Thunderbird was working just fine. (Thanks for the post recommending that solution.) *Now* Thunderbird 12.01 in Xubuntu 12.04 works. But for some reason it just refused to create afresh a Gmail account.

I would suggest something's not quite right with the version of Thunderbird that's part of Xubuntu/Ubuntu 12.04. And the issue isn't how many accounts, the issue is creating even the first. Not everyone can use a Windows machine to backup a working Thunderbird profile.

Update = Had similar trouble setting up KMail. Complains about the server certificate.

---

### Post by Netraam on 2012-05-19
> **rickwright67 said:**
> I have had the same experience as the OP. Fresh install of Xubuntu 12.04. Therefore fresh install of Thunderbird 12.01. Started it up. Tried to create email account (Gmail) just as I have done dozens of times on my other computers. 

Did not work. Could not authenticate the server settings. Tried manual. Copies settings from Gmail help. Nope. Nothing worked. Strange - I've done this many times so can't imagine what's different or wrong.

The one and only thing that *did* work was using Mozbackup to copy settings from a Windows XP machine where Thunderbird was working just fine. (Thanks for the post recommending that solution.) *Now* Thunderbird 12.01 in Xubuntu 12.04 works. But for some reason it just refused to create afresh a Gmail account.

I would suggest something's not quite right with the version of Thunderbird that's part of Xubuntu/Ubuntu 12.04. And the issue isn't how many accounts, the issue is creating even the first. Not everyone can use a Windows machine to backup a working Thunderbird profile.

I have exactly the same issue... sadly cant use Mozbackup atm as I only have the one machine and I did a complete clean upgrade to 12.04 (no dual boot with Windows). Any advice on how to correct this issue would be much appreciated...

---

### Post by Ocelot92 on 2012-05-20
Same problem for me. The same happened with Windows. I think it's a problem with gmail/Thunderbird, not Ubuntu. But here the work around: just set manually the configuration.  When you've done click on create account that will be enable. Thunderbird'll check the password and it'll create the account. It's work at least for me.

---

### Post by jfransom on 2012-05-20
I have had to change my account from fredRansom to this one because fredRansom stopped working. The new password I was sent didn't work either even with copy and paste.

I dumped thunderbird and deleted the .thunderbird directory. No point keeping something that doesn't work. For that matter, the Windows version doesn't work very well either.

---

### Post by 73ckn797 on 2012-05-20
I have always copied the T-bird and Firefox folders from /home as a precaution. If you use a separate /home partition, T-bird & FF will be picked up in the first start-up of either. Never had any problems. I have been able to do the same from Windows. Copy the T-bird/FF folders then drop them into the /home on new install.

---

### Post by Easy Limits on 2012-05-20
Depending on your email servers in which you get email from you will want to check to make sure you are getting the right port numbers.  The new version of Thunderbird does not get them right by default.  For instance, port 110 for incoming mail and port 25 for outgoing mail.

---

### Post by alforddm on 2012-05-22
I'm having this problem as well, with a clean install of Ubuntu 12.04  

Settings are correct it simply won't connect.  I've tried with two different email accounts both of which work great with windows and thunderbird.


I did finally get this to work.  A few things that weren't completely obvious to me...

1.) You have to enter the complete imap.googlemail.com in the box.  Just selecting imap or pop doesn't cut it.  
2.) Log out of your gmail account.  Not sure if this really helped or not but it can't hurt.
3.) Keep trying. I tried the same settings multiple times before they were finally accepted.

---

### Post by ammofreak on 2012-05-22
Hi ):P
Since everyone swears their settings for Thunderbird e-mail accounts are proper, then I will not waste your time regarding manual setup & non-standard ports & security settings. I would next try:

1) Make sure you are not in off-line mode. Go to File, Offline, and make sure Work Offline is NOT checked.

2) "If you use to be able to send before upgrading Thunderbird and it silently fails, check whether an add-on that hooks into the send process such as Check and Send was disabled. Either temporarily disable that add-on and see if the problem goes away or disable the version check per updating add-ons and enable the add-on."

3) "If you have some sort of anti-spam add-on that has a toolbar such as SPAMfighter check that the toolbar didn't disappear. Sometimes when that occurs it prevents Thunderbird from sending. Depending upon the add-on you may need to uninstall it or upgrade it."

Bye for now...:)

---

