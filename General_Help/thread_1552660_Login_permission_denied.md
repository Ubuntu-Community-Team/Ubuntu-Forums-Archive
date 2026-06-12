---
title: "Login permission denied"
date: 2010-08-13
forum: General Help
---

### Post by kartikdadwal on 2010-08-13
Hi all,

I was working on ubuntu and I closed my laptop screen for a while. When I opened it, it was blacked out and I could just see the cursor moving ( I thought it had gone to hibernate or something).  I switched off my laptop and then powered it back on.

Now, when I reached the user login screen where I enter my password and I click on my name, It says "Permission denied" and doesn't even ask for the password:(.

I clicked on "other" and entered my user name. It says "Permission denied" again!! :(:(.
I switched off and on my laptop but no use.

I know I can press alt+ctrl+esc and reach a command prompt. I tried entering my user name and password but nothing happens. I don't know what else can I do on that prompt.

This happened to my earlier too, then I formatted my laptop. But I can't do it every time. There has to be some solution!!.

Info:
Laptop: DELL Inspiron 1525
ubuntu: 9.10 Karmic koala 
Only one user that's me "Kartik"

PLEASE, help me solve this issue. I am stuck and can't do anything.

Thank you so much.

Kartik

---

### Post by labinnsw on 2010-08-15
[Try 1 of these results]("http://www.google.com.au/search?hl=en&as_q=How+to+recover+Ubuntu+password&as_epq=&as_oq=&as_eq=&num=10&lr=&as_filetype=&ft=i&as_sitesearch=&as_qdr=all&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images")

---

### Post by amac777 on 2010-08-15
From your descrption, it seems that either closing your laptop screen or powering your laptop off when the screen is black is causing data corruption. Does this happen every time you close the screen? 

I would try the above recommended  to boot into the recovery mode and look around to see if you can see any problems and to reset your user's password just in case. Also perhaps see if you can read the log file to see why the permission denied is coming up before you even have a chance to type a password:

```
less /var/log/auth.log
```

Scroll to the bottom and then see what it says about your attempts to login. 

If you can't boot from the recovery mode, perhaps try a live CD to get access to your logs.

But definately avoid closing the laptop screen until you figure out this problem.

Also avoid shutting of the computer without doing a problem shutdown. There are some command sequences you can enter to do a proper shutdown even when your computer is crashed:

[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

Scroll down to the "Raising Elephants" mnemonic device" to see how you can shutdown or reboot your computer when it's crashed. This will hopefully prevent data corruption.

---

### Post by kartikdadwal on 2010-08-15
Hi Labinnsw and Amac777,

I really appreciate your replies and help.

I performed the steps for password recovery. But it didn't help. I get these messages:
# passwd USERNAME
passwd: Permission denied

 Then I tried:
# su
su : permission denied.


All these above steps will help me recover or reset my password. But, I haven't forgotten my password and these steps are not working because there is some other problem. 

I digged deep and I figured out what is causing the problem. It is:

1)I had installed openvpn server on my laptop from: [http://openvpn.net/](http://openvpn.net/) using the HOWTO steps give on the website: [http://openvpn.net/index.php/open-source/documentation/howto.html](http://openvpn.net/index.php/open-source/documentation/howto.html)

NOTE : I did all the steps in "su" mode and openvpn worked perfectly!!

2) Now, I wanted to add extra authentication so I planned to add Pluggable Authentication Mechanism (PAM).

As a part of using PAM, I created "openvpn-auth-pam.so" which is a plugin and it was created in openvpn/plugin/auth-pam directory.

Immediately after creating this plugin, I faced these problems:
a) As I typed:
# su 
su: Permission denied

I could not login in "su" mode.

b) When I powered off or hibernate , etc and log back in and click on my username, without even asking for a password, it straight away says "Permission denied". 
I formated my laptop as I couldn't login. I performed these same steps and I ran into this problem again. I am formatting my laptop ever since and can't get pass this step!!.

I strongly feel that this "openvpn-auth-pam.so" plugin is causing this problem but I havn't got it fixed.

Current status:
I am stuck on the login screen (want to solve this issue and don't want to format again!)
ubuntu version:    9.10 (Karmic Koala)
openvpn version:  openvpn-2.0.9 (downloaded from: [http://openvpn.net/index.php/open-source/downloads.html](http://openvpn.net/index.php/open-source/downloads.html))

Please, help me solve this issue.

Let me know if you need any more information.

Kartik

---

### Post by amac777 on 2010-08-15
Okay, yes from your new description, I believe you are correct - the problem is PAM is now incorrectly configured. If all you did was create the openvpn-auth-pam.so and then this problem started, I would restart in recovery mode (the same technique you did to try reseting your password) and delete openvpn-auth-pam.so. If you made other changes to PAM, perhaps try undoing all the changes if possible.

If you can't get it working after you undo your changes and if no one else replied to this thread, I would suggest making a new thread with a subject such as "how can i reinstall pam" and describe what you did. I'm not exactly sure how to reset PAM back to its default settings.

---

### Post by kartikdadwal on 2010-08-18
Hi,

I managed to solve the problem..

Actually this problem of "Permission denied" occured the moment I installed PAM from the ubuntu repository.

What happened was, PAM was already in installed in my system (checked it through 'synaptic packet manager'). And I download ".tar.gz" PAM file from the ubuntu repository and compiled it and installed it using:
./configure
make
make install
This caused the problem!! PAM is very dangerous to play with as if it goes haywire, would lock you out of your system and this damage is irreversable; so I had to format my laptopo every time it happaned. 

In order to solve it, this time after formatting my laptop, I checked PAM through synaptic manager and just upgarded it to the latest version and after that I created openvpn-auth-pam.so plugin. It worked smoothly!

Thank you so much for your help.

Kartik

p.s: Now I have add "FreeRadius" to my openvpn using PAM :)

---

