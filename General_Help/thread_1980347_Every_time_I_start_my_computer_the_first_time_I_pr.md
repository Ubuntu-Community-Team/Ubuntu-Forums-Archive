---
title: "Every time I start my computer the first time I press enter it logs me out"
date: 2012-05-15
forum: General Help
---

### Post by snapdata on 2012-05-15
Hi! When I boot up Ubuntu (SSD) the first time I press enter (numpad or the main return) it logs me out. It doesn't matter where I press it (eg. no window, inside chrome, etc) or when. If I press it before ~15 seconds into the boot, though, my monitor stops receiving input.

Any ideas? This has puzzled me for weeks, I've been trying to get help on IRC but no one knows what's going on. I was hoping you guys could help me debug this!

I'm running 12.04, x86 64-bit

---

### Post by wilee-nilee on 2012-05-15
Does it do this on a live cd, if not then I would consider doing a reinstall, if no one has had an answer yet.

You can also create another account in users but it seems you would not get that far, hard to tell from the description.

---

### Post by snapdata on 2012-05-15
> **wilee-nilee said:**
> Does it do this on a live cd, if not then I would consider doing a reinstall, if no one has had an answer yet.

You can also create another account in users but it seems you would not get that far, hard to tell from the description.

I've reinstalled twice. The same issue reappears after a few restarts (without installing any additional software)

---

### Post by wilee-nilee on 2012-05-15
> **snapdata said:**
> I've reinstalled twice. The same issue  reappears after a few restarts (without installing any additional  software)

Could be a faulty cd, does this happen on the cd?

Do you have any other OS's on the computer to confirm maybe a keyboard problem.

You can also check the md5sum of the cd.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Strange behavior for sure.

---

### Post by roelforg on 2012-05-15
You said ~15s into boot.
Is this before or after logging in?
If before, than it should boot fine.
If after, xorg/gnome/whatever crashes

---

### Post by snapdata on 2012-05-16
> **roelforg said:**
> You said ~15s into boot.
Is this before or after logging in?
If before, than it should boot fine.
If after, xorg/gnome/whatever crashes

I have auto login on.


> **wilee-nilee said:**
> Could be a faulty cd, does this happen on the cd?

Do you have any other OS's on the computer to confirm maybe a keyboard problem.

You can also check the md5sum of the cd.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Strange behavior for sure.

I was dual booting Windows, but not anymore. A corrupted image is doubtful, it was 2 different CDs. I'll check the MD5sum anyway.

---

### Post by wilee-nilee on 2012-05-16
> **snapdata said:**
> I have auto login on.




I was dual booting Windows, but not anymore. A corrupted image is doubtful, it was 2 different CDs. I'll check the MD5sum anyway.

You might try another keyboard even if its a laptop you can plug one in. A rather unusual circumstance for sure,

---

### Post by snapdata on 2012-05-16
> **wilee-nilee said:**
> You might try another keyboard even if its a laptop you can plug one in. A rather unusual circumstance for sure,

Sadly I don't have another keyboard. One moment, I'll check with the onscreen keyboard and report back.

EDIT: Doesn't happen with the on-screen keyboard. [My keyboard has custom keys and is strange]("http://www.amazon.com/Razer-Anansi-MMO-Gaming-Keyboard/dp/B004H1R6JQ"), if I press the keys below space it toggles the trackpad on and off (as if I have one.) 

I've tried with the trackpad setting both on and off by the way, it has no bearing on the log out issue. The keyboard's function keys work fine, I don't see how the newline input could crash xorg/gnome. Very strange indeed.


Triple edit: Just to make sure there wasn't some input weirdness going on, I threw this together:

> john@snapdata:~$ cat newline.pl
$test = <STDIN>;
if($test =~ m/^(\n)$/)
{
	print "\nAs expected\n";
}

-----------------------------------------------------------------------
john@snapdata:~$ perl newline.pl


As expected
john@snapdata:~$ 



---

### Post by snapdata on 2012-05-17
edit: It doesn't occur for one restart after installing updates through the update manager. I've observed this twice.

---

### Post by snapdata on 2012-05-19
Still stuck. I can't figure this out.

---

### Post by roelforg on 2012-05-19
> **snapdata said:**
> Still stuck. I can't figure this out.

I'd like to help, but i do suspect some prog is crashing
So i'd like you to post the contents of /var/log/Xorg.0.log.old after a crash/logout

---

### Post by Quiane on 2012-08-02
i'm also having this issue...among others..could it be the visual drivers? (i think that's the culprit for my other issues..i'm using fglrx and it's been unstable from day one).

---

### Post by laserator on 2012-08-02
Have you tried going to the Grub menu

---

### Post by jim_deadlock on 2012-08-02
I also have a SSD and was having this same problem. I switched from autologin to normal login and it seems to have fixed it.

I think maybe startup programs were loading too fast because of the SSD or something like that.

---

