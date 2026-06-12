---
title: "updating programs"
date: 2006-02-05
forum: General Help
---

### Post by bountonw on 2006-02-05
I am only a few hours old in Linux.  Monday morning I am going to have to be able to use the office computer that I just switched over.  I need to type documents in Thai and would also like to update firefox.  How do I update openoffice, firefox or any other program.

If there is a good place to read up on this, I wouldn't mind reading.

Thank you.

---

### Post by Herman on 2006-02-05
> I am only a few hours old in Linux. Monday morning I am going to have to be able to use the office computer that I just switched over. I need to type documents in Thai and would also like to update firefox. How do I update openoffice, firefox or any other program.
If there is a good place to read up on this, I wouldn't mind reading. Welcome, bountonw, [A PDF Ubuntu Beginner's Guide  ]("http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf")by A.Y. Siu might be the best reading you can do if you are just beginning with Ubuntu. That should help you to be able to do some things pretty fast. In particular, I think you may be interested in beginning at page 22 of that guide, as that is where you should find the answer to your question of how to enable the extra repositories and updating everything. I recommend A.Y.Siu's other links as well:
[Basic ways to install software ]("http://www.psychocats.net/linux/installingsoftware.php")
[Enabling extra repositories]("http://www.psychocats.net/linux/sources.php")
[Editing Files that Belong to Root]("http://www.psychocats.net/linux/permissions.php")
[Mounting Windows Partitions]("http://www.psychocats.net/linux/mountwindows.php")
  [Great Linux Bookmarks]("http://www.psychocats.net/linux/resources.html")

If you want the latest upgrades for Open Office .org 2.0. I know that [automatix ]("http://ubuntuforums.org/showthread.php?t=66563")installs that along with lots of other good things.

My own link under here (lower left) is very elementary and is for installing and also helping people get started immediately after an install. A.Y.Siu's links are more advanced help. I think they are the ones you need. If you just need to find out how to get your printer working my left-hand link below might help. :D (Herman)

---

### Post by lol on 2006-02-05
We will need more information in order to help you...

There could be several ways to update programs, depending on:
- whether or not you have root access on the computer (I am not sure I understood correctly, but by "office computer", you mean a computer provided to you at work?).
- which distribution is installed on the computer.
- which version of the software you are looking for (is it in the Breezy repositories, or maybe available in Dapper or even a Debian distro).
- do you mind manually installing software in /usr/local or would you rather use only deb packages?
- etc.

The current version of Firefox in Breezy is 1.0.7, if you want to upgrade it to the version 1.5, try looking for "firefox 1.5" in the forums, I am pretty sure there is already a lot of howto explaining how to do so.

OpenOffice is currently 2.0, so unless you really need the version 2.0.1, there is no need to update it (still assuming you are running Breezy).

For Thai, I don't know if it requires a special Input Method. If this is the case, then I strongly suggest using SCIM, and to update it to version 1.4. The current version on Breezy is quite buggy.

---

### Post by bountonw on 2006-02-05
I am using ubuntu 5.10.

I am the boss at work and have root access to the computer that I have installed linux on.

Now that I know where &#3784;&#3762;the beginners guide is, I will read that.

I loaded Thai language and can write Thai in this post &#3649;&#3605;&#3656;&#3585;&#3655;&#3618;&#3633;&#3591;&#3652;&#3617;&#3656;&#3588;&#3619;&#3656;&#3629;&#3591;

But I can't for the life of me type Thai in openoffice.  There are no Thai fonts listed and I don't know how to install, but obviously my computer has Thai fonts or I couldn't type in Thai here.  (I also need to type in Lao.)

I don't mind manually installing software, but I need to read more so that I know what I am doing.  I have been reading a lot, but it is still too knew for me and will probably take me a little while. Thank you both for pointing things out for me.  After reading and fiddling a little more if I still have questions I will post again.

---

### Post by DaMasta on 2006-02-05
Have you tried **sudo apt-get install openoffice.org-l10n-th**?

---

### Post by DaMasta on 2006-02-05
Also, you'll need to add the universe repository for the above to work.

---

