---
title: "Suspicious activity"
date: 2012-02-06
forum: General Help
---

### Post by andrey_ on 2012-02-06
Hello there, 

Chromium browser is opening at its own.... I'm using Ubuntu 11.04..

Any suggestion please?

---

### Post by aasdfasdfg on 2012-02-06
Do you mean that the Chrome browser is auto-launching?

Are you trying to change your default browser? This can be done in System Settings -> System Info -> Default Applications

---

### Post by Frogs Hair on 2012-02-06
If it is starting when you first start the computer , check to see that it has not been added to startup applications . I have never experienced an application starting on its own that was not prompted by the user in some way . 

The nice thing about Linux is that nothing can be installed by its self .  If there is an application causing this it was installed with a password . There could be a problem with the Chromium installation . Removing the configuration file home/hidden folders and reinstalling may solve the problem .

If a link , say in the software center is used the default browser will open even if more than one browser is installed .

---

### Post by andrey_ on 2012-02-06
> **Frogs Hair said:**
> If it is starting when you first start the computer , check to see that it has not been added to startup applications . I have never experienced an application starting on its own that was not prompted by the user in some way . 

The nice thing about Linux is that nothing can be installed by its self .  If there is an application causing this it was installed with a password . There could be a problem with the Chromium installation . Removing the configuration file home/hidden folders and reinstalling may solve the problem .

If a link , say in the software center is used the default browser will open even if more than one browser is installed .

No, I did not set it to run on startup, Chrome is starting completely on its own, this is third time it happens, first two times I thought I clicked somewhere by mistake, but this time I'm sure it started completely on its own, prior to that a tab with my banking link opened in the same scenario .... not only that,
in Lotus Note ( email client) a new tab of Inbox opened on it's own (2 times yet).
Yesterday I was opening my web mail on AOL and No-script suddenly displayed a strange message, after searching the Internet I found out that it means there are some hidden buttons on the page and it used by hackers to spy on your Mic or Cam for example. I found that strange when opening such secured web mail like AOL.

I'm ready to provide any reporting result required to help me out.

Thanks in advance

---

### Post by Dangertux on 2012-02-06
> **andrey_ said:**
> No, I did not set it to run on startup, Chrome is starting completely on its own, this is third time it happens, first two times I thought I clicked somewhere by mistake, but this time I'm sure it started completely on its own, prior to that a tab with my banking link opened in the same scenario .... not only that,
in Lotus Note ( email client) a new tab of Inbox opened on it's own (2 times yet).
Yesterday I was opening my web mail on AOL and No-script suddenly displayed a strange message, after searching the Internet I found out that it means there are some hidden buttons on the page and it used by hackers to spy on your Mic or Cam for example. I found that strange when opening such secured web mail like AOL.

I'm ready to provide any reporting result required to help me out.

Thanks in advance

Did the NoScript warning say XSS? (not that it matters I don't think this is a compromise)

Also, this really sounds like hardware malfunction (perhaps a rogue touchpad driver or a bad mouse?). If you were being "spyed on" it would be highly unlikely the attacker would want to reveal their existence, and there would be nothing making them do so. A reverse VNC connection could be established and you wouldn't notice they were doing anything or they could harvest sequential screenshots or even video of your activities, they wouldn't have to "open a tab" to see what you were doing.

Additionally they could dump all of your saved browser passwords and do it locally so I really don't think this is the sign of a compromise.

Hope this helps.

---

### Post by andrey_ on 2012-02-06
> **Dangertux said:**
> Did the NoScript warning say XSS? (not that it matters I don't think this is a compromise)

Also, this really sounds like hardware malfunction (perhaps a rogue touchpad driver or a bad mouse?). If you were being "spyed on" it would be highly unlikely the attacker would want to reveal their existence, and there would be nothing making them do so. A reverse VNC connection could be established and you wouldn't notice they were doing anything or they could harvest sequential screenshots or even video of your activities, they wouldn't have to "open a tab" to see what you were doing.

Additionally they could dump all of your saved browser passwords and do it locally so I really don't think this is the sign of a compromise.

Hope this helps.

I Googled XXS and found the NoScript warning I saw, it was "ClearClick Warning": NoSrcipt intercepted a mouse or keyboard interaction with a partially hidden element

---

### Post by Dangertux on 2012-02-06
> **andrey_ said:**
> I Googled XXS and found the NoScript warning I saw, it was "ClearClick Warning": NoSrcipt intercepted a mouse or keyboard interaction with a partially hidden element

That's a form of click jacking. Basically say you want to click on the word CLICK , there will be an invisible element over it containing a link to malicious code, when you try to click CLICK you actually click the element. This is fairly commonly seen in HTML email service providers (like AOL)

I still don't think it's evidence of a compromise in and of itself.

Hope this helps.

---

### Post by andrey_ on 2012-02-06
> **Dangertux said:**
> That's a form of click jacking. Basically say you want to click on the word CLICK , there will be an invisible element over it containing a link to malicious code, when you try to click CLICK you actually click the element. This is fairly commonly seen in HTML email service providers (like AOL)

I still don't think it's evidence of a compromise in and of itself.

Hope this helps.

Thank you Dangertux, 
I'm new to Linux and I like it a lot more than Windows OS because of its relative security, but I found it difficult to check whether you system is compromised, specially with such tools like chkrootkit and Rkhunter because of false positive and some other things making it easier for you to consider any genuine threat as a simple false positive or a program bug etc...nothing definite
Are there other programs or simple guide to handle the OS security in effective and definite way? to get the most of Linux as a secure system instead of looking at it as a complete black box

---

### Post by claracc on 2012-02-07
You can find useful security information in the security subforum: [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

I would begin from the stickys.

---

### Post by HiImTye on 2012-02-07
what is the address that Chrome is attempting to load when it starts up, without your want?

---

### Post by 3rdalbum on 2012-02-07
> **andrey_ said:**
> I found it difficult to check whether you system is compromised, specially with such tools like chkrootkit and Rkhunter because of false positive and some other things making it easier for you to consider any genuine threat as a simple false positive or a program bug etc...nothing definite
Are there other programs or simple guide to handle the OS security in effective and definite way? to get the most of Linux as a secure system instead of looking at it as a complete black box

Well, it's difficult. There's no viruses for Linux, so you can't really have an anti-virus.

Rootkits are tougher than viruses. They are a targetted attack - a human attacker must tailor the attack to your system. A rootkit is designed not to be detected, and it does this by installing modified versions of 'top' and 'ps' that will not show any suspicious programs running. Of course, it will also install a modified version of any anti-rootkit programs that will pretend not to see a rootkit.

The good news is that, unless you are running server services on your system, it's almost impossible for you to have a rootkit either.

If there were lots of viruses and trojans on Linux then I'm sure there would be more comprehensive, user-friendly security packages. But the typical Linux desktop system is so difficult to find a way into, that the threat from attackers is negligible.

Also, in the last ten years there have been something like a million pieces of malware released (mostly on Windows). As far as I know, not a single one has done anything so obvious and so meaningless as open a blank browser window or an e-mail inbox window. Your symptoms not only sound like a keyboard problem, but sound like they are NOT a virus or any other piece of malware. It's simply not what malware does these days.

---

### Post by andrey_ on 2012-02-07
> **HiImTye said:**
> what is the address that Chrome is attempting to load when it starts up, without your want?

Hi, 

There is no address at all, it's blank page.

---

### Post by andrey_ on 2012-02-07
> **claracc said:**
> You can find useful security information in the security subforum: [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

I would begin from the stickys.

Thanks for the link.

---

### Post by andrey_ on 2012-02-07
> **3rdalbum said:**
> Well, it's difficult. There's no viruses for Linux, so you can't really have an anti-virus.

Rootkits are tougher than viruses. They are a targetted attack - a human attacker must tailor the attack to your system. A rootkit is designed not to be detected, and it does this by installing modified versions of 'top' and 'ps' that will not show any suspicious programs running. Of course, it will also install a modified version of any anti-rootkit programs that will pretend not to see a rootkit.

The good news is that, unless you are running server services on your system, it's almost impossible for you to have a rootkit either.

If there were lots of viruses and trojans on Linux then I'm sure there would be more comprehensive, user-friendly security packages. But the typical Linux desktop system is so difficult to find a way into, that the threat from attackers is negligible.

Also, in the last ten years there have been something like a million pieces of malware released (mostly on Windows). As far as I know, not a single one has done anything so obvious and so meaningless as open a blank browser window or an e-mail inbox window. Your symptoms not only sound like a keyboard problem, but sound like they are NOT a virus or any other piece of malware. It's simply not what malware does these days.

Thanks for your reply, 
Noted, now on I'll simply ignore any future similar issues as long as my keyboard is functioning, cause in Linux there are no viruses or Trojans  is designed to simply open a web browser.
Linux as OS turned out to be much simpler than I initially thought ;)

Edit: Chrome is not my default browser I'm using Firefox, but its shortcut is on the taskbar, I tried to run it by pressing <Super+6> and a default google.com search page opened, meanwhile when it opened on its own the page was simply blank

---

### Post by hawthornso23 on 2012-02-07
Remote desktop services could potentially do what you describe. Ubuntu has a VNC (remote desktop) server called vino installed by default. Supposedly in its default configuration it is locked down and secure. However if you didn't even know that you had a remote desktop server installed on your machine and can't imagine ever needing to login into your machine remotely over the internet, (corporate help desks like to have this ability which is probably why it is installed by default) then I recommend you consider uninstalling vino. Note that this will leave the remote desktop client (vinagre) installed so it will not change your ability to remotely log into other machines. It will simply remove the remote possibility that people on other machines might be using VNC via some misconfiguration or bug in vino to remotely log into yours. 

I also hope that you have a good password. Even if you run a single user desktop and have it set to always log you in automatically you need to have a good password. That is because the password also controls access to your machine if people try to get into it remotelyusing some kind of service like the vino VNC service mentioned above.
 
Good security involves knowing what services you have running, and only running those services you actually need. I also recommend getting rid of the guest session which lightdm introduced into Oneiric for similar reasons. Once again this should be secure in its default configuration, but it opens up another potential window into your machine, so  if you don't need it get rid of it. Bricked up windows are more secure than closed ones. Google for "Oneiric remove  guest session" to find out how to do this.

And finally - install gufw and turn on your firewall.

You don't need to worry about viruses when running ubuntu. But you shouldn't ignore security.

---

### Post by andrey_ on 2012-02-08
> **hawthornso23 said:**
> Remote desktop services could potentially do what you describe. Ubuntu has a VNC (remote desktop) server called vino installed by default. Supposedly in its default configuration it is locked down and secure. However if you didn't even know that you had a remote desktop server installed on your machine and can't imagine ever needing to login into your machine remotely over the internet, (corporate help desks like to have this ability which is probably why it is installed by default) then I recommend you consider uninstalling vino. Note that this will leave the remote desktop client (vinagre) installed so it will not change your ability to remotely log into other machines. It will simply remove the remote possibility that people on other machines might be using VNC via some misconfiguration or bug in vino to remotely log into yours. 

I also hope that you have a good password. Even if you run a single user desktop and have it set to always log you in automatically you need to have a good password. That is because the password also controls access to your machine if people try to get into it remotelyusing some kind of service like the vino VNC service mentioned above.
 
Good security involves knowing what services you have running, and only running those services you actually need. I also recommend getting rid of the guest session which lightdm introduced into Oneiric for similar reasons. Once again this should be secure in its default configuration, but it opens up another potential window into your machine, so  if you don't need it get rid of it. Bricked up windows are more secure than closed ones. Google for "Oneiric remove  guest session" to find out how to do this.

And finally - install gufw and turn on your firewall.

You don't need to worry about viruses when running ubuntu. But you shouldn't ignore security.

Thank you [hawthornso23]("http://ubuntuforums.org/member.php?u=867217").

---

