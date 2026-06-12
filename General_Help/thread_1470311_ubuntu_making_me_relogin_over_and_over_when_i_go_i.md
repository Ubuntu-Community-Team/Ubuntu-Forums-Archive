---
title: "ubuntu making me relogin over and over when i go into hotmail"
date: 2010-05-02
forum: General Help
---

### Post by spaceblaster on 2010-05-02
I just upgraded to the newest ubuntu.  Everything worked great before but since I upgraded, it asks me to relogin over and over again when I go into hotmail.  I had to use a different computer just to get into my hotmail to verify my new account here so I could ask about this.  It will repeat over and over making me log in but i won't even spend anytime in my email.   Any help would be appreciated.

---

### Post by BrokeMahPC on 2010-05-02
You have to login to hotmail over and over again? or ubuntu? Please describe exactly what happens.

---

### Post by spaceblaster on 2010-05-02
It makes me relogin to ubuntu.  I dont seem to have the problem going to any other sites.  This wasnt a problem before the upgrade.  I will go there login and look at my inbox and with 1-2 seconds the screen goes blank then an ubuntu will have a login screen and i have choices of my name and other.  I choose my name, enter my administrative password and then I am back on.  I have to restart firefox and then when i do it asks if i want to start a fresh one or retrieve the last session.  If i retrieve it repeats within seconds.  Over and Over.  It seems it has to do something to do with the upgrade because this wasn't a problem before.

---

### Post by spaceblaster on 2010-05-02
One thing that seems strange to me is that I don't even have to enter my password when i start up the computer.

---

### Post by BrokeMahPC on 2010-05-02
When you upgraded did you choose a new admin password? If so does entering the old password stop it bringing up the login? Do you have stored passwords for hotmail and have you asked firefox to remember them? There may be a missmatch with old / new passwords trying to access the keyring.

SOLUTION:
-Go to Applications-Accessories-Passwords and Encryption Keys
-Right click on **Passwords:**login
-Select Change Password
-Type your old login password in the "Old Password" field
-Type your new password in both the Password: and Confirm: fields.
-Click OK
-REBOOT

Evolution will now use your new login password to access the keyring.
Any good?
Sorry - just realised you are using Kubuntu - this probably will not work.

---

### Post by zappadragon on 2010-05-02
I am having the same problem but only with a few sites. It has nothing to do with passwords I will be surfing and the screen goes blank and I get logged out of Ubuntu

---

### Post by talent03 on 2010-05-02
Nevermind. I just saw zappadragon having the same issue and thought it was his thread. You should probably check whether or not it may be a video driver issue, if you are on flash intensive sites and making anything crash. Other than that, you probably need to post some log files.

---

### Post by BrokeMahPC on 2010-05-03
Good idea by talent03!
Another question - are you using 64bit ubuntu? Do you have the 64bit flash player from adobe installed. I don't think the flash player from the ubuntu repos works in 64bit.
Try the flash block plugin for firefox - if the problem stops then it must be the flash player.

---

### Post by spaceblaster on 2010-05-03
No I did not choose a new administrative password when I upgraded.  I have passwords remembered in firefox.  I am able to login.  Once I get to my ibox the problem occurs.  I am using ubuntu not kubuntu.  I made the mistake thats why I double posted.  I thought kubuntu was what it was after upgrade but it is 10.04.

---

### Post by spaceblaster on 2010-05-03
Also I didn't think hotmail was very flash intensive. Maybe I am wrong but, I am going to other sites without problems.  Watching video and things liek that with no problems.

---

### Post by spaceblaster on 2010-05-03
I think the problem went away on its own.  I was able to go into my inbox and delete stuff without ubuntu making me relogin.  If it comes back I'll let you all know.

---

### Post by spaceblaster on 2010-05-03
Well it is better but, it did it again once.  Still like to know what is causing it.

---

### Post by spaceblaster on 2010-05-04
Problem has come back pretty regularly with hotmail and once with another site now.

---

### Post by spaceblaster on 2010-05-05
I've gotten the problem on some on other sites now so it's not a Hotmail exclusive problem.

---

### Post by spaceblaster on 2010-05-06
Thanks for the help guys

---

### Post by spaceblaster on 2010-05-09
I fixed the problem by reformatting with ubuntu 10.04 from a boot disk I made off the site.  Before I just upgraded from the old version.  Haven't had the problem since.

---

### Post by pricetech on 2010-05-20
Glad you got it fixed.  I was going to suggest using another browser to see what happens.

I might be flash related since I'm getting prompted to install a plugin when I visit the site using SeaMonkey, though it works without the plugin.

I don't have flash installed by the way.  I just haven't bothered with it this install.

---

### Post by ozstar on 2010-07-06
Hi,

Well I have the login screen come on after the screensaver comes on. 

So if I leave the box alone for 5 minutes I have to login again.  It is driving me nuts!

How can I either set it to a longer time or get rid of it altogether.

Thanks

oz

---

