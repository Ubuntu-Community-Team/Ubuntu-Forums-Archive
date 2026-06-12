---
title: "Ubuntu Blanks the Screen after a few Minutes"
date: 2011-06-26
forum: General Help
---

### Post by p3aul on 2011-06-26
Hi!
I'm a newbieto linux and Ubuntu and I have a problem that I've been searching for the solution all day. When I leave the computer for a few minutes, it goes to sleep and I have a black screen. touching the mouse wakes it up but then I have to log back on with my password. I would prefer that it not do that and the solution was simple in windows ie "Not to powerdown anything". I can't find that particular option on Ubuntu 11.04. 

Also, I would prefer not having to type in a password either. There are no other users on my computer and I have no need to keep in "Locked down". I guess I could live with it if I have to but I sure would like to get the first one fixed.
Thanks,
Paul

---

### Post by yetiman64 on 2011-06-27
> ...When I leave the computer for a few  minutes, it goes to sleep and I have a black screen...That is the screensaver only (not powering down as such), go to the shutdown menu (top right of the screen) and select "system settings", then choose "screensaver" in the opened window. You can either turn it off or change it here, also de-ticking the 2nd option here will stop the screen from being locked on returning from the screensaver. You can also check your power management settings from the system settings window if needed.

Information regarding turning off passwords is not supported on this forum (threads in which that is asked for are sometimes locked), search the internet for that info. Google is your friend in that case. I tend to advise against such actions, particularly for new starters.

Regards, yetiman64

---

### Post by varunendra on 2011-06-27
> **yetiman64 said:**
> Information regarding turning off passwords is not supported on this forum (threads in which that is asked for are sometimes locked)
Really?? I didn't know that! In fact I was just about to tell him how. After all, it is a deliberately provided feature. Any effort to change those settings require authentication password anyway, so no unauthorized user can access those settings if s/he doesn't already knows that password. So why not?

Besides, option for auto login is also provided during installation process, for which there are tons of guides in and outside this forum. What if a newbie enables it during installation phase just to see what happens and then wants to turn it off?

I hope you understand my concern. Please explain it for me why this is so restricted in the forums.

---

### Post by p3aul on 2011-06-27
Thank you! I was about to pull all my hair out(till I remembered that I'm bald!) Everywhere I looked everyone was saying go to Power -> system settings without telling anyone how to get there! Thank you for explaing exactly where to go. It was simple after that.

Regarding the password thing, I know everyone on the net is paranoid about passwords. The only time I had a problem was when I inadvertently downloaded a keylogger and my debit card was compromised. I quickly moved all my money over to savings and called the bank. They restored the $1.23 that I lost. Of course this was MS Windows.  I'll just suffer, it's a small price to pay for a safer operating system. 
Paul=D>

---

### Post by yetiman64 on 2011-06-27
> **varunendra said:**
> Really?? I didn't know that! In fact I was just about to tell him how....[[COLOR=Blue]--here--[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10952716&postcount=10") is an example from about a week ago. Click on the title in the top right to see the full thread. 

Canonical provide the servers for this site as far as I understand it, and it is Canonical's security model this site supports. Turning off passwords is up to the user but goes against that model, posting the information here when there are plenty of blogs etc elsewhere on the net showing how makes it unnecessary to do here.

Edit: autologin feature does not stop password being required to elevate privileges during use even if enabled, I assumed the OP referred to all password prompts.

@ OP, Linux in general has effectively no virus / malware problems because of the use of passwords and file/folder ownership/permissions. Usually after a set up is completed the password prompts will lessen greatly. Pays to be a bit patient with them.

Your password being asked for is an indication the next action will be running as root. Root privileges in Linux are very powerful and if used wrongly (eg by a piece of malware when you have no password for it to get past) can destroy your install / data.
[B]
Edit 2[/B]: OP on re-reading your first post it appears I have read it wrongly, the autologin feature is fine to use as my first edit would suggest. Sorry for the misreading. In system settings look for the login screen settings and authenticate to change them. 

@ [varunendra]("http://ubuntuforums.org/member.php?u=1043629"), your are actually correct that was from my misreading the OPs first post, sorry about that

---

### Post by varunendra on 2011-06-27
Nevermind! Your mistake actually helped adding some very important and useful info to the thread. Thanks to you for the valuable info.

@p3aul,
I think you should now mark the thread as [Solved] (follow my signature to see how).

---

### Post by p3aul on 2011-06-27
Thanks for the additional posts! This cleared up my thinking about passwords and actually made me see the sense of using them. Ubuntu only asks for the the password when it installs something I have initiated and thats fine. 

On my wife's laptop running Vista, it too asks for permission to continue an install. She rarely has problems with malware. On the other hand, I was runing Win 7(which never asks for permission, when a fake anti-virus was installed without my knowledge. All of a sudden this fake anti-virus  shut down my own antivirus, MS Security Essentials, and started scanning(?) my computer turning out a huge list of malware and viri. I tried to shut it off but all of a sudden my screen went blank and the computer was shut down. I don't have the original install disk because Acer doesn't provide one. I can't afford the $200 dollars it would take to purchase another one. Besides, the more I use Ubuntu, the more I like it. I had Photoshop and Coreldraw on my Win 7, but I think Gimp and Inkscape is just as good. 

Before I installed Ubuntu permanently, I tried out Fedora LiveCD. It was almost worthless and hard to understand.

Long live Ubuntu!:D
Paul

---

